---
title: "algorithim"
date: 2011-03-26
forum: Programming Talk
---

### Post by dazman19 on 2011-03-26
Hi, I need to make an algorithim to solve a futoshiki puzzle in java.

I have an idea as to how I want to approach the problem. I want to use the process of elimination to figure out the cells. 

So i would start off reading in the puzzle template into a puzzle object from a file, and setting the possibilities for each cell object, and then as i scanned the puzzle i would remove numbers until i could solve a cell, if solved i would start the scan again on the uncompleted cells and check the constraints. before marking the cell as solved. Then recursively complete the process until the entire puzzle is solved. 

The hardest part is to determine what cell to process next is. I could scan the puzzle. row by row, but it would be more efficent to have a way of figuring out what cell I solve next.

Also i dont know how good this approach will be, if i can solve 4x4 and 5x5 puzzles i will be pretty amped.

---

### Post by schauerlich on 2011-03-26
From 3 minutes of googling, it look like futoshiki is similar to a sudoku puzzle, but there's no 3x3 mini grids and there's the additional inequality restraints. Perhaps you could try modifying one of the approximately 1,000,000 sudoku solvers online? Many of them use a backtracking strategy. Basically, every time you make a move you remember where you are, so that if the puzzle ends up unsolvable down the line you can rewind back to a "good" state. It's easy to do this with recursion. [http://en.wikipedia.org/wiki/Backtracking](http://en.wikipedia.org/wiki/Backtracking)

---

