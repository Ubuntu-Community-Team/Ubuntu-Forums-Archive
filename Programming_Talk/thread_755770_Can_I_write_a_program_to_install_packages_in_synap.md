---
title: "Can I write a program to install packages in synaptic?"
date: 2008-04-15
forum: Programming Talk
---

### Post by mattgaunt on 2008-04-15
Hey everyone,

I have an idea for a program that saves all my thunderbird, firefox, background image and so on, as well as un-install and install programs that I prefer to the standard install, on my main computer.

This is just an attempt to make upgrading ubuntu a slightly easier and pleasant process by only having to save one file file produced by this program and then running the program on a new install.

I was just wondering if anyone can shed some light on if this is possible?? If it is I imagine I would need to use some sort of API of linux to program it in C.

But any ideas and anyone have any gd advice or guidance??

Gaunt

---

### Post by loell on 2008-04-15
manipulate **apt** by python. 

or package these files as deb(s)

---

### Post by Tuna-Fish on 2008-04-15
C is a really bad match for this kind of thing.

Just make a bash script. Like this:
[php]
#! /bin/bash
apt-get install //names of all the packages you like, separated by spaces. no endlines until the end
apt-get remove //packages you want to get rid of
[/php]
then save that as some file, and turn the execute rights on for it (chmod a+x filename.sh from the terminal)


Generally all programming languages have a purpose for which they are good. C is for systems hacking and for writing something that REALLY has to be very fast. This is a scripting task, use a script for it.

---

### Post by mattgaunt on 2008-04-15
One thing I did want to do is make it something it is fairly adaptable and possibly usable by other people, which means it would have a GUI front end to control it.

Python is a language I am planning on learning over the summer so cud be gd opertunity to use it for this.

Thanks for the replies tho guys

---

### Post by EXCiD3 on 2008-04-15
Python and PyGTK would work prefect for you. Easy to program, fits the purpose and allows for an easy gui :D

---

