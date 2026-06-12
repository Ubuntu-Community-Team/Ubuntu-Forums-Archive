---
title: "Reversi / Othello Small Java FOSS Project."
date: 2009-02-16
forum: Programming Talk
---

### Post by mike_g on 2009-02-16
I started making an Othello game in Java using Swing. At the moment I have it in a state so that 2 players can take it in turns to play against each other. I plan on adding AI, basically minimax with alpha beta pruning, but as I suck at the game I'm probably not going to be all that good at coming up with an evaluation function for it. 

Its an OS project so anyone that wants to help make it better is welcome. Apart from the evaluation, it would be nice to have network play. Either p2p or perhaps through a php server with a db to log games. Anyway, if anyone wants to play around with the source it can be found [here](http://grundez.net/downloads/reversi.zip) along with the Jar. 

Suggestions on how to come up with an evaluation function are also welcome. Cheers.

[IMG]http://grundez.net/images/reversi.png[/IMG]

---

### Post by jimi_hendrix on 2009-02-16
i am interested...i have nothing better to do and know java :) i do have a lot of school work though so when i can work it is not know

---

### Post by Reiger on 2009-02-16
The key is to 'obtain' the corners. These cannot change colour, and act as the end points of the largest 'lines' you can make (not to mention the effect of the (implicit) lines in quadrature with the ones you make).

---

### Post by bruce89 on 2009-02-16
Contributing to a project is much easier if you have some kind of source code repository.

---

### Post by mike_g on 2009-02-17
> i am interested...i have nothing better to do and know java  i do have a lot of school work though so when i can work it is not know
Same here, I got work and uni atm. While I'm studying AI, the kind of stuff I have to do so far is all theory and no coding. Anyways, if you like feel free to add to it, and give us a shout if theres anything you want to know about it. Its all pretty simple so far maybe ~300 lines of code.

> The key is to 'obtain' the corners. These cannot change colour, and act as the end points of the largest 'lines' you can make (not to mention the effect of the (implicit) lines in quadrature with the ones you make).
Yeah, adding weight to the corners is the easy part. Parity and edge play seem more difficult tho. It would be nice to also have a little variation in play style as well. For example some games the bot will stick more to the center, and others it will try and seal off as much of the sides as possible.

> Contributing to a project is much easier if you have some kind of source code repository.
Yep, hadent got that far yet. Maybe I'll set a project up on launchpad or something tomorrow.

---

### Post by u4687416 on 2010-04-16
Hi, I have read your thread. Seems interesting? Can i too contribute to it? If yes whats the project status like?

---

### Post by matmatmat on 2010-04-17
Your link seems to be broken!

---

### Post by hyperAura on 2010-04-17
well for evaluation function u could have the simplest which is just a subtraction of the number of black discs minus the number of the white discs..

as a 2nd evaluation function u could have the position value evaluation where corners get the maximum and corner surrounding boxes get minimum as they risk the corners if captured.

as a 3rd one u could have the number of available positions as there are players looking forward to maximize their number of moves to force the opponent to pass its turn thus playing twice in a row..

---

