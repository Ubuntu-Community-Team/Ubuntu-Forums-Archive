---
title: "Chess engine in php"
date: 2010-02-21
forum: Programming Talk
---

### Post by aloprot on 2010-02-21
After my previous post I came up with an idea, to work day by day to create something instead of just reading and reading and endless reading. So I thought I could start step by step and make a php chess engine script which later all can use. I just want some directions on how to start. How could I connect two players and make a game so that they could battle each other. And more important how could I design an AI in php for playing chess?

Thanks, Pat.

---

### Post by Some Penguin on 2010-02-21
I am somewhat perplexed why you would attempt to use a language intended for server-side production of dynamic web pages, for chess, and would recommend against it.

For chess, a sane architecture should probably recognize that how the game is actually presented and how moves are accepted is completely separate from whether those moves are legal and whether or not the game is over (and if so, in what way), and whether a player is a human being or a program.


For example, you might start with the following:

- Writing a data structure that stores a move list.  A move list encapsulates the entire state of a game of chess -- from it, you can determine everything.
- Writing code to turn a text file into a move list structure.
- Writing code to turn that move list structure into text.
- Writing code that can accept a move list structure, and determine:
   1.  Whether it is, in fact, a legal set of moves.
   2.  What the board looks like if it is in fact legal.
   3.  Whether the game is over, and if so, who won or whether it is a draw.

---

### Post by aloprot on 2010-02-22
Well I have seen sites like instantchess, who work in php so I thought this is the best solution right now for my problem since I don't know other languages. I'm not good in php but at least I know just a little.

Thanks for your advice!

---

### Post by CptPicard on 2010-02-22
The interesting problem in chess is the game tree search algorithm used -- for a simple example look at the [alpha-beta pruned minimax]("http://en.wikipedia.org/wiki/Alpha-beta_pruning"). The other, secondary problem is the writing of the evaluation function. In general, in chess, the search dominates the evaluator, so it's better to be able to search deeper in the game tree than to write a very good (and expensive to compute) evaluator.

Those chess sites you mention use php just to generate web pages... if they allow you to play chess against the server, they certainly run some chess engine at the back to drive the game.

For speed reasons, chess engines are written in C... but that really is far too complex a project for you currently. I would suggest that you learn Python and take a look at nvteighen's TicTacToe-project instead; it's much simpler than chess and much more beginner-friendly.

---

### Post by aloprot on 2010-02-22
Yes I think you are right, maybe it's a bit to much for me right now. 

Really I don't have words to thank Ubuntuforums. Such great people here. Thanks for answering my questions.


Signed, a humble beginner.:P

---

### Post by CptPicard on 2010-02-22
> **aloprot said:**
> 
Signed, a humble beginner.:P

Code, don't grovel. That is not required ;)

---

### Post by Some Penguin on 2010-02-22
Tic-tac-toe does have the property that the rules are much simpler to enforce, in so far as detecting a game end is pretty simple.  Chess is uglier that way; even if we ignore the AI component, one still has to notice checks, determine whether there is *any* move that gets one out of check, handle castling and en passant...

At least it has no randomness nor hidden information, which makes subtle cheating impossible so long as you can compare the move history to ensure no revisionism.

As for an AI, tic-tac-toe is small enough that you could work out the entire state space with paper and pencil, if you like.  It's a solved problem (an optimal AI should always achieve a draw against a competent opponent, and possibly a win against somebody who isn't...)

---

Another _very_ simple game is Hexapawn.  Same 3x3 board.  Each player has three pawns lined up at his end of the board.  

Each player must make exactly one legal move on his turn.   Pawns act just like chess pawns, except that neither double-move nor en passant is possible -- just single steps forward into unoccupied spaces, or single-step forward diagonal captures.  Victory comes when any of your pawns reaches your opponent's end rank, or when it's your opponent's turn and he cannot move.

The state space is even smaller, IIRC (certainly the maximum branching factor is smaller), and the second player always wins if playing optimally.  

Martin Gardner once built a mechanical Hexapawn player which he trained using the following method:  there were containers representing game states, and jelly beans which represented legal moves (transitions from states to states).  Whenever he beat the machine, he ate the jelly bean representing the machine's last move.  If it was the machine's turn and it had no moves left (any legal moves had already been proven to be losers), that also counted as a loss for the machine so he again ate the jelly bean.  This works for tiny spaces.  It doesn't work for Chess or Go, whose state spaces are far too large to be pruned that way -- there, heuristics and pattern recognition are far more valuable.

---

