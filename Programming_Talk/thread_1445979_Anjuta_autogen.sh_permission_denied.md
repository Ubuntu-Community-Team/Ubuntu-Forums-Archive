---
title: "Anjuta autogen.sh permission denied"
date: 2010-04-03
forum: Programming Talk
---

### Post by heepie on 2010-04-03
I trying to make a very simple app with ajunta just to get the hang off it. But when I try to make a very simple app with it I'm getting some error messages. I'm creating a new project with anjuta, then I edit the *ui file where I add a couple of widgets, I make the right association with glade files (callback.c) But when I build the project I get this message:

Building in directory: /home/heepie/workspace/anjuta/gtk-foobar/Debug
/home/heepie/workspace/anjuta/gtk-foobar/autogen.sh --enable-maintainer-mode CFLAGS=-g -O0 CXXFLAGS=-g -O0 JFLAGS=-g -O0 FFLAGS=-g -O0

/home/heepie/workspace/anjuta/gtk-foobar/Debug/(anjuta:803): libanjuta-WARNING **: Cannot execute command: "/home/heepie/workspace/anjuta/gtk-foobar/autogen.sh"

execvp failed: Permission denied
Completed unsuccessfully
Total time taken: 0 secs


I'm sure it's a very simple option but at the moment i'm stuck and I tried everything I can think off. Going to the terminal didn't help either.

Using anjuta 2.28.00

---

### Post by kishan.b on 2010-12-22
I actually tried 
       sudo anjuta
It worked fine..

---

### Post by kishan.b on 2010-12-23
Its a pity that there are no other replies here..  If u know please take time to reply.. Bcoz ther are others who hav the same problem !!

---

