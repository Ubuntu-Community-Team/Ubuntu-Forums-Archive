---
title: "calling programs from different directoris"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by KylePhys on 2012-11-08
I have a file which is basically a data in some directory .../x/y  and a program in a directory ../x which can take this file as an argument and plot the graph, I was wondering is there a way while remaining in the directory "y" be able to call a program in the directory "x" without typing its whole path like ~/...../x, ( a clever command to call something from one or two directories above)?

Thanks.

---

### Post by steeldriver on 2012-11-08
You can use '..' as a shorthand for the parent dir within a relative path 

```
../prog
```to run a program in the immediate parent dir

```
../../prog
```to run a program located 2 dirs above your current dir

---

### Post by drmrgd on 2012-11-08
Also to add, depending on how the program is scripted and what its requirements are, you might be able to create a 'bin' directory in your $HOME folder and run it from there.  Once you create /home/<username>/bin, after you log out and log back in, that directory will become part of your $PATH, which means that you'll be able to execute the program from anywhere, just like other system commands.

---

### Post by KylePhys on 2012-11-08
Thank you!

and what if i have this arrangement 

...d/x -> the directory of the file

...d/y -> directory of the program

How can I call the file while being in the y?  

./prog ../x/filename   doesn't work

---

### Post by Wim Sturkenboom on 2012-11-08
> 
./prog ../x/filename **doesn't work**

Can you be more specific?

---

### Post by KylePhys on 2012-11-08
> **Wim Sturkenboom said:**
> Can you be more specific?

It says "cannot open the file"

---

### Post by steeldriver on 2012-11-08
nevermind - misread

---

### Post by PinkFloyd102489 on 2012-11-08
Quick cheat sheet:

. - current directory (ex: ./run.sh)
.. - Directory above current (ex: ../run.sh)
~ = Home directory (~/run.sh would be /home/USER/run.sh)

You can also use the pwd command in a script to figure out where you're currently at.

---

### Post by drmrgd on 2012-11-08
> **KylePhys said:**
> It says "cannot open the file"

It could very well be that the program (or script - you haven't specified) is coded to be run from the directory where the file resides, and you can't do it on a remote file.  So, in that case you'll have to make sure you always execute the program from the same directory as the file you want to process.  You can still have the executable in a different location it seems (if I understand you correctly), though.  I've seen a lot of scripts like this, that won't accept paths to the files to be processed and just looking the present working directory (PWD) or current working directory (CWD) for the files to process.

---

### Post by KylePhys on 2012-11-08
Thank you guys for all your help.

---

