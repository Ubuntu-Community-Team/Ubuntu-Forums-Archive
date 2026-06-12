---
title: "solve sudoku iteratively"
date: 2009-11-09
forum: Programming Talk
---

### Post by pearlygate on 2009-11-09
Has anyone ever made a sudoku solver before? I made one by constructing a search tree and search using DFS using recursion. something like
```


//call solve(initialTable)

boolean solve( List<Integer>[][] table) {
  //if table is solved return true
  //else let solutions = all possible solutions for unfinished cells in the state ordered by cells with the least number of possible solutions
  //for each possible solutions set the cell = some number
  //if this solve some other cells, do them and update the table.
  // call solve(modifiedTable)
  // if solve(modifiedTable) return true, then return true
  // else undo the changes made to the table
//if for loop doesn't find solution return false
}

```

Of course there are other optimizations, etc but I am curious if there is a way to do this iteratively? I'm kinda stuck thinking about it.

Thanks

---

### Post by Tony Flury on 2009-11-09
There are loads of online and offline Sudoku solvers.

The whole point is that puzzles which are published are solvable by the application of logic only - with no guesses.

On your specific question - "how do you do it iteratively" - there is one easy to develop method - which is brute force - try ever option in order and check if it is valid.

I am fairly sure I have seen a real solve application, which does not do brute force, and does not use any recursive type solution, it uses logic purely to eliminate impossible options. If you think about how most human players solve the puzzles they tend not to work recursively - they don't keep lots of partially filled tables in their heads and backtrack if they get an impossible solution.

Found it - look at [http://www.sudokusolver.co.uk/](http://www.sudokusolver.co.uk/)

---

