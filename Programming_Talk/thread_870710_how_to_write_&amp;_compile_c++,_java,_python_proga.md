---
title: "how to write &amp; compile c++, java, python progams in emacs"
date: 2008-07-26
forum: Programming Talk
---

### Post by sam2501 on 2008-07-26
i want to write c/c++, java & python programs & should be able to compile them in my emacs


i am new to this whole ubuntu, linux, emacs scene but i was able to install 
common lisp & now able to compile lisp programs from emacs


i want to know whether if this can be extended to other languages as well & am really confused:confused::confused:



it wud be cool if i can compile in all these languages in emacs rather than 
a seperate app for each one


forgive me if posted this thread in the wrong place

---

### Post by ConMan318 on 2008-07-26
Emacs is a text editor, not a compiler.  You can write any program in emacs, and compile/run them in a terminal or as executables.

For starting off I would assume you want to be running them from the terminal.  In this case, you use Emacs to make the text file of the source code.  Then, depending on the language you are writing in, you run and/or compile that source code.  For example, for C, you would navigate to the folder containing the file that you want to compile.  Then you run
```

gcc fileName.c
./a.out

```

For python you would run "python filename.py".  Look up a tutorial on one of those languages.  Generally, the first thing that a programming tutorial covers is installing the language and then how to run programs.

---

### Post by sam2501 on 2008-07-26
you have a point der, but i want to compile them from within emacs
much like when i press
   M-x slime
i was taken to lisp repl or prompt
are there any ways of implementing other languages like this
where i can edit & compile lisp programs from within emacs by doing m-x slime rather than alternating between terminal & emacs for compiling & editing respectively  :(:(


And BTW thanks for the reply

---

### Post by darpified on 2008-07-26
Use `M-x compile’, which will run make in the current directory.

As long as you have the makefile properly configured, it'll use any programming language that you need.


For more grisly details, see this link.
[http://www.emacswiki.org/cgi-bin/emacs-en/CompileCommand](http://www.emacswiki.org/cgi-bin/emacs-en/CompileCommand)

---

### Post by shifty2 on 2008-07-26
> **ConMan318 said:**
> Emacs is a text editor, not a compiler.  
And that is the beauty of emacs :) It is whatever you want it to be.

Python is just a case of C-c C-c in python mode to execute the document you are currently editing.

---

### Post by LaRoza on 2008-07-26
> **shifty2 said:**
> And that is the beauty of emacs :) It is whatever you want it to be.

Python is just a case of C-c C-c in python mode to execute the document you are currently editing.

The only language emacs is capable of interpreting or compiling is its own form of Lisp. It isn't a compiler as stated.

---

### Post by Ruhe on 2008-07-26
For java programming in emacs use [**JDEE**]("http://jdee.sourceforge.net/").
But it's not the best environment for java programming. I love emacs and use it everywhere, but as java developer I prefer IDE's: NetBeans, IDEA, Eclipse.
Of course you can write and run your python and C (and java) programs inside emacs, type:
 M-x shell
and you'll get linux shell running in emacs.

---

### Post by shifty2 on 2008-07-26
I prefer term to shell (M-x term) it is just a more intelligent terminal.

I interpreted his comment as saying "emacs only edits text" whereas it has, as said earlier, built in methods for executing gcc, g++ etc. Initially it was asked if you can compile code emacs - which you can even if emacs is just a "text editor".

---

### Post by sam2501 on 2008-07-26
Your replies only answered my question partially or perhaps i couldn't get them

I guess i will ask the question clearly & plainly 

i wanted lisp so i installed slime, cmucl from synaptic,added a few lines
in .emacs file in my home dir

now, M-x slime command in emacs brought me directly to lisp prompt

here's my question

-> M-x <command> shud take me to a python prompt, c/c++ or java compiler implementer
-> what commands do i need.... & any additional software required other than those that come by default in Hardy



And thanks in advance

---

### Post by shifty2 on 2008-07-26
I don't know about C/C++/Java but for python:

Make sure you have python-mode installed and set up (I don't know how well you know emacs, if you don't know how to do that ask me to clarify). I'm not on ubuntu right now, but I'm pretty sure its included in the default emacs/is available for download from synaptic - search for it.

You can then get an interactive python shell by typing M-x python-shell. Additionally, if you are editing a python document you can execute that by pressing C-c C-c.

You

---

### Post by Ruhe on 2008-07-27
Ok
C and java aren't interpreted languages, so you cannot "talk" to them as you can with python.

Emacs has everything you need for writing C programms.
I guess you installed all development tools by "sudo apt-get install build-essential". So you can write your C programm, write make file, and then type "M-x compile". Or you can start gdb - debugger.

To write&compile&run java programs you have to install jdk (look for how-to's on this forum). Then install [**JDEE**]("http://jdee.sourceforge.net/") about which I wrote in previous post. It's not so easy to connfigure all this stuff, so you'll spent a lot of time, before you run your first applet ;) just read about JDEE and some of your questions will go away. Ant or Maven can save a lot of time. 

And again you cannot interact with C or java because they're compiled languages.

---

### Post by LaRoza on 2008-07-27
> **Ruhe said:**
> Ok
C and java aren't interpreted languages, so you cannot "talk" to them as you can with python.

And again you cannot interact with C or java because they're compiled languages.

They aren't by nature. There is nothing saying they can't be interpreted.
```

~$cat p.c
#!/usr/bin/tcc -run

#include <stdio.h>

int main(void)
{
    puts("Look Virgina! There is an interpreter...");
    return 0;
}
~$chmod +x p.c
~$./p.c
Look Virgina! There is an interpreter...
~$

```

---

