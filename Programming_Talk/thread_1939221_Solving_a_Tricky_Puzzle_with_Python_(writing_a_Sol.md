---
title: "Solving a Tricky Puzzle with Python (writing a Solver)"
date: 2012-03-11
forum: Programming Talk
---

### Post by lionaneesh on 2012-03-11
After trying for 2-3 hours I was able to find a solution to the following [puzzle]("http://www.enterthetank.com/bombtrap.html") :-

[B]Problem Description :-
[/B]

Given a 8 x 8 , board with 64 boxes fill 8 of these boxes in such a way that no two filled boxes fall on the same straight
line - horizontally, vertically or diagonally!

**Checker** ([source]("http://www.go4expert.com/forums/showthread.php?t=27993")) :-

```
#!/bin/env/python
# Checker for a 8x8 bomb trap

# Correct Solution
game = [
            [0, 0, 0, 0, 0, 0, 1, 0],
            [0, 0, 0, 0, 1, 0, 0, 0],
            [0, 0, 1, 0, 0, 0, 0, 0],
            [1, 0, 0, 0, 0, 0, 0, 0],
            [0, 0, 0, 0, 0, 1, 0, 0],
            [0, 0, 0, 0, 0, 0, 0, 1],
            [0, 1, 0, 0, 0, 0, 0, 0],
            [0, 0, 0, 1, 0, 0, 0, 0]
       ]

def check_ones(array) :
    ones = 0
    for h in array:
        if isinstance(h, list) :
            ones = ones + check_ones(h)
        elif h == 1:
            ones = ones + 1
    return ones

def diagonal_check(game):
    errors = ''
    for i in range(0, 7):
        for j in range(0, 7):
                if game[i][j] != 1:
                    continue

                # diagonal 1
                diag1 = []
                h, k = i, j
                # addition loop
                while h <= 7 and h >= 0 and k <= 7 and k >= 0:
                    diag1.append(game[h][k])
                    h = h + 1
                    k = k + 1
                # subtration loop
                h, k = i-1, j-1
                while h <= 7 and h >= 0 and k <= 7 and k >= 0:
                    diag1.append(game[h][k])
                    h = h - 1
                    k = k - 1

                # diagonal 2
                diag2 = []
                # add k loop
                h, k = i, j
                while h <= 7 and h >= 0 and k <= 7 and k >= 0:
                    diag2.append(game[h][k])
                    h = h - 1
                    k = k + 1

                # add h loop
                h, k = i + 1, j - 1
                while h <= 7 and h >= 0 and k <= 7 and k >= 0:
                    diag2.append(game[h][k])
                    h = h + 1
                    k = k - 1

                # at this point we have 2 diagonal arrays and we can simply check
                # for multiple 1's, if there are multiple 1's in any diag list
                # it means we have 2 points in a diagonal i.e check failed

                if check_ones(diag1) > 1:
                    errors += "Diagonal 1 check @ point [%d, %d] evaluated to FALSE\n" % (i+1, j+1)
                if check_ones(diag2) > 1:
                    errors += "Diagonal 2 check @ point [%d, %d] evaluated to FALSE\n" % (i+1, j+1)
    if errors != '':
        print errors
        return False
    return True

check1 = True # Let's be +ve ;)
errors = ''
# let the game begin

if check_ones(game) != 8:
    print "Please fill up exactly 8 places."
    exit()

for i in range(0, 7):
    horizontal = []
    vertical   = []
    for j in range(0, 7):
        horizontal.append(game[i][j])
        vertical.append(game[j][i])
    if check_ones(horizontal) > 1:
        errors += "Multiple mines in Horizontal, @ Row [%d]\n" % (i + 1)
    if check_ones(vertical) > 1:
        errors += "Multiple mines in Vertical,  @ Column [%d]\n" % (i + 1)

if errors != '':
    print errors
    check1 = False

# Lets do some diagonal checking now

check2 = diagonal_check(game)
if check1 and check2 :
    print "Correct :)"
```

Now my questing is how can i go about making a solver for this puzzle, To be frank i solved this using absolute hit and trial. SO writing a brute-forcer for this puzzle would be quite foolish, please suggest some ideas to go about writing a solver.

---

### Post by simeon87 on 2012-03-11
This is the eight queens puzzle, see more information [here](https://en.wikipedia.org/wiki/Eight_queens_puzzle), including how to write a solver.

---

