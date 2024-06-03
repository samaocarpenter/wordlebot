# wordlebot

A fun little bot to solve Wordle!

This is a program that I created in 2023 to solve the New York Times Wordle game optimally. 
There are a few iterations of my model present in this repository; the most recent is the top function in the wordle_solver.ipynb notebook.
Now immortalized in GitHub for me to show off!

This solver uses a combination of information theory and some heuristics to solve Wordle extremely fast! 
It is designed to never fail, and in my testing it never needs to go beyond the fifth guess and rarely beyond the fourth. 
The current implementation calculates the entropy for each possible guess based on the pool of remaining solutions, and guesses the optimal word. 
This means that in most cases, it chooses to go "fishing" by guessing words that are not possible solutions until it's certain.

This bot performs slightly worse than the state-of-the art!
This is pretty much by design, for these reason:

1. The daily Wordle word isn't chosen by a truly random procecss, and some words are more likely than others. This model prefers to think of Wordle as a theoretical rather than practical task, and assumes that every possible word is equally probable. However, some other models have increased performance by using a heuristic to add weight to common words.
2. This model prefers to minimize risk, and will typically "fish" until it's certain. Some other models prefer to take chances by guessing words in the solution list, especially if it's justified by weighting words as in the previous bullet point. Although this can improve performance when combined with weighting words, this model prefers to rely on certainty rather than luck.
3. This model does not recurse! This model finds an optimal word, but doesn't consider an optimal chain of words or factor its next guess in. This is because the sample space of Wordle is extremely small, and implementing recursion essentially means just computing the full decision tree, which feels like cheating.

Those are all compelling ways to improve the performance, and perhaps someday I shall implement them! For now, though, enjoy this Wordle solver; it is extremely close to optimal, works well on variants, and will almost always beat a human!
