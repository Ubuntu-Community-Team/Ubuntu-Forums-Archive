---
title: "Using an integer variable as an array subscript in Python"
date: 2010-11-21
forum: Programming Talk
---

### Post by Chameco on 2010-11-21
[SIZE=2]Hello. I have recently started programing a small game in python using pygame, which I eventually plan to grow into a not-so-small game. I am competent with pygame (read: I can hobble along), but have recently had a problem. I am trying to organize the properties of various tiles using a two-dimensional nested list. I have a problem with subscripting. I am trying to use a while loop nested within another while loop to check to see if there are any "columns" left[/SIZE] ([SIZE=2]the nested list), and if there are, executing the second loop to write values to all the objects in the column. I tried to use variables as list subscripts, but realized that it was just trying to use the second variable as a  subscript to the first. This whole paragraph is probably incomprehensible, so here is my code.
[/SIZE]```
def redrawScreenWithCharPosition(charPositionX, charPositionY):
    row = [[0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0]]
    moreRowsLeft = 0
    moreCollumnsLeft = 0
    while moreCollumnsLeft <= 9:
        while moreRowsLeft <= 9:
            if row[moreCollumnsLeft[moreRowsLeft]] != 1:
                row[moreCollumnsLeft[moreRowsLeft]] = 0
            pixelCoordinateCollumn = moreCollumnsLeft * 50
            pixelCoordinateRow = moreRowsLeft * 50
            screen.blit(tile, (pixelCoordinateCollumn, pixelCoordinateRow))
            pygame.display.flip()
            moreCollumnsLeft = moreCollumnsLeft + 1
        moreCollumnsLeft = moreCollumnsLeft + 1
        moreRowsLeft = 1
```

---

### Post by Arndt on 2010-11-21
> **Chameco said:**
> [SIZE=2]Hello. I have recently started programing a small game in python using pygame, which I eventually plan to grow into a not-so-small game. I am competent with pygame (read: I can hobble along), but have recently had a problem. I am trying to organize the properties of various tiles using a two-dimensional nested list. I have a problem with subscripting. I am trying to use a while loop nested within another while loop to check to see if there are any "columns" left[/SIZE] ([SIZE=2]the nested list), and if there are, executing the second loop to write values to all the objects in the column. I tried to use variables as list subscripts, but realized that it was just trying to use the second variable as a  subscript to the first. This whole paragraph is probably incomprehensible, so here is my code.
[/SIZE]```
def redrawScreenWithCharPosition(charPositionX, charPositionY):
    row = [[0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0], [0,0,0,0,0,0,0,0,0,0]]
    moreRowsLeft = 0
    moreCollumnsLeft = 0
    while moreCollumnsLeft <= 9:
        while moreRowsLeft <= 9:
            if row[moreCollumnsLeft[moreRowsLeft]] != 1:
                row[moreCollumnsLeft[moreRowsLeft]] = 0
            pixelCoordinateCollumn = moreCollumnsLeft * 50
            pixelCoordinateRow = moreRowsLeft * 50
            screen.blit(tile, (pixelCoordinateCollumn, pixelCoordinateRow))
            pygame.display.flip()
            moreCollumnsLeft = moreCollumnsLeft + 1
        moreCollumnsLeft = moreCollumnsLeft + 1
        moreRowsLeft = 1
```

So you mean that it's row[moreCollumnsLeft][moreRowsLeft] you want?

("Column" has one l, by the way.)

---

### Post by spjackson on 2010-11-21
I'm not totally sure what you are asking.

First, your array subscripts should look like this:
```
row[moreCollumnsLeft][moreRowsLeft]
```or the other way round, because I am unclear whether you mean column to be outer and row to be inner, or the other way round.

Your looping is a bit awry, and as I say, I'm not sure what you mean to be outer and inner but within
```
        while moreRowsLeft <= 9:
```you need to be incrementing moreRowsLeft and within
```

    while moreCollumnsLeft <= 9:


```[FONT=monospace]you need to increment [/FONT]moreCollumnsLeft. You seem to have these mixed up.

Consider a for loop if you have a known number of iterations.

---

### Post by StephenF on 2010-11-21
Thoughts:
```

rows = [[0]*10 for x in xrange(10)]
for pc_row, row_data in enumerate(rows):
    for pc_col, element in enumerate(row_data):
        screen.blit(tile, (pc_col * 50, pc_row * 50))
        pygame.display.flip()

```
I still don't get what you want with those zeros. Lots of data going up in smoke. Could reduce further but not sure what you really need.

---

### Post by unknownPoster on 2010-11-21
you may want to consider using numpy arrays.

---

