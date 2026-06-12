---
title: "Tic Tac Toe AI"
date: 2008-07-31
forum: Programming Talk
---

### Post by lordhaworth on 2008-07-31
Hey all
I know everyone writes naughts and crosses games and theyre easy etc etc... 
Im wanting to implement a computer player, and this is proving more difficult. Its easy enough to play a random move but what i plan on doing is making the program reckognise board layouts and play the best move it knows (and randomly otherwise). At the end of the game if it loses it will subtract 1 from each move it made in its "Memory File" and if it wins it will add 1. If it has not encountered a board layout before it will also add this and the move it made, etc, to the file. 

Now the trouble im having is what the best way to store the information throughout the game is. I need to save the board layout (1,2,3,4,X,0,7,8,X), the move coordinate (1 to 9) for each move and then at the end of the game modify some value which records how successful the move has been in the past. At the end of the whole thing all this needs to be saved in a file. 
I can store bits in arrays but how i will eventually store only 'new' layouts in the file and append the success value of old moves i am a bit stuck with!

Any help or references much appreciated

Tom

---

### Post by hod139 on 2008-07-31
Tic-Tac-Toe is a solved game (meaning you can always play to a draw) and is a very common AI programming assignment.  The wikipedia page has a decent description     
  [http://en.wikipedia.org/wiki/Tic-tac-toe](http://en.wikipedia.org/wiki/Tic-tac-toe)
You do not have to store the entire game in the game tree though, the other nice thing about tic-tac-toe is that it is symmetric.  Even if you do store the entire board, the wikipedia article has the correct strategy to use.

---

### Post by lordhaworth on 2008-07-31
Cool cheers for pointing me in a new direction, I think itll be useful to get a reasonable computer player working first, but eventually i would like to create an AI that I have to "Teach" to play well from what its seen before

Thanks again

Tom

---

### Post by nanotube on 2008-08-01
> **hod139 said:**
> Tic-Tac-Toe is a solved game (meaning you can always play to a draw) and is a very common AI programming assignment.  The wikipedia page has a decent description     
  [http://en.wikipedia.org/wiki/Tic-tac-toe](http://en.wikipedia.org/wiki/Tic-tac-toe)
You do not have to store the entire game in the game tree though, the other nice thing about tic-tac-toe is that it is symmetric.  Even if you do store the entire board, the wikipedia article has the correct strategy to use.

that's true, but i think the idea of using it to implement a 'learning' AI is also a good learning experience (pun intended :) ).

as an upper bound, there are a total of 3^9 possible board states (9 cells, each cell can be blank, X, or 0), 19683, and in each of those states, you can make <= 9 moves, so a total of 177147 possible moves to "weight". (in reality, taking out impossible board states and impossible moves, the total number is much less). so, after some training, you would eventually be able to pick the highest-rated move for each board state, without having to actively "solve" the game manually.

---

### Post by MaxIBoy on 2008-08-01
Tic Tac Toe AI is easy. Here are the rules, in order of priority:
[LIST]
[*]If there is a row/column/diagonal in which two spaces have been taken (doesn't matter which person,) complete it.
[*]If possible, snag the center cell.
[*]Pick a random cell.
[/LIST]

---

### Post by nanotube on 2008-08-01
> **MaxIBoy said:**
> Tic Tac Toe AI is easy. Here are the rules, in order of priority:
[LIST]
[*]If there is a row/column/diagonal in which two spaces have been taken (doesn't matter which person,) complete it.
[*]If possible, snag the center cell.
[*]Pick a random cell.
[/LIST]

you're missing a few (see the wp article linked above). in particular, avoiding forks is pretty important. :)

---

### Post by lordhaworth on 2008-08-01
nanotube is right, I could make a computer player without masses of difficulty in various ways. But it would be quite cool to make the computer start off with as little as possible and then improve as it "learns" - this is what i think ill work on but as i said originally my problem is storing the moves and board layouts it makes and then adding / appending the progress to a file. The point of interest was a learning program more then just an opponent

Quite interesting stuff though, this is my first shot at any kind of AI

---

### Post by Nemooo on 2008-08-01
Out of curiosity: What language are you doing this with?

---

### Post by lordhaworth on 2008-08-01
Im trying to get proficient at using Fortran90 so thats what im doing it in.

---

### Post by slavik on 2008-08-01
min-max is a good algorithm for this.

recognising layouts though is something that would have to be done for Go

---

### Post by nanotube on 2008-08-01
> **lordhaworth said:**
> nanotube is right, I could make a computer player without masses of difficulty in various ways. But it would be quite cool to make the computer start off with as little as possible and then improve as it "learns" - this is what i think ill work on but as i said originally my problem is storing the moves and board layouts it makes and then adding / appending the progress to a file. The point of interest was a learning program more then just an opponent

Quite interesting stuff though, this is my first shot at any kind of AI

instead of using a file (which is good for sequential appends), i suggest you use a database, like sqlite maybe, which is good for updating data rows (which is what you'd have to do to update the scores for the moves). i'm sure there's an interface to sqlite in fortran, but any database backend will do, really. a db lends itself very nicely to this kind of thing.

---

