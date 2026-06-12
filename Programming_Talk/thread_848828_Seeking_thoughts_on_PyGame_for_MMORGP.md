---
title: "Seeking thoughts on PyGame for MMORGP"
date: 2008-07-03
forum: Programming Talk
---

### Post by MicahCarrick on 2008-07-03
I've been a programmer for over a decade, and I'm falling in love with Python. I've worked with SDL in C and C++ and only done Python with GTK+ desktop applications.

I'm not much of a gamer, but every year or so I love playing the original Zelda or The Mana World--a MMORPG which works great on Linux.

I have a young brother (13) who has been getting into programming in little bits. He's a big gamer--whether it's the latest 3d super game or my old Atari--he loves them all. He's been running Linux (I might have had something to do with that) for about 6 months and has been learning HTML, CSS, Java, and Flash (the Flex SDK is available for Linux now). He is determined to learn how to make a game, and I'm trying to steer him towards Python as I feel it offers the most bang for your buck as a newbie.

He goes on and on about how he's going to make an MMORPG if it takes him 15 years. He went so far as to say "I've got to learn how to do it before I get older and have to get a job". Smart kid.

I've considered making a very simple 2d MMORPG myself from time to time, however, I've never done any substantial game development (I can make sprites move around with keyboard input using SDL and C--that's about all I've done).

So, long story still long (see above), I'm looking for people's opinions about pyGame's ability to handle an MMORPG--I was thinking using Twisted for the networking side. If this is a project that is feasible in pyGame, I would like to embark on this with my brother as both a fun project, a way to "bond", as well as a way to force feed him some programming theory along the way. 

I'm not looking (unless things go well) for anything too over the top, but knowing him, we'll want to have smooth animations, potentially dozens of sprites in the screen all potentially animated, smooth movement (not the one arrow key move the character 1 "square" over), etc.

I've done quite a bit of reading and some experimenting with pyGame and although it seems possible, it seems the limits are well within sight. If I were embarking on this project alone, I would likely opt for C, however, I really want to see if I can both get him interested in Python and see if I can push Python to it's limits.

Thoughts? Do you guys think a game with the "complexity" of say, Zelda for SNES as a multiplayer online game? Basically, MMORPG without the first "M"?

---

### Post by CptPicard on 2008-07-03
I don't know about PyGame -- it's well possible that it's too primitive -- but Python itself should be capable of handling some Ultima Online-style MORPG with ease. It's certainly not lack of computing power you'll be running up against -- I hear EVE Online is written in Python!

Writing your own networking for the engine isn't awfully difficult either, after all the server just sits there reading from sockets, running the engine and posting events back to the clients.

To get ideas about how to go about architecturing the thing, you check out [www.worldforge.org](www.worldforge.org). Maybe it would even be more interesting to fork one of their projects or even contribute back to one of them, if you are so inclined. Starting everything from scratch is... an awful amount of work.

---

### Post by days_of_ruin on 2008-07-03
Pygame is pretty much a sdl python wrapper geared towards games.
So is your game going to be from a top down view?You would
probably want to make it like the original zelda and not have the 
screen scroll as I heard its to slow, but who knows processors are
always getting faster.

So go for it!:guitar:

---

### Post by days_of_ruin on 2008-07-03
I googled pygame mmorpg and apparently someone has made [one.]("http://www.pygame.org/project/435/")
If you need more number cruching power try
pyrex and or psyco(If you are using an intel chipset).

---

### Post by pmasiar on 2008-07-03
MMORPG is a lot of programming. Doing it as first system is hopeless.

You might be interested in our project GameBaker (see my sig) - simple wrapper for pygame to make games easier. Start what we have, and you will add just features your brother need for his game :-)

But even that might be hard for total beginner: Project Euler has many simple training tasks. See wiki in my sig for links.

---

