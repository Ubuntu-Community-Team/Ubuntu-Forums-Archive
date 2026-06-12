---
title: "How to install from a source without configure file?"
date: 2010-07-20
forum: Packaging and Compiling Programs
---

### Post by efrens on 2010-07-20
I'm trying to install a Yahoo chat client called GenY.
The source is available from it's website, [http://geny.sourceforge.net/](http://geny.sourceforge.net/)

My main goal was to be able to debianize the source so that I can "dpkg -r" if for some reasons I don't like what I see.

But I'm new to this whole thing of making packages, so upon searching the net I realized that I need to do a checkinstall -D to make the .deb file.

But, somewhere before that I learned that I need to run ./configure. The problem is, there's no configure file in the source.

So I searched again and learned that autoconf can make a configure file for me, but only if there's a config.in or configure.in in the source, but there is none either.

I'd like to know if I'm following through the right track. Because it seems to me I'm at a dead end.

Can anyone shed a light on this?
I badly want to debianize this GenY thingy and see if it works.

Thank you.

---

### Post by SevenMachines on 2010-07-21
checkinstall can deal with any wrapping up of source code as long as it has a command to build/install it. you dont necessarily need ./configure or anything more advanced.
You can add the 'installation' command as an option to checkinstall (it does autodetection for 'ususal' commands and this usually isnt needed), if the source only has a Makefile you'll probably use

$sudo checkinstall make install

Geny wont work for me without fixing a few problems with newer gcc's so i cant tell you how checkinstall will go for you.

Note you might be fine just running the program from the directory you built it in

---

### Post by efrens on 2010-07-21
Thanks for the reply.

But doing a sudo checkinstall make install gave me this. And I have no idea what to do.

make: *** No rule to make target `/usr/share/qt4/mkspecs/linux-g++/qmake.conf', needed by `Makefile'.  Stop.

I guess I should just give up?

(all I wanted was to make webcam work with a Yahoo! Messenger alternative anyway)

---

### Post by SevenMachines on 2010-07-21
you'll need qt4-qmake
$sudo apt-get install qt4-qmake

i dont think the source is set up (at least not obviously to me :) ) for  a system install. you should be able to just run make and then run ./geny from the build directory to try it out

---

### Post by efrens on 2010-07-21
hey thanks.
I think I was able to install it. Yay!

Now how do i run it?

Sorry for my ignorance, but when I run geny the terminal says there's no such program... (I can dpkg -r it though)

I wonder where it went. No traces in /usr/bin. What now?

---

### Post by SevenMachines on 2010-07-21
it looks like the Makefile has a rule for install but it doesnt do anything :( since checkinstall uses this 'do nothing' rule, it works in creating a .deb file but doesnt actually install anything (since the Makefile doesnt). This is probably a sign that geny is a work-in-progress(!) but you can still test it out by not using checkinstall and instead just trying to build the source and run in locally (ie, in the build directory)
$make
$./geny

---

### Post by SevenMachines on 2010-07-21
just to add, if you're looking for your webcam to work with a yahoo messenger alternative there might be better and more well known programs for this, but i have to admit i know nothing about that sort of thing :) 
if you want to try and get this one working i'll try and help but you might also want to post in other more general forums if you're looking for a working alternative

---

### Post by efrens on 2010-07-21
I tried. It gave me errors.
It really is a work-in progress software anyway.

Although I think I learned a lot from this. Thanks.

---

