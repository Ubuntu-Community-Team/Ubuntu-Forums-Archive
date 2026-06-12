---
title: "n00b question on opening executables"
date: 2006-12-01
forum: Programming Talk
---

### Post by riven0 on 2006-12-01
Alright, this is going to sound stupid, but I'm trying to edit this executable file and I can't get it to open. I've tried everything from vim to emacs to gedit and more, and it just won't open! 
Alright, in vim and emacs it does open, but I get a bunch of characters like this:
> ?ELF^A^A^A^@^@^@^@^@^@^@^@^@^B^@^C^@^A^@^@^@&#1031;^D^H4^
@^@^@<a0>^T^@^@^@^@D^H<84><a2>^D^H\^A^@^@h^A^@^@^F^@^@^@^@^
P^@^@^B^@^@^@<98>^R^@^@<98><a2>^D^H<98><a2>^D^H<c8>^@^@^@<c8>
^@^@^@^F^@^@^@^D^@^@^@^D^@^@^@(^A^@^@(<81>^D^H(<81>^D^H ^@^@^@ 
^@^@^@^D^@^@^@^D^@^@^@Q<e5>td^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^
@^@^@^@^F^@^@^@^D^@^@^@/lib/ld-linux.so.2^@^@^D^@^
@^@^@^@^@^

So my questions is: what exactly am I doing wrong? Do I need a plug-in or something? ](*,) 

BTW, the file is a ELF 32-bit LSB executable...

---

### Post by 23meg on 2006-12-01
Why exactly are you trying to edit a binary? Try a hex editor instead of the usual text editors.

---

### Post by riven0 on 2006-12-02
I'm trying to configure the enlightment_start to load xscreensaver and ivman at startup. I always assumed I would just edit the xsession file, but then I read on the net that the bin file should be edited. So I actually have no idea what I'm doing, ](*,) but I'm going to test it out.

BTW, know any good hex editors?

thanks for the help so far :)

---

### Post by riven0 on 2006-12-02
Hold on a minute! I just checked out the hex editors and I'm pretty sure that's not what I need. Hmmm, I think I've been played for a fool.  #-o  I'm going to look at the enlightenment.desktop file again....

---

### Post by tribaal on 2006-12-02
EDIT: Most often, you'll want to modify the program's _source code_  and then recompile it... you hardly ever edit the binary file directly (except when you're trying to reverse engineer or hack/crack it). If for some reason you do want to edit a binary file then the hex editor is the (only) way to go.

Hum not sure if that's what you're looking to do, but to *execute* a binary program, double-clicking in nautilus doesn't work like in windows.

The easiest and trouble-free way is to run it from the command line, or try making a launcher for it.

A good proportion of binaries are programmed to be accessed by the command line interface...

Hope this helps

- trib'

---

### Post by riven0 on 2006-12-02
> **tribaal said:**
> Hum not sure if that's what you're looking to do, but to *execute* a binary program, double-clicking in nautilus doesn't work like in windows.

The easiest and trouble-free way is to run it from the command line, or try making a launcher for it.



Hehe, thanks for the help, tribaal, but that wasn't exactly what I was looking for. I know how to execute a binary, (I'm using Thunar with e17), but I read on a website I would have to *edit* the binary if I wanted xscreensaver to run at startup. It looks like I should have just listened to my intuition and ignored that advice instead of going through all this trouble...#-o

---

### Post by coder_ on 2006-12-02
I believe E17 comes with tools to do what you need, as it did when I last used it with SuSE.

You have to use GUI tools, or a commandline program to create the files for you.  I am annoyed by E17 in that aspect, but hey!  It sure looks good when properly configured!  ;)

---

