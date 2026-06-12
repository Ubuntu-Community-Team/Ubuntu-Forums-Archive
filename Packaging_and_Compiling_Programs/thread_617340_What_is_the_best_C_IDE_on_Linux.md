---
title: "What is the best C IDE on Linux?"
date: 2007-11-19
forum: Packaging and Compiling Programs
---

### Post by sc30317 on 2007-11-19
What is the best C IDE on Linux?

Your thoughts?

---

### Post by meatpan on 2007-11-19
You cannot ask or answer this question unless:
o  You have an understanding of the type of programming that needs to be accomplished.  Is this a small or large project?  Do you need packaging support?  Will there be gui design?  How much (and what kind) of debugging is necessary?
o  The programming talent of the user is well understood.  Expert programmers will likely use different IDE's than novices.

---

### Post by sc30317 on 2007-11-19
I am a novice programmer, and I am programming text based only ansi stuff.  We use gcc to compile programs and gdb to debug.

---

### Post by KoRnholio on 2007-11-19
I like KDevelop, its pretty easy to learn.  It comes with either its own debugger or a gdb interface (most likely the latter), which helps a lot.

---

### Post by avik on 2007-11-19
Personally, I just use Gedit (and I'm sure Kate on KDE would be good as well).  As long as you're making relatively small programs , then that should be enough.

There's Anjuta, but I didn't like the fact that it made me set up a project for everything.  For my needs, which I'm guessing would be similar to yours, the extra files created were not worth it.  From my experience, that has been the case for many IDEs, which are geared toward huge projects.

As long as you're using CLI tools, makefiles are great, and Gedit (assuming you use GNOME) has the right plugins for many tasks, including a class browser and limited code completion.

For what you described above, that should be good.  At least it has been for me.

---

### Post by mrman208 on 2010-03-23
hi, i am too wondering what is a good C IDE for Ubuntu.

I am a pretty advanced programmer and am planning a pretty big project. (shh. its a secret ;) )

---

### Post by cubeist on 2010-03-24
There are a ton of "Which IDE" threads on these forums, and a ton of discussions elsewhere on the web:

[http://lmgtfy.com/?q=IDE+Linux]("http://lmgtfy.com/?q=IDE+Linux")

There is even a comprehensive sticky on the Programming and Development forums which answers all your IDE questions!

[http://ubuntuforums.org/showthread.php?t=1006662]("http://ubuntuforums.org/showthread.php?t=1006662")

---

### Post by thesenu on 2010-03-25
you can use default gcc
or install netbeans and add the c/c++ plugin
:D

---

### Post by joshua.rh on 2010-03-25
I haven't found anything I like better than geany as of now.  You can easily change the compile command (I'm sure you can do this elsewhere, it's just easy in geany).  Another thing that's cool about geany is it's fast.  You can open a bunch of files, wait a few secs, then search em all quickly.  Geany is also stable.  I can't recall any problems I've had where I thought afterwards: "well they messed up".  The last thing I'll say about geany is it has a clean interface. I turn most everything off, as I just like to get to my work, especially if I'm doing it for a class and won't be working with a team.  You can find it at [http://geany.org/](http://geany.org/)  .  Good luck with you're C programming,

Josh

---

### Post by user333 on 2010-03-25
I use code::blocks for c++, but it does c too

---

### Post by ermalguni on 2010-04-01
I am currently using Eclipse CDT.

---

### Post by marioandres on 2010-04-01
I think the best is vim and make from command, with your own makefile.
But if you like use an IDE, i like Eclipse. :)

---

### Post by km0r3 on 2010-04-02
> **marioandres said:**
> i think the best is vim and make from command, with your own makefile.
+1

---

### Post by CarlosRuiz on 2010-04-03
Hi:

For me, the best IDE for Linux is GEANY...

It's very simple and easy to use, and it has a lot of very useful tools for any kind of programmers (novice and seniors)... you can use it for small or big projects... xD

Byeee... :P

---

### Post by mohitd2000 on 2010-04-18
> **ermalguni said:**
> I am currently using Eclipse CDT.
+1 I love Eclipse IDE. It tends to my Java, Andriod (ADT), and C/C++ (CDT) needs. Plus, there are hundreds of plugins for Eclipse.

---

### Post by pconroy on 2010-04-18
> **thesenu said:**
> netbeans and add the c/c++ plugin
:D


that's what I use.

---

### Post by cupid1102 on 2010-04-28
> **marioandres said:**
> I think the best is vim and make from command, with your own makefile.
But if you like use an IDE, i like Eclipse. :)

I have the same ideas with u :lolflag:

---

### Post by alexmurray on 2010-05-02
emacs ftw

---

### Post by lucasp0927 on 2010-06-09
IMHO emacs with cedet and ecb is the best IDE

---

### Post by WitchCraft on 2010-06-17
CodeBlocks + wxFormBuilder

---

### Post by Tom Dignan on 2010-07-11
For C? I personally prefer gvim with ctags and a terminal emulator.

---

### Post by ibuclaw on 2010-07-11
Vi... Because everything else is complicated enough... :P

Also, an IDE that crashes is worse at facilitating coding than a piece of paper.

---

### Post by Tech2077 on 2010-07-12
I'm surprised it hasn't turned into the usual emacs vs nano vs vim vs gui war. Hands down the best ide for a novice is a mix of vim/nano/emacs/gedit with gcc/makefiles. When you get to over 10 files, then you can move onto ide's like code::blocks, netbeans, or eclipse.

---

### Post by DJPhilTBCollins on 2010-10-22
> **joshua.rh said:**
> I haven't found anything I like better than geany as of now.  You can easily change the compile command (I'm sure you can do this elsewhere, it's just easy in geany).  Another thing that's cool about geany is it's fast.  You can open a bunch of files, wait a few secs, then search em all quickly.  Geany is also stable.  I can't recall any problems I've had where I thought afterwards: "well they messed up".  The last thing I'll say about geany is it has a clean interface. I turn most everything off, as I just like to get to my work, especially if I'm doing it for a class and won't be working with a team.  You can find it at [http://geany.org/](http://geany.org/)  .  Good luck with you're C programming,

Josh
I found this thread fairly high up on a google search and I joined up just to say thanks for this. It's just what I was looking for, and I figured I'd take the calculated risk of bumping a dead thread to put some useful info in case others follow the same path I did.
I've just begun to learn C as a first language since C64 basic, and Geany is the perfect step up from gedit and a terminal window. I'd recommend it to anyone who's learning from the very start with pdf files and googling error messages.

Thanks again guys, time to go play with arrays. :)

---

### Post by ibuclaw on 2010-10-22
Oh no he didn't! :evil:

Thank-you everyone for your contributions. If the age of this thread isn't a good indication, I'm putting this discussion to sleep.

Have a nice day.

---

