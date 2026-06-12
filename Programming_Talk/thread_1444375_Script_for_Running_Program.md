---
title: "Script for Running Program"
date: 2010-04-01
forum: Programming Talk
---

### Post by KdotJ on 2010-04-01
Hey people, I'm sorry to double post this thread but the Packaging & Compiling forum was maybe the wrong place to put this and is a bit dead there.

Here is my question:

Say for example that I have a program named "testprog" and its written and compiled in java. It there a way that I can write a script and add to my /usr/local/bin directory that will allow me to run the "testprog" program simply by opening a terminal and typing "testprog"?

Thanks in advance for any help

---

### Post by geirha on 2010-04-01
```
sudo install -o root -g root -m 0755 ./testprog /usr/local/bin
```

---

### Post by KdotJ on 2010-04-01
Thanks for the reply,
but what does that command actually do?
The part that says "./testprog" , that wouldnt work for my java program right as you cant run a java program like this right?

I have got something to work but I'm quite sure its not the correct way at all:

```

#!bin/bash

cd projects/testprogram
java testprog


```

This saved as an executable file and added to my /usr/local/bin

---

### Post by cubeist on 2010-04-01
> **KdotJ said:**
> Thanks for the reply,
but what does that command actually do?
The part that says "./testprog" , that wouldnt work for my java program right as you cant run a java program like this right?

I have got something to work but I'm quite sure its not the correct way at all:

```

#!bin/bash

cd projects/testprogram
java testprog


```

This saved as an executable file and added to my /usr/local/bin

sure, that way works. Geirha was offering a solution to install the actual program in /usr/local/bin with permissions set.  You can also cp a program into /usr/local/bin and then adjust the permissions; or you could run your program from user-space... ie, non-root.

---

### Post by moetunes on 2010-04-01
I would just make a folder called bin in your home directory. Bash profile is set to include it if it exists.
In terminal type   $PATH   to check. :)

---

### Post by cubeist on 2010-04-01
the way I actually do it is keep the program in my projects folder then make an link to the project in my /usr/local/bin

this way I can continue to edit the program from user-space.

to make links, the command is
```
cd /usr/local/bin
sudo ln -s /path/to/program
```

---

### Post by KdotJ on 2010-04-01
Great help guys thanks a lot :D
I do infact have a bin directory in my home directory already, but my aim was to put the program in a place accessible to all users, hence me going for /usr/local/bin

thanks again!

---

