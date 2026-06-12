---
title: "PHP check if board is split"
date: 2009-05-10
forum: Programming Talk
---

### Post by geek_of_doom on 2009-05-10
I am developing a PHP game which consists of a 4x4 board, which I have stored as a 2-dimensional array called $board, which takes on a form somewhat like the following:

```
array(
  array(0, 0, 0,0)
  array(0,-1, 1,0)
  array(2, 0,-1,0)
  array(0, 0,-1,0)
)
```In the game, players are allowed to remove tiles. In the $board variable, -1 represents a tile that has been removed, and 0, 1, and 2 represent remaining tiles. I will not go into detail the difference between 0, 1, and 2.

When removing tiles, players are given the restriction that they cannot split the board into two or more parts (diagonally adjacent squares are considered separate.) The problem lies in checking whether a given position is valid in terms of this rule.

I have tried numerous functions and algorithms to tackle this problem, none of which worked at all. Does anyone have a solution, if there is one?

Please forgive me if I've posted in the wrong location.

---

### Post by Reiger on 2009-05-10
You mean isolation of one non -1 "section" from another? Or a simpeler rule: there cannot be X-"-1" symbols in a row where X is the height/width of a board?

If the board is square (it may be arbitrarily large, though) and the latter applies, you could use summation of fields to check for a result more reliably if we also may assume that *any* negative value corresponds to removal. The reason is that -given these modified rules- you can calculate the proper removal value for a given tile as follows:

Let l = the length of a row
Let i = the number of the current row, some index
Let j = the number of the current column, a 1-based index:
Then:
Removal value for tile(i,j) = - 1 * ((j + i) mod l)

You now have a configuration which avoids duplicate values in rows or columns or diagonals (of length l); better yet, checking for the case "l removals in a row" becomes as easy as comparing the sum of the tiles with -1 * l * (l + 1) / 2.

---

### Post by geek_of_doom on 2009-05-10
One nitpick. The board below, although an invalid position with in the game, does *not* have a row or column consisting only of -1's.

```

(0) ( 0) (-1) (0)
(0) ( 0) (-1) (0)
(0) (-1) ( 0) (0)
(0) (-1) ( 0) (0)

```

Your algorithm apparently does not work.

---

### Post by Reiger on 2009-05-10
If otherwise correct: use positive integer powers of l (with each exponent corresponding to a move-type).

```

array(t*l^1, t*l^3 /* etc. */)

```

Then the check becomes something like:
Let m = the integer associated with the operation to check
l^m * l * (l + 1) / 2

So you would then do a for-each m in M (the set of all possible moves per tile) compare; if none match then the new board is valid.

EDIT2: t is of course given as plugging in the tile() function on a given coordinate i,j. Just as with the -1 only case.
EDIT3: Scratch EDIT 1, the integer powers must be such that 1*l^M(n) > l*l^M(n-1), where M(n) is integer associated with the move to check; thus the maximum value you can obtain for a field in the previous move type is smaller than the smallest value obtained with the next move type.

---

### Post by geek_of_doom on 2009-05-10
I apologize if I am beginning to irritate you with my n00bishness, but I do not quite understand. :( "The integer associated with the operation to check" is completely Greek to me...

---

### Post by simeon87 on 2009-05-11
> **geek_of_doom said:**
> One nitpick. The board below, although an invalid position with in the game, does *not* have a row or column consisting only of -1's.

```

(0) ( 0) (-1) (0)
(0) ( 0) (-1) (0)
(0) (-1) ( 0) (0)
(0) (-1) ( 0) (0)

```

Your algorithm apparently does not work.

Let's see: a position is valid if it is connected to at least one other tile (otherwise it is sealed off from the rest). Therefore, at least one adjacent position should be non-negative. However, this is not a sufficient condition because the board may be split into multiple parts.

To check whether a given board is valid, you could use the flood fill algorithm ([http://en.wikipedia.org/wiki/Flood_fill](http://en.wikipedia.org/wiki/Flood_fill)): a board is valid when the algorithm can fill all the non-negative positions (i.e., the number of filled positions is equal to the number of non-negative positions).

---

### Post by Reiger on 2009-05-11
> **geek_of_doom said:**
> I apologize if I am beginning to irritate you with my n00bishness, but I do not quite understand. :( "The integer associated with the operation to check" is completely Greek to me...

Well each type of operation on a tile is represented by a certain "integer". You used -1, 0, 1, and 2 in your original game. However, with my powers of l solution to your problem you must make sure that these "integer values associated with the operation to check" are far apart enough not to yield noise when the tile(i,j) function returns l. (Which it will do once per column and once per row and once per diagonal.) A simple implementation of that constraint is to have these values be a multiple of 2: 0, 2, 4, 6, etc.

Just to repeat, the tile(i,j) function is: (i + j) mod l. [With i and j 1-based array indices]

---

