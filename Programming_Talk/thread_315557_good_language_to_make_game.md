---
title: "good language to make game"
date: 2006-12-09
forum: Programming Talk
---

### Post by Fittersman on 2006-12-09
i am going to be going into cs30 in high school and i want to create a game for my project. what is a relatively easy to learn language that can create a game and run on ubuntu. 

also if you could send me a link that has how to learn to use it and a list of the commands you can use that would be great.

---

### Post by gummibaerchen on 2006-12-09
> **Fittersman said:**
> i am going to be going into cs30 in high school and i want to create a game for my project. what is a relatively easy to learn language that can create a game and run on ubuntu. 

also if you could send me a link that has how to learn to use it and a list of the commands you can use that would be great.

As everytime: Python (with PyGame).

If you want spend a lot of time on that you can create Games in nearly every language that has OpenGL(?) bindings.

---

### Post by Fittersman on 2006-12-09
i downloaded pygame but im missing some things and i dont know how to get them, do you know how i can get them?

i ran config.py and i got this:

Using UNIX configuration...


Hunting dependencies...
sh: smpeg-config: command not found
WARNING: "smpeg-config" failed!
SDL     : found 1.2.10
FONT    : not found
IMAGE   : not found
MIXER   : not found
SMPEG   : not found
NUMERIC : found 24.2


Warning, some of the pygame dependencies were not found. Pygame can still
compile and install, but games that depend on those missing dependencies
will not run. Would you like to continue the configuration? [Y/n]:

---

### Post by Fittersman on 2006-12-09
and also if you could play the game on a psp im sure that would get me some bonus marks :P

---

### Post by gummibaerchen on 2006-12-09
> **Fittersman said:**
> and also if you could play the game on a psp im sure that would get me some bonus marks :P
don't think that would work with an unhacked psp.

---

### Post by Fittersman on 2006-12-09
ooo i seeee but what if mine is already hacked?;) 

if you know what i mean

---

### Post by pmasiar on 2006-12-09
I always promote python and pygame is pythonic way to write games. On ubuntu, pygame is way to go.

But hands down the easiest way to program games is [Game Maker]("http://en.wikipedia.org/wiki/Game_Maker") - drag-and-drop GUI to make games. 10 years old kid can make games, I seen it. I made my first simple game within one hour - and it was fun to play and hard to win! But: Windows only, with free and paid versions. 

If only someone reimplemented it in python... :-(

---

### Post by slavik on 2006-12-09
C++ and SDL using OpenGL to draw stuff. :)

Check out NeHe tutorials on gamedev.net

---

### Post by pmasiar on 2006-12-09
C++ for a HS student, with (presumably) little or no programming experience, and with very limited timeframe to complete the project? You must be kidding.

Hey, don't trust advice of strangers, make your own mind, compare for yourself: [python ]("http://en.wikipedia.org/wiki/Python_%28programming_language%29") and [C++]("http://en.wikipedia.org/wiki/C%2B%2B"). 

Or even better: for python, start command shell and try different statements. With dynamic typing and memory management - No C++ type police to blow off your "suspicious" statements. Try [instant hacking in python]("http://hetland.org/python/instant-hacking.php"). Python is already installed in your ubuntu box, open terminal, type 'python', press enter and start hacking! DO IT NOW! :-)

---

### Post by Wybiral on 2006-12-09
Forget C++... Use ASM!!!

JK, I vote python too... I prefer C++, but if you want it done fast, python is the way to go. Easy debugging, tons of libraries, easily readable code (which might help if you need to show it to a teacher!) and all the help you need (for here and from galaxies of tutorials on the internet).

So what kind of game are you looking to make?

---

### Post by Fittersman on 2006-12-10
i really havent decided what type of game in going to make yet, i was going to wait until i have decided what programming language i was going to use then i would decide the game (based on how hard it would be to make)

and does anyone know how i can fix that problem with pygame im having? i dont know what packages im lacking for the install to be complete and have it operating fully.

---

### Post by dwblas on 2006-12-12
This link to the pygame README [http://www.pygame.org/readme.htm](http://www.pygame.org/readme.htm) says that the missing items are all part of SDL.  I would suggest (re-)installing the appropriate packages, libsdl-sound, libsdl-ttf, etc.  Just search for "SDL" in synaptic.

---

### Post by po0f on 2006-12-12
Or, just search for "[pygame](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=pygame&searchon=names&subword=1&version=edgy&release=all)":
```
[FONT="Courier New"]$ sudo aptitude install python-pygame[/FONT]
```

---

### Post by neemz on 2006-12-12
I think this is one of those "if you have to ask you can't afford it" kind of questions.

Making a game should not be anywhere near the agenda when learning to program, even basic text games or games like pong will only be within your skill level after a few months of learning.

As an example I am writing a multiplayer verison of the KDE Konquest game, which is a game based upon a 2d grid. I've been working on it 2 months so far and im half way there, its been tough, and I started to program 4 years ago.

However I wrote an internet version of Pong after 6 months with a classmate if that helps bring you some confidence in your idea.

---

### Post by slavik on 2006-12-12
i suggest your first game to be a maze game, sounds cheap but you learn input, basic opengl, and collision detection (and reaction).

then you can turn it into tetris or side scroller

---

### Post by Fittersman on 2006-12-12
actually i wasnt really thinking of creating a massive sweet game, i did some programming and i realize that im guan have to create a low quality game, so i was thinkin something like that old black and white aliens game where they keep getting faster for everyone you destroy and your a little spaceship...that one

---

### Post by pmasiar on 2006-12-12
> **neemz said:**
> I think this is one of those "if you have to ask you can't afford it" kind of questions.

Making a game should not be anywhere near the agenda when learning to program, even basic text games or games like pong will only be within your skill level after a few months of learning.

Exactly. Thats why suggested game maker: drag&drop GUI tool to program games (and games only). 10 years old, with little help, created his own platform game. And we had discussion about events, creating and destruction of objects, etc.

---

### Post by neemz on 2006-12-12
> **Fittersman said:**
> actually i wasnt really thinking of creating a massive sweet game, i did some programming and i realize that im guan have to create a low quality game, so i was thinkin something like that old black and white aliens game where they keep getting faster for everyone you destroy and your a little spaceship...that one

Sounds like a good idea :)

---

### Post by Wybiral on 2006-12-12
Look at some C++ source code, maybe take a day or two trying to learn it... If you don't understand "if" conditions and "for" loops after a couple of days, forget about C++ for now and try python. I suggest not using an EDI or editor or anything, just use a text editor and write everything from scratch, this will help you write better code (relying on an IDE to highlight your errors is a bad habit).

Very simple:

1. A simple text based adventure game, it only requires a bunch of if statements and user in/out.

2. A "guess the number" game. This is a classic first program example... The computer generates a number between 1 and 100 and the user tries to guess it. For each guess the computer returns whether they guessed too high or two low until they guess the number. This teaches user in/out, if conditions, and comparison operators.

Easy:

1. Pong is a really good first game. It teaches you a lot of the basics of 2d game programming.

2. Something like a dartboard type game (like the games that have two power bars that you have to press a button, then release to determine the final location of the dart). That would be a very simple first game.

3. A platform-style game like mario or jetpack, but one that doesn't scroll (it's not hard to build them when everything is all on one screen)

Medium/hard:

If you know any 3d math (basically just trig), using pyOpenGL to create a one-floored cell/cube-based FPS shooter would be pretty easy. You can think of a one-floored FPS as a 2d game viewed from 3d (the player cannot jump or go up stairs or anything, this eliminates a lot of the more challenging aspects of a game engine).

---

### Post by samjh on 2006-12-13
> **Fittersman said:**
> i am going to be going into cs30 in high school and i want to create a game for my project. what is a relatively easy to learn language that can create a game and run on ubuntu. 

also if you could send me a link that has how to learn to use it and a list of the commands you can use that would be great.

Firstly, what languages do you already know, if any?  There is no need to reinvent the wheel.  If you already know a programming language, that language should be your first consideration.

But if you don't know any languages, then as others have suggested, Python is a good choice.  [http://docs.python.org/tut/](http://docs.python.org/tut/)  In Ubuntu, just go into your terminal and type in "python" without quotes, and you will get the Python interpreter.  Fiddle at will! :)

Whatever language you choose, writing a full-fledged game is not a trivial task.  Even with a relatively easy-to-learn language like Python, you may need 10-20 hours of self tuition to be competent enough to begin writing even a very simple tic-tac-toe style game with AI and GUI: a task that is sure to take several more hours at least.

---

### Post by Fittersman on 2006-12-14
what do you guys think about the difficulty of this site? (if your willing to check it out), its 
[http://www.psp-programming.com/tutorials/](http://www.psp-programming.com/tutorials/)

---

### Post by pmasiar on 2006-12-14
> **Fittersman said:**
> i downloaded pygame ... i ran config.py 

You need to be more patient and try to learn before start doing something. You need to learn how to do stuff the right way. BTW it is also faster: is faster to open the door than making hole in the wall by banging your head :-)

Right way to install stuff in Ubuntu is via Synaptic (or apt-get if you prefer  command line). One of the reasons why Ubuntu (and debian) is so popular is Synaptic: it will resolve all your dependencies. Installing by hand doesn't make sense - especially it you have no idea what are you doing. :-)

Try installing pygame via synaptic and tell us if you have any errors.

---

### Post by Fittersman on 2006-12-15
haha thats the problem also, i like command line because it gives me specific things to type in and i start to learn what each command does but in symnatec the files are not names the way you would see them on a website so i dont know what files i need to install to get hte package up and running.

---

