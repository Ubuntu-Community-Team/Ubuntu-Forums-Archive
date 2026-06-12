---
title: "The right thing to do"
date: 2008-10-23
forum: Programming Talk
---

### Post by jesuisbenjamin on 2008-10-23
Hello forum,

Recently i have been learning basics of, and played around with, Python.
Though it is not innocently i have begun learning: i am trying to put together into a multiplayer computer game a game i have already made on board.
For now i would like to make the program so that it works with a text interface, but the idea is to add graphics (3D), which i would leave to my bro who's professional in the field.
But for now i need to find the right code and begin with the good end. The thing i must admit: i have no clue how multiplayer games are working and whether it is really essential to know this to make the game or whether this can simply be added to as a plugin later on.
Should there be a master/slave version of the game? Or do i simply do a local version which exchange data with a central database? 
What sort of code would i be using? Can i achieve this with Python? Or do i need to use flash or java? 

If you said Python you would make me happy, then i wouldn't have to learn basics again... ;)

Oh important note: i would like to make this game open-source for people using Linux (if that makes any difference...)
Cheers!

---

### Post by jimi_hendrix on 2008-10-23
a 3d MMO is very hard to make (it takes teams of people years)...

---

### Post by jesuisbenjamin on 2008-10-23
thanks, i am not so worried about the 3D to be honest, as i said my bro is a pro in the field, there programs out there you can do 3D games even if you miss 1/4 of your brain. (i.e. Quest3D) I simply need to find the right material to work with to create the actual content of the game (as opposite to graphics) and make sure i start on the right foot as far as networking is concerned.

As to the amount of years it will take: well i am still planning to live some more... but thanks for the warning! ;)

---

### Post by Ferrat on 2008-10-23
As stated a MMO takes years being so complex, however if I was you I would try my hand at a RPG then perhaps later add a Online feature which in theory could be expanded to a Online game. 

First of switching a game from pure text to 3d is a Major step, to help you brother you should really check with him what languages he is most proficient in and try to adapt to him, also don't make it pure text better if you try making it either in a existing 3D engine or use SDL since most of the basics of the game will depend on the engine itself and it would be easier if you started with that in mind. 

Also you have to work out how the game is suppost to look/act before you start making it and adapt the style after that. 

If you really want to learn to make a game, try making a Tetris clone or a chess game to start with in SDL and 2D graphics, there are many good tutorials out there for that and that will give you basic game development that is used more or less no matter what game you create after that, graphics, controls, sound, you could try simple networking and also simple A.I. learning this would impress your brother since you can actually help him and not just make a few lists and simple background code and it would probably look more fun and attractive to you r brother and you would be at a stage where you could learn from what he is doing :)

---

### Post by snova on 2008-10-23
The entirety of the game's logic should reside on the server, so that clients can't cheat by modifying the code. (This is a problem with a lot of multiplayer games- modified clients displaying too much information, or helping the player.)

Python is fine. Find a nice networking library (Twisted comes to mind, there are plenty others) and familiarize yourself with it, then start on a basic protocol. Keep it flexible.

To start with, try writing a game where you can move a little pixmap around in a fixed size level composed of a grid of squares. When player 1 moves, the client sends the command to the server (which makes sure you didn't go through the sides), which echos it to player 2 (but only if 2 can see 1!), which update the display...

---

### Post by jimi_hendrix on 2008-10-23
> **Ferrat said:**
> If you really want to learn to make a game, try making a Tetris clone or a chess game to start with in SDL and 2D graphics, there are many good tutorials out there for that and that will give you basic game development that is used more or less no matter what game you create after that, graphics, controls, sound, you could try simple networking and also simple A.I. learning this would impress your brother since you can actually help him and not just make a few lists and simple background code and it would probably look more fun and attractive to you r brother and you would be at a stage where you could learn from what he is doing :)

<OT>were are these tutorials...when i google how to make a 2d game in *language* i get broken code </OT>

but ya you should probably start small...i believe i read somewhere the order advised is something like tetris then pong then pacman then mario bros.

then when you get to the game like ferret said you will need to talk with your bro and then i advise you get some basic 3d object and just put it on the screen and then make it move and build from there

---

### Post by jesuisbenjamin on 2008-10-23
> **snova said:**
> Find a nice networking library (Twisted comes to mind, there are plenty others)

Could you please explain what a networking library is?

---

### Post by jesuisbenjamin on 2008-10-23
> **jimi_hendrix said:**
> something like tetris then pong then pacman then mario bros.

All i am trying to do is a silly diplomatic board game. What strikes me is that the examples above are action games. My à priori is that those are two categories of game which would not have the same requirements.

The example of Snova sounds more like what i am looking at. If it was not for the graphics or networking, i would do it on python without much difficulty since i only need dictionaries and a bit of if and then and there you go.
The 3D i am talking about is not a 3D action game or whatever. I simply would like the board (map) to show in 3D.

Is it really necessary to clone Mario Bros (which i have never liked playing?)

:-k

---

### Post by snova on 2008-10-23
> **jesuisbenjamin said:**
> Could you please explain what a networking library is?

Um... a library that does networking? You're going to need networking code to communicate betwen the clients and the server. Sockets work differently on every platform, so you'll be glad for an abstraction. Usually a simpler and easier abstraction.

> **jesuisbenjamin said:**
> Is it really necessary to clone Mario Bros (which i have never liked playing?)

Of course not. It's merely a suggested list of games to write in order of difficulty, rather than jumping in and writing something impossibly complicated (like an MMORPG or a FPS).

3D graphics shouldn't be too difficult to add to what you're trying to write. And you can absolutely use Python to do graphics and networking. Twisted is *written* in Python, for one. And it encompasses everything from HTTP to IRC to... everything.

SuperTux is fun. :)

---

### Post by jimi_hendrix on 2008-10-23
> **jesuisbenjamin said:**
> All i am trying to do is a silly diplomatic board game. What strikes me is that the examples above are action games. My à priori is that those are two categories of game which would not have the same requirements.

The example of Snova sounds more like what i am looking at. If it was not for the graphics or networking, i would do it on python without much difficulty since i only need dictionaries and a bit of if and then and there you go.
The 3D i am talking about is not a 3D action game or whatever. I simply would like the board (map) to show in 3D.

Is it really necessary to clone Mario Bros (which i have never liked playing?)

:-k

you will need snova's advice too but you should probably read [this]("http://www.gamedev.net/reference/design/features/makegames/page2.asp") and the next page at least

the games i mention each have a learning point

---

### Post by pmasiar on 2008-10-23
> **jesuisbenjamin said:**
> All i am trying to do is a silly diplomatic board game.

In multiuser game, you have players and "world". Network library anables communication between client programs (players) and "world" over the 'net.

Consider making "world" a database, and clients can every minute or so check if there is a new move. This will simplify your client/server communication. 

For extra credit go for web application, like Django ;-) It's about time someone started writing multiuser games for Django, everything else is being done.

---

