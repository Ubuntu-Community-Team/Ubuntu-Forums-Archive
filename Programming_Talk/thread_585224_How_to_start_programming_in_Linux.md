---
title: "How to start programming in Linux?"
date: 2007-10-21
forum: Programming Talk
---

### Post by Wolfrat on 2007-10-21
Long time reader, first time poster.

Sorry if this post seems very stupid/simple, but I'm pretty new to Linux.

I'm just wondering, what programming language/programs etc. should I use to make the following program? (and for it to work in ubuntu)

Basically I want the program to:
1. Have a slider, with positions 1 to 100 (or so), and then store the slider's value in a variable.
2. I then want the program to execute the command 'smartdimmer -s [variable stored from slider].

I know it seems really simple, but it seems like a good place to start for me, and at least this way, by the time I'm done making it, I actually have something I can use, and I'll have gained lots of knowledge.

So yeah, I'd just like to know how I should go about developing something like this for ubuntu.

PS: I have lots of experience in PHP, and some knowledge of Java.

Thanks in advance.

---

### Post by kebes on 2007-10-21
The best way to learn programming or a new language is to have specific goals to keep you interested... so your idea for a simple program is a very good one.

There are of course many languages that can accomplish what you want, and everyone has different preferences. My recommendation would be to learn Python. It is a very clean language (so fast to learn), but is also one of the most powerful and feature-complete languages I've seen. (It's also well-supported in Ubuntu specifically.)

With regard to the specific program you want to write, Python has GUI toolkits that will help you make the graphical aspects, and
can make arbitrary shell/system calls, which is what you need.

There are many Python GUI toolkits to choose from, but the most popular appear to be wxPython, pyQT, and Tkinter. I'm sure they are all good. I've used pyQT in the past and the IDE makes it easy to generate GUI elements (drag-and-drop). 


With regard to learning how to program in Python, what you need to do is find some tutorials and run through them. There are so many to choose from it's hard to pick. [This Python tutorial]("http://docs.python.org/tut/tut.html") looks good, I've used [this intro to pyQT ]("http://www.cs.usfca.edu/~afedosov/qttut/") and it was helpful, though a bit light on details. [This forum thread]("http://ubuntuforums.org/showthread.php?t=333867") has links for introductions to all kinds of languages (including [Python]("http://ubuntuforums.org/showthread.php?t=333867#5")).


I hope that helps.

---

### Post by Wolfrat on 2007-10-21
Thanks, I'm googling those programs and designers you just mentioned. I'll post in the forum again once I complete my little program ;)

---

### Post by Acglaphotis on 2007-10-21
EDIT: Wrong thread

---

### Post by LaRoza on 2007-10-21
> **Wolfrat said:**
> Long time reader, first time poster.

Sorry if this post seems very stupid/simple, but I'm pretty new to Linux.


The sticky titles "New to Programming in Linux -- Read This" might be a good start.

---

### Post by Wybiral on 2007-10-21
I suggest Python as the language and GTK as the GUI API. A slider + button application should be pretty straight-forward for someone who has already done some programming in other language.

---

### Post by Nekiruhs on 2007-10-21
I too recommend Python. Also use Glade (Package: glade-3) to design the GUI.

---

### Post by spinetingler on 2007-10-21
I have progragrammed VB for several years and have recently decided to put more focus in ubuntu. I like you wasn't sure where to start but the answer cam screaming at me... I started with Python because I was attracted to its cross platform ability and became much more interested after seeing the different toolkits available. I have decided to start with wxPython but plan to do some development in Glade also. Good luck on your quest.

---

