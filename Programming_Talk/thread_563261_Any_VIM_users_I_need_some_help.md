---
title: "Any VIM users? I need some help"
date: 2007-09-29
forum: Programming Talk
---

### Post by iiieckiii on 2007-09-29
Hello all the I am the newest resident uber-noob here and I have just installed VIM on Feisty or at least I guess I did (when I type vim in terminal it takes me to VIM) so I'm guessing I've done this correctly. It states version 7.0.235 and I wanted to know how to use this for C programming. I chose VIM because while I was doing research online people have pointed toward VIM as the more popular choice over emac's. Anyways I've tried doing research on my own but there hasn't been any information for people that are uber noobs like myself. Few questions are, how to start once I reached VIM? and how to save what I've done in VIM, how do I compile things with gcc, any super basic information will help me out. Please help an utterly helpless noob so one day I can grow and become uber :KS. 

P.S when I say I'm an uber-noob I really mean it I don't know crap, I don't even know the basic of the basics, I kind of need my hand held for a bit. Sorry guys and gals... and thanks for those that help.

---

### Post by Celegorm on 2007-09-29
VIM is a great text editor, but it has a high learning curve, so you will have to be patient with it until you've had time to develop a bit of proficiency. There's an interactive tutorial for vim called vimtutor which is probably the best thing to start with. I'm not sure which package it's in, but if you type 'vimtutor' in the command line and don't have it installed, it should tell you which package to get. There are also a lot of websites with vi tutorials, and you might even find a book on using vi at your local bookstore (I've got a nice vi pocket reference book that only cost me $10). As far as using vim for C programming, there are some useful settings for color coding and auto indenting. To turn these on, use ':syntax on' and ':set ai', respectively. If you want to use these every time you run vim, make a file called .vimrc in your home directory and put those two commands in it, separated by a newline. For compilation, 'gcc filename.c' will compile a file and make a binary called a.out. To run it, type './a.out' To name the output file something other than a.out, use the -o option. For example, 'gcc -o filename.o filename.c' will make a binary file called filename.o

---

### Post by dwhitney67 on 2007-09-29
In today's World, VIM is probably not for newbies.  In the old days, its predecessor, vi, was pretty much the "in" thing to use to edit scripts and other source code.  I for one use VIM.

I would first recommend that you get the "full" VIM, since Ubuntu is lame in shipping only the minimal version.  Thus for starters,

[FONT="Courier New"]$ sudo apt-get install vim-full[/FONT]

I cannot recall if that package also provides gVIM (the graphical interface for VIM), so you might need an additional install to get that.

Otherwise, for VIM, you can launch it from the command line such as:

[FONT="Courier New"]$ vi someFileName.c[/FONT]

Basic commands are:

[FONT="Courier New"]i - enter insert mode
a - append/enter insert mode
esc - exit insert mode
k - move the cursor up one line
j - move the cursor down one line
h - move the cursor to the left
l - move the cursor to the right
x - delete a character
dd - delete a line
o - create empty line below an existing one and enter insert mode
u - undo previous command(s)
:q! - exit VIM without saving
:w - save/write file
:wq - save/write current file and exit VIM[/FONT]

There are tons of other commands and command-combinations.  For more details:

[FONT="Courier New"]$ man vim[/FONT]

To compile C programs, you have a choice:  use the command line for simple tasks or create a Makefile.  If you choose to create a Makefile, then you can "call it" from gVIM or invoke it from the command line.  Creating a Makefile is a topic in itself.

To compile a simple C program from the command line:

[FONT="Courier New"]$ gcc someFileName.c -o nameOfExecutable[/FONT]

To run the program:

[FONT="Courier New"]$ ./nameOfExecutable[/FONT]

I recommend that you acquire "Kernigan and Ritchies" C Programming guide, and look for other references on VIM and Makefiles.  I've been writing software for over 20 years and using Unix/Linux for almost 19 years.  I still do not know the full complement of commands that are available with VIM, nor all of the "tricks" needed to build/design Makefiles.  Yet I am sufficiently proficient.

If you require specific help on something, feel free to ask.

---

### Post by duff on 2007-09-29
I learned vi with this guide: [http://www.google.com/search?hl=en&q=filetype%3Apdf+vi+quick+reference](http://www.google.com/search?hl=en&q=filetype%3Apdf+vi+quick+reference)

Print it out and keep it with you.

---

### Post by kknd on 2007-09-29
You can use the pre-made scripts from other users. In the gvim official site, there is a lot of plugins, that does snippets and code completion. Very good!

---

### Post by iiieckiii on 2007-09-29
OMG! Thank you guys SOOO MUCH! You have no idea how much you guys have helped me already. Other forums I've been to people don't respond or answer with totally irrelevant answers or tell me that I'm a noob and go learn something else. You guys are very helpful and nice to not shun a noob :cool:

---

### Post by Natr0n on 2007-09-30
You can also download The Vim Book (or is it just Vim Book?) by Steve Oualline as a pdf [[COLOR="Blue"]here[/COLOR]]("http://www.vim.org/docs.php"). (Look for a link  about half way down the page that says "as a pdf".)

---

### Post by orlox on 2007-09-30
I believe the easiest way to get started is vimtutor. Just type on console:

pablo@PCPABLO:~$ vimtutor

And vim will open with the tutorial file. Just do everything it says and when you're done, you should at least have enough knowledge on using vim for text editing (I believe it's essential to first understand how to edit files with vim before trying to use it to program specifically in C).

---

