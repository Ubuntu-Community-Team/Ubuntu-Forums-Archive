---
title: "converting .glade file"
date: 2011-03-03
forum: Programming Talk
---

### Post by loserboy on 2011-03-03
following this tutorial here [http://www.micahcarrick.com/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/gtk-glade-tutorial-part-1.html).

I'm getting stuck converting a glade file to .c at this part in the tutorial

> /*
First run tutorial.glade through gtk-builder-convert with this command:
  gtk-builder-convert tutorial.glade tutorial.xml
  
Then save this file as main.c and compile it using this command
(those are backticks, not single quotes):
  gcc -Wall -g -o tutorial main.c `pkg-config --cflags --libs gtk+-2.0` -export-dynamic
  
Then execute it using:
  ./tutorial
*/



i converted the glade to xml, but then running the second command throws this error

```
$ gcc -Wall -g -o tutorial main.c `pkg-config --cflags --libs gtk+-2.0` -export-dynamic
gcc: main.c: No such file or directory
```

i can only assume it's because that command doesn't include saving the xml as main.c, so i did that by copying and renaming the file but im sure thats not right and it didn't work.

so yea what am i missing?

edit to add:
also having a problem when trying to run it through python 

```
$ ./tutorial.py
  File "./tutorial.py", line 14
    <?xml version="1.0"?>
    ^
SyntaxError: invalid syntax

```

---

### Post by loserboy on 2011-03-03
disregard. found a newer howto that makes more sense.
so that this thread is not a waste, someone with the problem i had might find this link useful

[http://jmoiron.net/media/legacy/glade1/](http://jmoiron.net/media/legacy/glade1/)

now where'd that solved button go

---

### Post by Milliways on 2011-03-03
> **loserboy said:**
> disregard. found a newer howto that makes more sense.
so that this thread is not a waste, someone with the problem i had might find this link useful

[http://jmoiron.net/media/legacy/glade1/](http://jmoiron.net/media/legacy/glade1/)

now where'd that solved button go

This tutorial is very old (2003?)
glade has changed quite a lot since, and I suggest you look for something more up to date.

[http://www.micahcarrick.com/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/gtk-glade-tutorial-part-1.html) is quite good, but still a little out of date

---

### Post by loserboy on 2011-03-03
the link you posted is the one i started at, but was unable to get anything to run. I found out after i posted that my second link was way old, but i go tired of talking to myself so i didnt repost. At any rate it at least gave me a window to look at when i ran it.

---

### Post by Milliways on 2011-03-04
> **loserboy said:**
> the link you posted is the one i started at, but was unable to get anything to run. I found out after i posted that my second link was way old, but i go tired of talking to myself so i didnt repost. At any rate it at least gave me a window to look at when i ran it.

I am not a Python programmer (trying to learn), but I used this to learn something about GTK.

I just saved 
[http://www.micahcarrick.com/files/gtk-glade-tutorial/PyGTK/tutorial.py](http://www.micahcarrick.com/files/gtk-glade-tutorial/PyGTK/tutorial.py)
and
[http://www.micahcarrick.com/files/gtk-glade-tutorial/part-1/tutorial.glade](http://www.micahcarrick.com/files/gtk-glade-tutorial/part-1/tutorial.glade)
and got it to run with little change.

One of the big differences to glade is that it now directly supports GtkBuilder format
Open the tutorial.glade, change preferences to GtkBuilder and save. (This may mention errors - ignore these for now.)

Change tutorial.py to open tutorial.glade rather than tutorial.xml
There is no need to convert using gtk-builder-convert tutorial.glade tutorial.xml

This may still work, but I have never had much success with this.

Read the section "GtkBuilder and LibGlade "

---

### Post by loserboy on 2011-03-04
thanks i'll give it a shot

---

