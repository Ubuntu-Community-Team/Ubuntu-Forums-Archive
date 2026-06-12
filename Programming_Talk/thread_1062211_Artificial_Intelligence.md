---
title: "Artificial Intelligence"
date: 2009-02-06
forum: Programming Talk
---

### Post by Mr.Macdonald on 2009-02-06
I recently have learned that I am not to good at it, because I can't figure out how to write a connect4 AI. Are there tutorials or college videos on AI.

Using Scheme would be preferred!

---

### Post by Tony Flury on 2009-02-06
Well calling an Auto Connect 4 bot an AI is pushing the definition a bit (maybe a lot)

From what i know of Connect 4 is a complete game - in other words it is always possible to win by playing the right moves - almost regardless of what the opponent does.

If I was going to write Connect 4, I would make the decisions based on weightings - look at every possible move - and weight it according to its benefits to me (or ineterference with the opponent). So it would be an entirely empirical decision - not what i would call intelligent.
The major benefit of this approach is that you can write the code to go defensive or offensive - entirely depending on the weightings.

You might also have a table of opening moves - if you can work out what is a good set of moves.

What you need to know is what is a winning strategy for Connect4. I can't help you there - i can never beat anyone at it.

What would be a good AI would be to make it learn - rather than apply a consistent strategy.

---

### Post by Mr.Macdonald on 2009-02-06
I should rephrase, I am bad at writing efficient perfect AI's. I wanted my connect 4 to be unbeatable. So I wrote a backtracking algorithm to find the quickest winning path. It works, just its to slow (very slow).

EDIT: there are means to force a win
EDIT: if I can make it read all the moves and find a path to win, then why learn if you know all? But learning would be more efficient, and this is just a learning step.

---

### Post by JakeFrederix on 2010-03-12
[URL="http://www.google.be/url?sa=t&source=web&ct=res&cd=1&ved=0CAYQFjAA&url=http%3A%2F%2Fwww.connectfour.net%2FFiles%2Fconnect4.pdf&rct=j&q=connect+four+white+wins&ei=8deaS7W-H8mO4gazrvFu&usg=AFQjCNG7vifJZqz2vW-SOvuLyhzmlWX3jA"]Connect 4, white wins

[/URL]Basically a thesis someone wrote on writing a bot to play connect 4.

---

### Post by diesch on 2010-03-12
A good book on AI ist [Artificial Intelligence: A Modern Approach](http://aima.cs.berkeley.edu/) by Stuart Russell and Peter Norvig

---

### Post by CptPicard on 2010-03-13
There is no learning needed or going on in these sorts of games which can be seen as a game tree search with a fairly simple evaluator. You can make your search faster by pruning it -- read up on alpha-beta and the minimax (or negamax) searches...

---

### Post by IllegalCharacter on 2010-03-15
I'll second the Russell and Norvig book. It's a good one!

---

