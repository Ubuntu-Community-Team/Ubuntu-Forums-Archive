---
title: "Change the color letters and font in c++"
date: 2009-09-17
forum: Programming Talk
---

### Post by DiegoTc on 2009-09-17
Hi everyone
I am having a great doubt
Is there a way that I can change the color letters in c++ in terminal?
I know there is a way in Windows, but not sure if there is one to do it with Ubuntu

And i would like to know if there is a standard way to doing it that will work in windows or linux?

---

### Post by Natr0n on 2009-09-17
The ncurses library is what you're looking for. Open a terminal and type ```
man ncurses
``` to read all about it.

Also, there is a version of ncurses for Windows called PDCurses. I think it's identical to ncurses. Don't quote me on that.

---

### Post by dwhitney67 on 2009-09-17
> **DiegoTc said:**
> Hi everyone
I am having a great doubt
Is there a way that I can change the color letters in c++ in terminal?
I know there is a way in Windows, but not sure if there is one to do it with Ubuntu

And i would like to know if there is a standard way to doing it that will work in windows or linux?

Can you please be more specific?  Are you referring to the text that you view when editing source code?  If so, consider using vim or an IDE (eg. Eclipse, CodeBlocks, gEdit, etc).

P.S.  If you are using vim, you will need to insert the statement "syntax on" (w/o the quotes) in ~/.vimrc.

---

### Post by nvteighen on 2009-09-17
There are two methods.

1) Using low-level terminal manipulation (termios).
2) Using high-level terminal manipulation (ncurses... which is a wrapper around termios)

There's another ncurses-like library whose name I don't remember now... but ncurses is the best-established of all.

---

### Post by DiegoTc on 2009-09-17
> **dwhitney67 said:**
> Can you please be more specific?  Are you referring to the text that you view when editing source code?  If so, consider using vim or an IDE (eg. Eclipse, CodeBlocks, gEdit, etc).

P.S.  If you are using vim, you will need to insert the statement "syntax on" (w/o the quotes) in ~/.vimrc.


I mean when you run the program in terminal
I want that Hello World appears in red color.

But ncurses just works in linux
Is there a method that works multiplataform?

---

### Post by Natr0n on 2009-09-17
> **DiegoTc said:**
> 
But ncurses just works in linux
Is there a method that works multiplataform?

Actually, [PDCurses]("http://pdcurses.sourceforge.net/") works on both platforms.

---

### Post by DiegoTc on 2009-09-17
Okay
SO pdcurses is multiplataform
But how do I install it for using it on Codeblocks?
Searching on google I can only find tutorials but running codeblocks on windows

---

### Post by JordyD on 2009-09-17
> **DiegoTc said:**
> Okay
SO pdcurses is multiplataform
But how do I install it for using it on Codeblocks?
Searching on google I can only find tutorials but running codeblocks on windows

You don't need to install it *for* Code::Blocks. Just install it*, include the header file(s) you need, and link it (if necessary). I'm not aware of the specifics of PDCurses, but they have [documentation]("http://pdcurses.sourceforge.net/doc/index.html").

* To install, just go into the directory you extracted it into, and run:
```
./configure
make
sudo make install
```
in the terminal.

---

### Post by Zugzwang on 2009-09-18
> **DiegoTc said:**
> Okay
SO pdcurses is multiplataform
But how do I install it for using it on Codeblocks?
Searching on google I can only find tutorials but running codeblocks on windows

See [this post]("http://http://ubuntuforums.org/showthread.php?t=1258665"), section 2 for explanations why you cannot find it.

---

### Post by c0mput3r_n3rD on 2009-09-18
It sounds like you're not looking for a library in order to physically change the texts appearance (color style etc.), but to just change the terminal options so that the text is different?  If I am correct then you do it the same way as you would in winblows; go to the properties of the termimal and change the font color.  Other wise ncurses is what you're looking for.

---

