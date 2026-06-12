---
title: "keystrokes"
date: 2009-01-17
forum: Programming Talk
---

### Post by akimatsu123 on 2009-01-17
Hi,

First, I would like to say this is purely educational. I want to write a C++ terminal program that will log key strokes. Doesn't have to be discrete or anything like that, I don't plan on using it on anyone so the program can just be blatantly running in the foreground. 

Can someone point me in the right direction? Which commands should I use?

---

### Post by stroyan on 2009-01-17
How you log keystrokes will depend on details you haven't stated.
You may log characters using a pty device file.  That will be like recording a single terminal.  The 'script' command from the bsdutils package does that.  You can get the source for script to see how it works.  "apt-get source bsdutils" and look at util-linux-2.13.1/misc-utils/script.c .

You could try recording all keystrokes to an X server.
The Xnee package does that.  You can get the source from it to see how it works.
"apt-get source xnee"
The xnee and libxnee-dev packages are in the "universe" repository.  (Or see [http://www.gnu.org/software/xnee/](http://www.gnu.org/software/xnee/) .)

You may need to add source code and universe to your ubuntu system's software sources list.  You can do that with the "System"->"Administration"->"Software Sources" menu item.

---

