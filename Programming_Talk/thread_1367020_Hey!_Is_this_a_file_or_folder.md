---
title: "Hey! Is this a file or folder??"
date: 2009-12-29
forum: Programming Talk
---

### Post by Mathew Roy on 2009-12-29
Hi all,
 I am a LINUX newb!...

I am making a small program in c to encrypt files. The program accepts the <source file> and <destination file> as arguments (using getopt()).
So there is a chance that someone may give path of a folder as source file!. And when that happens my program should be able to recognise it and should open the folder and should process all files inside it. 
I just dont know how to do that. Can any one plz help me...

One more thing, is there any way to find the size of a file through program (by not using seek()). In windows this is possible by reading ffblk structure. But how do I do it under LINUX?:confused:

Now my program is completely command line, and I would like to make it GUI (Graphical User Interface), plz help me do that too.

I have attached the whole code with this thread!..

Plz help me...

---

### Post by Some Penguin on 2009-12-29
man stat/lstat/fstat

As for GUI-ization, pick and learn a GUI toolkit.

Simplest method I ever saw was XForms -- GUI layout tool which created callback stubs for you, paired with a library -- but that's *long* dead.

---

### Post by Mathew Roy on 2009-12-29
> **Some Penguin said:**
> man stat/lstat/fstat

As for GUI-ization, pick and learn a GUI toolkit.

Simplest method I ever saw was XForms -- GUI layout tool which created callback stubs for you, paired with a library -- but that's *long* dead.

hi, it would have been really helpful if u had explained it a little!...err...well I am a newb!!! :-k
I am even new to the GUI programming world. So I dont understand what these callbacks mean!. Well I have "Glade Interface Designer" installed.

---

### Post by Some Penguin on 2009-12-29
Well, read the stat/fstat/lstat manpage.  Pay attention to the section on POSIX macros that operate on the st_mode field.  Pick the invocation that applies to what you have -- a file descriptor or a path.

As for GUI toolkits, there's no magic shortcut.  Pick one and learn it.  This is somewhat of a holy war, with some preferring Qt, some GTK, probably some Motif holdouts.  Then read the tutorials.

---

### Post by Mathew Roy on 2009-12-29
well,
plz pardon my ignorance!
what really is the stat!?. Is it a program or function??. How do I  invoke stat from my program. 
I am terribly sorry for my ignorance..
Thanz 4 all help extended.

---

### Post by Some Penguin on 2009-12-29
Type 'man fstat'.

It's a function.  Well, three very similar ones.   Read the manual page.  There's even sample code at the end of it.  It's pretty POSIX-based, so the specific macros should translate well to other 'nixes.

---

### Post by Mathew Roy on 2009-12-29
Thank u very much!
Now I understand how to find size of a open file using fstat().
But I need something more.....
I want the list of all files inside a folder. Some function corresponding to findfirst, findnext (windows)  in LINUX.

---

