---
title: "How do I program in Emacs, Vim"
date: 2005-07-28
forum: Programming Talk
---

### Post by coolblue on 2005-07-28
I cant seem to understand any of the Emacs/Vim tutorials out there!
I'm a newbie and want to start programming in Vim/Emacs.

Now I typed some code in Vim/Emacs...now how do I compile it?
And I hope I can save my codes, right?

Can anyone knowing any one of these editors give me tips etc. from their own experience?

On how to program in Vim/Emacs?

Thanks....I'm a TOTAL newbie to Emacs/Vim:)

---

### Post by dcraven on 2005-07-28
[QUOTE=coolblue]I cant seem to understand any of the Emacs/Vim tutorials out there!
I'm a newbie and want to start programming in Vim/Emacs.

Now I typed some code in Vim/Emacs...now how do I compile it?
And I hope I can save my codes, right?

Can anyone knowing any one of these editors give me tips etc. from their own experience?

On how to program in Vim/Emacs?

Thanks....I'm a TOTAL newbie to Emacs/Vim:)[/QUOTE]

First of all, Vim and Emacs are very different editors. Narrowing down which one you are actually talking about would be a good start (I'm a heavy Vim user myself). Secondly, understand that these are editors, not compilers. There does exist, however, some extensions or scripts that make compiling easier or more "integrated". Thirdly, what language are you writing in? This bit of information would make explaining compilation methods a little simpler.

Cheers,
~djc

---

### Post by thumper on 2005-07-28
I use emacs every day at work for editing source, but still use the command line for compilation (well most of it).

There is Meta-X compile, sometimes bound to C-c C-c depending on your mode.

You can find out if a given command is bound to a key press by asking for help on a function:
   C-h f  (Ctrl H is help, try Ctrl-H ?, very useful) compile

The compile emacs function asks for a command line to run.  Instead of it always asking what to do you can bind the parameters like this (put it in your .emacs file):

```

(global-set-key [(control f7)] (lambda () (interactive) (compile "make")))

```

---

### Post by charlieg on 2005-07-28
Gentoo vi & vim tutorial:
[http://www.gentoo.org/doc/en/vi-guide.xml](http://www.gentoo.org/doc/en/vi-guide.xml)

Best beginners tutorial I know of.

Get comfy with :help in vim and you're golden.

And using ! you can launch shell comands...

!make

Mmm.  Vimminess.

---

### Post by jerome bettis on 2005-07-28
this is what got me started on vim:  [http://heather.cs.ucdavis.edu/~matloff/UnixAndC/Editors/ViIntro.html](http://heather.cs.ucdavis.edu/~matloff/UnixAndC/Editors/ViIntro.html)

once you've gone through that there's a link at the bottom with more vim stuff.  i'm using this as my .vimrc and it's really nice:  [http://newbiedoc.sourceforge.net/tutorials/vim/appendixa.html.en](http://newbiedoc.sourceforge.net/tutorials/vim/appendixa.html.en)

---

### Post by coolblue on 2005-07-29
[QUOTE=dcraven]First of all, Vim and Emacs are very different editors. Narrowing down which one you are actually talking about would be a good start (I'm a heavy Vim user myself). Secondly, understand that these are editors, not compilers. There does exist, however, some extensions or scripts that make compiling easier or more "integrated". Thirdly, what language are you writing in? This bit of information would make explaining compilation methods a little simpler.

Cheers,
~djc[/QUOTE]
 
I wanna program in C/C++ and perl, (and maybe java but not now).

---

### Post by dcraven on 2005-07-29
[QUOTE=coolblue]I wanna program in C/C++ and perl, (and maybe java but not now).[/QUOTE]

Well, if using C/C++, I'd suggest looking into and learning how to write simple makefiles. This is certainly not necessary, but can make life simpler in the long run. Especially if/when your project gets large. Speaking strictly from a Vim perspective, if you have a Makefile for your program, you can typically just type ":make" in Vim and it will compile the program using "Quickfix" (see :help quickfix in vim). The program will be compiled, and if errors occur, Vim will place the cursor on the line where the first error (or warning) occured. The commands :cn and :cp will take you to the next and previous errors respectively.

As for Perl programming, there is no need to compile. Just make your script executable by typing "chmod 755 myscript.pl" in a terminal (replacing myscript with your script's name obviously) and you can then run it like any other file.

Enjoy!
~djc

---

