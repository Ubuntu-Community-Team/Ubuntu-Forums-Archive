---
title: "Solving sudoku with python"
date: 2010-09-05
forum: Programming Talk
---

### Post by ApEkV2 on 2010-09-05
I have been trying to solve the standard sudoku puzzle with this Python script.
However, it is unable to solve any puzzle. It is based on a recursive algorithm and is not bruteforce.
I know it gets passed inserting two legal numbers into the Grid, but then after the second level of recursion, it returns False to main.

Any help would be appreciated, I don't know where the problem would be.

The isLegal function checks the row, column, and 3x3 box for a duplicate of the trialValue.
The getEmptyCell function searches the grid for the next NULL cell.
The isFull function checks the grid to see if it is finished.

Edit: the section in red is one of the problems. I was just subtracting until I found a familiar number.
    Now, I've created a dictionary to make sure it is the right 3x3 square.
    However, it still fails to complete.

```

None

```

---

### Post by ApEkV2 on 2010-09-05
Code revision and bump. Added a dictionary to check whether I'm checking the right 3x3 box.
Also, I'm going to bump this thread when it goes off the front page.
I haven't gotten any answers for a number of previous threads.

Changes are in blue.

```

None

```

---

### Post by ApEkV2 on 2010-09-06
Thanks for the help, it seems no-one was able to notice the simple problem.
if cell_number = 18 then reversed(range(cell_number)) starts at 17 which I didn't want.
That was simple enough to fix, and now the program works. Very fast that is.

I'm loving Python.

---

