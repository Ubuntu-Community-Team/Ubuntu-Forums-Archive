---
title: "Compile from source .tcl"
date: 2007-05-02
forum: Packaging and Compiling Programs
---

### Post by Lutherian on 2007-05-02
There comes a time in every Windows-to-Linux refugee's life when they realise that they can't go on avoiding "compiling from source". This is the day and I have to jump off the cliff.

I'm trying to compile a program that would be called notebook ( A personal wiki type program) I know *nothing* about programming. I don't even know what the significance of the .tlc extention is, or what programming language this the source is written in. (C C++ C# ?) I tried some commands such as [COLOR="DarkRed"]**sudo make file -f Makefile**[/COLOR] - ofcourse nothing happened.

For now I'm hoping for a cut-and-paste solution and perhaps some pointers to where I could get more info - else face the RTFM response, which I would deserve if I didn't at least try to understand.

Below are the  source files that I have extracted to a folder on my Desktop
Thanks to all
===================================================


drwxr-xr-x  3  4096 2007-05-02 19:35 ./
drwxr-xr-x 11  4096 2007-05-02 21:16 ../
-rw-r--r--  1  1106 2005-04-03 05:38 canvas.tcl
-rw-r--r--  1   476 2005-04-12 16:41 hdr.tcl
-rw-r--r--  1   844 2005-04-17 02:23 home.txt
-rw-r--r--  1   573 2005-04-23 19:05 keys.tcl
drwxr-xr-x  9  4096 2007-05-02 19:35 lib/
-rw-r--r--  1  2143 2003-12-11 21:19 license.txt
-rw-r--r--  1    70 2003-12-11 21:19 main.tcl
-rw-r--r--  1  1511 2005-04-26 18:41 Makefile
-rw-r--r--  1 17029 2005-05-30 18:46 README.txt
-rw-r--r--  1   519 2004-10-20 04:49 temp.tcl
-rw-r--r--  1   235 2004-12-05 02:11 temp.txt
-rwxr-xr-x  1   247 2004-10-18 02:22 test.tcl*
-rwxr-xr-x  1   948 2003-12-11 21:19 update.tcl*

---

### Post by WW on 2007-05-02
[Tcl]("http://en.wikipedia.org/wiki/Tcl") is a scripting language.

Did you find any instructions in the file **README.txt**?

---

### Post by Lutherian on 2007-05-02
Hi WW - thanks
as for the readme file... it wasn't too helpful, basically a list of bugfix info, installation info for the windows executable and then this statement for "other systems"

[COLOR="Red"]"For other systems, you'll need to download "notebook.kit" and 
the TclKit runtime for your platform from
[http://www.equi4.com/pub/tk/8.4.9](http://www.equi4.com/pub/tk/8.4.9).  Put the TclKit runtime on
your path, and mark notebook.kit executable."[/COLOR]

Although this doesn't sound like compiling to me - ofcouse now that you say that Tcl is a *scripting language* - it starts to make sense - so then I wouldn't compile this at all, just run it as if it were a batch file, script file or macro etc, etc 

What confuses me is the I thought that "Makefile" is something used to make an installation file ...anyway I'm getting side-tracked. 
Still somewhat confused though LOL

---

