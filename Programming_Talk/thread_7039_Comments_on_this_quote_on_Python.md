---
title: "Comments on this quote on Python?"
date: 2004-12-03
forum: Programming Talk
---

### Post by littlegreenman on 2004-12-03
Hi all,

I am starting to learn Python. I am  a beginner in the world of programming (know some HTML, know some Basic from the time of the Spectrum 48K, and that's that), but read the Python Help file on Ubuntu, found it interesting and started playing with it.

I found this quote on [http://www.computershopper.co.uk/shopper/labs/64701/python.html](http://www.computershopper.co.uk/shopper/labs/64701/python.html)

"Python's only real drawback is that it has no facilities to allow the beginner to create graphics or games, which makes it a little duller for the novice than the likes of DarkBASIC. It also doesn't have a wide acceptance in the professional programming world except as a scripting language on non-Windows machines, and it isn't built for speed or efficiency. However, if you learn Python you are well positioned to understand the more important object-oriented languages. Python is a good choice for learning but it isn't particularly powerful."

Would be very interested to read any comments you may have.

Thanks.

---

### Post by jdodson on 2004-12-03
[QUOTE=littlegreenman]Hi all,

I am starting to learn Python. I am  a beginner in the world of programming (know some HTML, know some Basic from the time of the Spectrum 48K, and that's that), but read the Python Help file on Ubuntu, found it interesting and started playing with it.

I found this quote on [http://www.computershopper.co.uk/shopper/labs/64701/python.html](http://www.computershopper.co.uk/shopper/labs/64701/python.html)

"Python's only real drawback is that it has no facilities to allow the beginner to create graphics or games, which makes it a little duller for the novice than the likes of DarkBASIC. It also doesn't have a wide acceptance in the professional programming world except as a scripting language on non-Windows machines, and it isn't built for speed or efficiency. However, if you learn Python you are well positioned to understand the more important object-oriented languages. Python is a good choice for learning but it isn't particularly powerful."

Would be very interested to read any comments you may have.

Thanks.[/QUOTE]


hrmmmm, ok well according to your quote they think python is bad for a few reasons:

1.) no graphics or games libraries
2.) its not very popular on windows
3.) isnt for speed of efficentcy

ok starting with the first one.  these people do not realize the power of pygame([http://www.pygame.org/](http://www.pygame.org/)).  pygame is the reason i will only develop games in python.  seriously, check it out, it owns all.   so they simply did not do any homework on this one.  if they mean NATIVE support, then i guess few programming languages are "good" enough for these people.

the second point is simply stupid.  just because python is popular on *nix and not windows as much does not mean it is not a good language.  python is becoming more and more popular and some school are even switching to it in curiculum.  i think this point is simply not worth the material it was typed and saved on.  just because one language is "popular" does not make it better.  take visual basic for instance, very popular, does that make it good?  i think what makes a language good is subjective, however i do have opinions on what languages i consider good.

last point.  ok well few languages are build for speed and efficency.  if you want mega speed use C, if you more speed use assembler.  the beauty of high level interpreted languages is the speed at which you can construct something.  it is important to realize that programmer time is often more expensive then a few clock cycles.  i am not condoning bad code, far from it, i just realize that sometimes a high level languages works well.  i understand that implementing the kernel in python is not a good idea, python is not a kernel language.  it is a fast development OOP like coolorama toolkit that has much functionality.

if this person complains about python speed and uses Java, they need to be flogged.  however there are some that feel that assembly is the only way to ride......

---

### Post by Daniel G. Taylor on 2004-12-03
Well, jdodson did a pretty good job of knocking their arguments down, but I thought I'd just add a few comments of my own.

First off, Python is _very_ easy to interface with C libraries. A good example against their game comment is that there are OpenGL bindings for Python. Check out the NeHe tutorials, they all have Python versions. Because it's actually calling the C code in the OpenGL libraries, it's fast. Very fast.

Another reason Python isn't slow as they claim is that all the interpreted code is byte-compiled. You will notice that Python creates .pyc files, those are the byte-compiled versions that Python actually uses to run. Because of this, it's much faster than if it were just interpreting the language without an intermediate step. Java works in a similar way to this, as does C#. Notice, it will be slower than plain C, but I wouldn't call it slow.

About not being popular on Windows, every book I have read on Python used Windows for almost all their examples, and many system administrators that I know use it for administration tasks (running Windows servers).

About Python not being powerful, I have to laugh. If you have a C library, Python can use it (with a bit of help, of course, but you don't have to rewrite the library). Python comes with a  standard library that is amazing, and is so easily extensible I am still amazed. Python runs on practically any platform, and on practically any hardware.  You can even test parts of your code interactively in the interpreter (and write new code to test there as well).

Python is an excellent lanugage for pretty much any task in my book (unless it's some huge number-crunching thing) and it's my favorite language (so yes, I'm biased).

---

### Post by daniels on 2004-12-04
I'll be a little less verbose, because it's already been said well -- the quote is, simply, complete crap.

---

### Post by jdodson on 2004-12-04
[QUOTE=daniels]I'll be a little less verbose, because it's already been said well -- the quote is, simply, complete crap.[/QUOTE]


ha!  right.   :mrgreen:

---

### Post by zeroK on 2004-12-29
To be honest I also don't understand their gaming example... why would you code a "graphical game" - I mean something like Quake or UT - in a language like Perl or Python? You need high performance so the best choices would be C or C++ (in combination with some ASM hacks perhaps ;-) ). 

For the rest... I totally agree with daniels *g* The statement is crap**.**

---

### Post by Quest-Master on 2004-12-29
zeroK: There have been a number of games coded in Python. Check the interview on pygame.org about the commercial game which used it. They used Python as sort of the "glue" for the game; running the actual game, etc. etc. All of the raw stuff is usually done in C.

I must agree with the rest of you here as well: this quote is a piece of quote which should go by without being noticed.

---

### Post by jdodson on 2004-12-29
[QUOTE=zeroK]To be honest I also don't understand their gaming example... why would you code a "graphical game" - I mean something like Quake or UT - in a language like Perl or Python? You need high performance so the best choices would be C or C++ (in combination with some ASM hacks perhaps ;-) ). 

For the rest... I totally agree with daniels *g* The statement is crap**.**[/QUOTE]

i am programming a 2d tile based RPG akin to final fantasy 2 and dragon warrior in python using the pygtk libraries.  i dont imagine it would run much faster in C as all i am doing is updating GUI widgets and python makes the coding easier.  i tested it on old machines and it seems to work fine with no speed benifiet either way as my code is pretty tight.  i guess it just depends on what kind of game you are making.  then again i wouldnt use python for a 3D based game, unless it was a pretty low polygon count game.  

i have used pygame and have to admit it is a great interface to work with.  i chose to not use it for my game because i just need to draw tiles and pygtk is fine for that.  i need to get some python sound library for when i put in sounds, anyone know of one that is good?  i do not think python natively supports sounds for gnu/linux, though windows python supports .wav files, though it looks like it is a windows only thing.

-jon

---

### Post by Quest-Master on 2004-12-30
You could use sdl_mixer in Pygame for sound, or a more appropriate choice being pyAo.

I haven't tried GTK yet, but I don't see how it would be suitable for games. :o I should really try it out some times since I am interested in making a game exactly like the one you are aiming for (2D tile-based RPG).

---

### Post by jdodson on 2004-12-30
[QUOTE=Quest-Master]You could use sdl_mixer in Pygame for sound, or a more appropriate choice being pyAo.

I haven't tried GTK yet, but I don't see how it would be suitable for games. :o I should really try it out some times since I am interested in making a game exactly like the one you are aiming for (2D tile-based RPG).[/QUOTE]

it is good for tile based games for a few reasons(IMO).  The first reason is that you can create a full GUI for the game in it.  second is that you can create images that stand for the tiles, for instance my game has 240 images that are lined up in 12 rows of 20 images per row.  when my player moves i simply update the image i am moving to and update the image the player left from.  this makes movement low on the CPU as all you do is redraw 2 small image tiles.  this also avoids a constaint game loop as the GUI just awaits user input and sits idle when nothing is happening.  GTK also handles the keyboard input as well, so when the player pushes the "up" button GTK calls the move function.    most games in gnome or qt are made in similar ways, they just might use c or c++ instead of python.  

i just decided against pygame because it was a layer of abstraction i did not need, and i wanted to learn GTK.  plus ubuntu(i believe) natively comes with pygtk in the distro, so for ubuntu users at least, one less package to install.

---

### Post by wtd on 2004-12-31
[QUOTE=Quest-Master]zeroK: There have been a number of games coded in Python. Check the interview on pygame.org about the commercial game which used it. They used Python as sort of the "glue" for the game; running the actual game, etc. etc. All of the raw stuff is usually done in C.

I must agree with the rest of you here as well: this quote is a piece of quote which should go by without being noticed.[/QUOTE]

Exactly.  Python itself is implemented in C, and they've left an API for others to use to create Python interfaces in C.  So you prototype your game in Python, then convert the slow parts to C or C++ as necessary.  It's a beautiful way to create large projects.

[list]
[*]Make it work
[*]Make it work correctly
[*]Make it work fast[/list]

---

### Post by Quest-Master on 2004-12-31
And for people who want still want fast development time with the speed of C, SWIG and Pyrex are awesome.

---

### Post by poster_nutbag on 2004-12-31
[QUOTE=jdodson]i just decided against pygame because it was a layer of abstraction i did not need, and i wanted to learn GTK.  plus ubuntu(i believe) natively comes with pygtk in the distro, so for ubuntu users at least, one less package to install.[/QUOTE]

I'm writing a strategy game and also looking into using PyGtk, since it'll be GUI based, and I don't feel like coding a GUI in pygame. How easy is it to manipulate and update an image area in PyGtk for game purposes (basically a Civ-style map, with some minor animation, in my case)?

And, back on-topic:
The python quote must be from someone who has heard of python but not used it. Python is a great language to start learning with: it's free, easy to pickup, has plenty of online books to read through, powerfull and a ton of libs for all sorts of things.
Trust me, I've been coding since 1981, been through some 20+ languagues: I would reccomend python to anyone starting programming.

---

### Post by Quest-Master on 2004-12-31
I'm gonna have to talk to to you later about PyGTK jdodson.. it's really catching my interest now after reading your opinion and some articles on it. :)

---

