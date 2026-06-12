---
title: "Weekly Programming Challenge, 1 April 2007"
date: 2007-04-01
forum: Programming Talk
---

### Post by po0f on 2007-04-01
This installment of the (semi) Weekly Programming Challenge has the participant, you, solving the old problem of [the Knight's Tour](http://en.wikipedia.org/wiki/Knight's_tour):

[quote=Wikipedia]The Knight's Tour is a mathematical problem involving a knight on a chessboard. The knight is placed on the empty board and, moving according to the rules of chess, must visit each square exactly once.[/quote]

This challenge will assume a standard chess board size of 8x8.  As usual, any language allowed, but no libchess please!  ;)

points++ for solving the problem given a board of size **n**x**n**.

---

### Post by Jmccaffrey on 2007-04-02
This is my first crack at the problem, I made an algorithm that can solve the tour for a board size nxn using back-tracing.
```

#!/usr/bin/env python
def find_tour(size, start_x, start_y):
    moves = [[1, 2], [2, 1], [2, -1], [1, -2], [-1, -2], [-2, -1], [-2, 1], [-1, 2]]
    board = []
    trace = []
    n_move = 1

    for i in range(0, size):
        board.append([-1] * size)
        
    board[0][0] = 0
     
    cur_x = start_x
    cur_y = start_y

    while n_move < size * size:
        p = []
        
        for move in moves:
            move_x = cur_x + move[0]
            move_y = cur_y + move[1]

            if (move_x >= 0) and (move_y >= 0) and (move_x < size) and (move_y < size) and (board[move_x][move_y] == -1):
                p.append((move_x, move_y))

        while not len(p):          
            cur_x, cur_y, p = trace.pop()
            board[cur_x][cur_y] = -1
            n_move -= 1;

        cur_x, cur_y = p.pop()

        board[cur_x][cur_y] = n_move
        trace.append((cur_x, cur_y, p))
        n_move += 1

    return board

b = find_tour(8, 0, 0)
print b

```

This is pretty slow but it works so far.  I plan to create a GUI to better visualize the tour tomorrow.

Here is the output for 5x5:
```

jmccaffrey@windy:~/mywork/knights-tour$ time ./pytour.py
[[0, 3, 8, 17, 20], [9, 16, 19, 2, 7], [4, 1, 12, 21, 18], [15, 10, 23, 6, 13], [24, 5, 14, 11, 22]]

real    0m0.113s
user    0m0.112s
sys     0m0.000s

```

---

### Post by Gorlith on 2007-04-02
i once made one that solved an nxn board using backtracing for one of my classes here at NJIT. If i have time too later today maybe I'll see if my memory still lets me throw one together!

---

### Post by dwblas on 2007-04-03
> This installment of the (semi) Weekly Programming ChallengePoint of order, are there now two challenges per week?  Or should it be semi-monthly?

---

### Post by po0f on 2007-04-03
dwblas,

"semi", because they haven't exactly been happening on a weekly basis (if you haven't noticed).  I sometimes don't find time or even an idea for a challenge to post every week, which is why some weeks don't have one.  I will work on more regularly posting new challenges, at *least weekly*.

Certainly, more frequent challenges could be posted if the demand is high. :)

---

### Post by dwblas on 2007-04-03
I been down for the last month with the flu that's been going around, so didn't know if the timing had changed or not.  Thanks for the effort put forth coming up with the challenges.

---

