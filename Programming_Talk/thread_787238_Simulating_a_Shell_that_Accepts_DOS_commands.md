---
title: "Simulating a Shell that Accepts DOS commands"
date: 2008-05-08
forum: Programming Talk
---

### Post by Yamazaki on 2008-05-08
Hi there, if you could help me with this, i'd be appreciated, i need to simulate a shell that accepts DOS commands (10-15 commands) like "edit-copy-rename-move .. etc" and execute them under linux on terminal, the reason for this, since everyone would just "omg use terminal commands", it's a challenge.

So any help?

Edit: This is not a homework solution request thread, i'm a shell programming beginner, shedding some light on the subject would be appreciated, thanks.

---

### Post by smartbei on 2008-05-08
Sounds like a general scripting programming language challenge. What part are you having trouble with? Have you figured out how you want to accomplish the task?

---

### Post by Yamazaki on 2008-05-08
> **smartbei said:**
> Sounds like a general scripting programming language challenge. What part are you having trouble with? Have you figured out how you want to accomplish the task?
Yes, Creating a single shell that executes DOS commands, like running CMD on windows, but since i'm so noob, i just started reading "Beginning Linux Programming, Fourth Edition" book, i don't know how to create a shell that performs several methods. I think it's not necessary to write these functions, i can refer to linux's, for example when user write "edit" the shell will open any editor, same for remove, i can just refer to rm command or do i have to build the whole functions from scratch?.

---

### Post by smartbei on 2008-05-08
That sounds reasonable. In that case, you would probably want a program that reads from the user a command and its parameters, translates it to the standard shell equivalent, and then executes it.

Where is this challenge from? Are you limited to a certain programming language?

---

### Post by Heinzelotto on 2008-05-08
[http://www.ss64.com/bash/alias.html](http://www.ss64.com/bash/alias.html)

this won't accept parameters from dos commands though (unless the parameters are the same as in the linux version)

another possibility would be scripts named after dos-commands that parse the given arguments and issue the right corresponding linux commands.

---

### Post by Yamazaki on 2008-05-11
> **smartbei said:**
> That sounds reasonable. In that case, you would probably want a program that reads from the user a command and its parameters, translates it to the standard shell equivalent, and then executes it.
Yes exactly.

> Where is this challenge from? Are you limited to a certain programming language?
From a friend, and i can program in C and Shell scripting on linux (More experienced with C). First i thought of switch if user typed edit it should open gedit editor /usr/bin/gedit, else if user typed copy, it should excute cp function, .. etc, but i really don't know how to call the equivalent functions on linux, i mean how to call cp method?.

I also thought of the interface be somthing like that:

./test

Welcome please select the desired command:

-Copy
-Edit
-Delete
...etc 

and once the user type the desired command, the program should execute the function, so i'll be making a function for every command and call it, but again i don't know if i could simply call cp/gedit/rm .. etc functions without making them from scratch or not.

What do you think?

---

### Post by LaRoza on 2008-05-11
How about DOSBox?

---

### Post by Rinzwind on 2008-05-11
Would it not suffice to set some aliases?

Here's a random aliases list from the web:

alias attrib='chmod'
alias chdir='cd'
alias copy='cp'
alias cp='cp -i'
alias d='dir'
alias del='rm'
alias deltree='rm -r'
alias dir='/bin/ls $LS_OPTIONS --format=vertical'
alias edit='pico'
alias ff='whereis'
alias ls='/bin/ls $LS_OPTIONS'
alias mem='top'
alias move='mv'
alias mv='mv -i'
alias pico='pico -w -z'
alias rm='rm -i'
alias search='grep'
alias v='vdir'
alias vdir='/bin/ls $LS_OPTIONS --format=long'
alias which='type -path'
alias wtf='watch -n 1 w -hs'
alias wth='ps -uxa | more'

These are some windows variants:

clr clear
cls clear
copy cp -i
del rm -i
delete rm -i
dir ls -alg
home cd ~
ls ls -F
md mkdir
move mv -i
pwd echo $cwd
type more

---

### Post by Yamazaki on 2008-05-13
> **Rinzwind said:**
> Would it not suffice to set some aliases?

Here's a random aliases list from the web:

alias attrib='chmod'
alias chdir='cd'
alias copy='cp'
alias cp='cp -i'
alias d='dir'
alias del='rm'
alias deltree='rm -r'
alias dir='/bin/ls $LS_OPTIONS --format=vertical'
alias edit='pico'
alias ff='whereis'
alias ls='/bin/ls $LS_OPTIONS'
alias mem='top'
alias move='mv'
alias mv='mv -i'
alias pico='pico -w -z'
alias rm='rm -i'
alias search='grep'
alias v='vdir'
alias vdir='/bin/ls $LS_OPTIONS --format=long'
alias which='type -path'
alias wtf='watch -n 1 w -hs'
alias wth='ps -uxa | more'

These are some windows variants:

clr clear
cls clear
copy cp -i
del rm -i
delete rm -i
dir ls -alg
home cd ~
ls ls -F
md mkdir
move mv -i
pwd echo $cwd
type more
is it possible to execute all these commands from a single script? rather than typing one by one.

---

### Post by LaRoza on 2008-05-13
> **Yamazaki said:**
> is it possible to execute all these commands from a single script? rather than typing one by one.

Put them in your .bashrc

---

### Post by CptPicard on 2008-05-13
Sounds like a great place to apply some Lisp macros... grab SBCL, it gives you a runtime environment "shell" out of the box, then define macros for your shell commands that translate your "shell language" to Lisp forms, and then eval those :)

---

### Post by LaRoza on 2008-05-13
> **CptPicard said:**
> Sounds like a great place to apply some Lisp macros... grab SBCL, it gives you a runtime environment "shell" out of the box, then define macros for your shell commands that translate your "shell language" to Lisp forms, and then eval those :)

You Lisp fans...

---

