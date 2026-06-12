---
title: "Getting input from GNU Chess to my program?"
date: 2011-10-05
forum: Programming Talk
---

### Post by cyb3r_sn4k3 on 2011-10-05
Hi everybody I am making a robotic arm to play chess with a human opponent. So all the moves will be detected and printed on a C program(through serial). But the problem is how do I input these moves into GNU chess(glchess)?(or any other chess game/program).?

---

### Post by PaulM1985 on 2011-10-05
I guess you have a few options depending on how complex your program is going to be:

1 - Starting with the simplest, you could simply manually input the moves into the system that are completed by the opponent.

2 - Get your system to take pictures of the board, recognise the differences and use that as an input.

I'd go with manual input, get the arm working, then try to give your robot "sight".

Paul

---

### Post by cyb3r_sn4k3 on 2011-10-05
> **PaulM1985 said:**
> I guess you have a few options depending on how complex your program is going to be:

1 - Starting with the simplest, you could simply manually input the moves into the system that are completed by the opponent.

2 - Get your system to take pictures of the board, recognise the differences and use that as an input.

I'd go with manual input, get the arm working, then try to give your robot "sight".

Paul


But how do I input the moves to the game?


Also, just for the record I am using reed switches embedded under every block and a small magnet under the chess pieces to read the opponents moves.

---

### Post by cyb3r_sn4k3 on 2011-10-05
Bump.

---

### Post by hakermania on 2011-10-05
At least 24 hours for bumping!

I haven't understood very clearly what you want to do.
As far as I've understand you want to make an 'arm' that plays against the human a chess game like gnuchess.
So, gnuchess or others come with an option to play human vs machine.
If you want to make an arm I'd suggest you to make a complete game, it will not differ so much anyway.

---

### Post by haqking on 2011-10-05
> **cyb3r_sn4k3 said:**
> Bump.

Why dont you use a DGT board ?

---

### Post by NovaAesa on 2011-10-05
If I understand correctly, all you need is to be able to give "moves" to the chess engine (GNU chess) and get back "replies" from the engine?

To do this, I would start with reading the following:
[http://www.gnu.org/software/chess/manual/](http://www.gnu.org/software/chess/manual/)
[http://en.wikipedia.org/wiki/Chess_Engine_Communication_Protocol](http://en.wikipedia.org/wiki/Chess_Engine_Communication_Protocol)

---

### Post by cyb3r_sn4k3 on 2011-10-05
> **haqking said:**
> Why dont you use a DGT board ?


Oh cool didnt know of that thanks.

---

### Post by haqking on 2011-10-05
> **cyb3r_sn4k3 said:**
> Oh cool didnt know of that thanks.

They are great bit of kit, but expensive ;-)

---

