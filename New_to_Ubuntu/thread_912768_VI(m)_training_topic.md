---
title: "VI(m) training topic"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by eentonig on 2008-09-07
**_Prologue_**

although CLI usage is becoming less and less a requirement in GNU/linux, there are some times where ones become confined to the tools that exist CLI based only (recovery mode, servers, X crashed, ...). The one skill that any user should master in those circumstances, is text editing. 
Virtually every linux distribution I know off, comes with a text manipulation program, called [COLOR="Sienna"]'vi'[/COLOR] or [COLOR="Sienna"]'vim'[/COLOR]. 

Vi(m) can be a pain to learn in the beginning, but ones you learn it's usage, I personally learned to prefer it  over GUI based editors. so I decided to start a series of short, task based, trainingsessions to guide the novices in the fine art of practical and efficient text manipulation.

**_CLASS INTRO_**

The minimal requirements to follow the lessons are as follow:
- Know how to open a terminal.
- know how to start/exit vi(m)

Every lesson will 
- start with a short explanation on a or some concepts. Very brief, the main goal is to point the student in the right direction to find what he needs.
- A few tasks to complete. Students are encouraged to complete these and post the outcome, and more importantly! Explain how they achieved it.
- (Discussion: Additional Questions to answer.)

**_Lesson 1. Basics and setting up a usefull environment to work with_**

After opening vi for the first time, most people are frustrated they can't enter any text (I know I was). That's because vi uses two distinct modes for working on a text file. command mode, the default when you open vim, and insert mode, which allows you to type text. We'll go deeper into both of these later on. For now, let's focus on making vim a nice(r) environment to work in.

Most current distributions don't install vi anymore, but provide it's successor vim (VI Improved). For old time sake, and possibly some other good reasons as well, they not only make sure that when you start vi, it actually points you to vim, but they also start vim in the old fashion vi compatibly mode. Which is, honestly, a bit limiting.

**Task 1.** Open the global vim configuration (yes, you have to find it yourself) and read through it. Do not edit anything here.

**Task 2.** (And the last time you're allowed to finish your homework in any editor you prefer.). Create a personal configuration file.
$HOME/.vimrc and activate the options you think you'll like or use. But at a very minimum, you're vim should behave
- to give you syntax highlighting, so you don't have to stare a a boring chunk of text.
- to enable mouse usage (although we'll do our best to use it as less as possible)
- Have command line completion <Tab> (filenames, help topics, ...)
- display the current mode and partially-typed command in status bar.
- enable spell checking for you're language
**Task 3** If you hate CLI environments, install gvim. This will give you the benefit of being able to run a GUI version of vim. But also that you can partially use the menus as a cheat sheet for command sequences.



**Discussion: **

Give me some pointers what usage you have most for vi, so I get an idea in which direction I need to focus later on.

---

### Post by meborc on 2008-09-07
nice... i always wanted to learn vi... but since nano is soooo easy i have kind of forgot about it :)

i need to connect to my university's cluster from time to time and change my input files for automatic calculations... and on the university's server there is only emacs and vi available... so i would very much be interested in pointers on how to modify files... delete whole rows of text, save, move around in file etc...

---

### Post by rye_ on 2008-09-08
I'm also looking into vi (for rails development).  I appreciate any tips you're able to give.

Cheers,

Ryan

---

