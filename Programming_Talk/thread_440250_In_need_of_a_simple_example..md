---
title: "In need of a simple example."
date: 2007-05-11
forum: Programming Talk
---

### Post by locke.dragon on 2007-05-11
For the project I'm working on, I need a simple GUI written in C that can edit variables in a text document.  Could someone point me in the direction of an example that would do something like this?  I'm not very good at writing code from scratch, but I'm able to easily work with code as long as I have an example.  Please help.

---

### Post by Blacktalon on 2007-05-11
Hmm...that sounds to much like doing some one's homework.

But if you want an example code try doing a search through google, that's the best help you find pretty much.

But if you need some help coming up with ideas to help you get started on how this would work, I can definately help you there:

1.  Use some code that takes in a paramater of a file name.
2.  inside you code ask for an letter or word that you would liked changed.
3.  save that input.
4.  Ask what you would like it changed to.
5.  Save that input
6.  Use a search (Linear probably would be best for this even though it would be pretty slow).
7.  Rewrite the word with the changed word.
8.  Save file, and exit.

This one should be to bad to implement, it will just take a little bit of time and effort.

Good luck!

---

### Post by locke.dragon on 2007-05-11
thanks for the advice, but just for future reference, it's not homework, it's a dock i'm working on.

[http://www.thelinuxdock.blogspot.com/](http://www.thelinuxdock.blogspot.com/)

---

### Post by Blacktalon on 2007-05-11
Gotcha!

Sorry I can't help much more then that but I am not very good at 'C', I know Java myself

---

### Post by locke.dragon on 2007-05-11
would java work in this situation?  the GUI doesn't have to be C, as long as it can edit a text file that has C code in it, recompile somehow, and re-run the C program, anything would do!  :D

---

### Post by nicholas22 on 2007-05-11
Basically you could try GTK+ if you need pure C/C++ but this might be quite a steep learning curve.

Or you could would use a Java front-end and JNI, which links to C/C++ libraries.
Java has ample GUI-building tool support, such as the NetBeans, Eclipse, JBuilder IDEs.

Hope this helps

---

### Post by locke.dragon on 2007-05-11
yeah.  that helps alot.  thanks!  is there any way you could post links to those programs/plug-ins?

---

### Post by wtruong on 2007-05-11
you should just use a shell script, perl, or python.  replacing words is so much easier in there

---

### Post by locke.dragon on 2007-05-11
could you possibly point me in the direction of a simple example GUI?

---

### Post by FuturePast on 2007-05-11
personally I would do a shell script using zenity and sed.

---

### Post by locke.dragon on 2007-05-11
cool.  thanks for the idea.  that might be easier.  but would anyone here be willing to either point me to an example program or write one for me?  i'd be more than happy to include you as a member of the project and i'd kiss your feet if you wrote the script/GUI/whatever for me.  :P

---

### Post by FuturePast on 2007-05-11
```

$ cat someText 
Programming Talk:
This forum is for all %REPLACE% programming questions.
The questions do not have to be directly related to Ubuntu and any language is allowed.
$ sed --in-place "s/%REPLACE%/$(zenity --entry)/g" someText 
$ cat someText 
Programming Talk:
This forum is for all DoesThisHelp programming questions.
The questions do not have to be directly related to Ubuntu and any language is allowed.
```

---

### Post by WW on 2007-05-11
Since I am trying to learn more python, this seemed like a good exercise.  I took an older python program that I wrote, and hacked it up to do something that might be close to what you want.  Copy the files **edit_thing.py** and **main.c.txt** to a directory, rename **main.c.txt** to **main.c** (the forum software wouldn't let me attach main.c) and then in that directory, run
```

$ python edit_thing.py &

```

---

### Post by locke.dragon on 2007-05-11
omgsh!!!  [IMG]http://i159.photobucket.com/albums/t147/clipsandeggs/faint.gif[/IMG]  i can't thank you enough WW!  this is EXACTLY what i'm looking for!  i think that with some time and effort on my part, this will be EXACTLY what my project needs.  thank you thank you thank you!  (boy am i over-reacting.  [IMG]http://i159.photobucket.com/albums/t147/clipsandeggs/sweat.gif[/IMG])  [IMG]http://i159.photobucket.com/albums/t147/clipsandeggs/mwahaha.gif[/IMG]

---

