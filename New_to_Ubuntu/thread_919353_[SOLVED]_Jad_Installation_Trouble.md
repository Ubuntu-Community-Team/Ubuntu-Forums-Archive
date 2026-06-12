---
title: "[SOLVED] Jad Installation Trouble"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by pickles46 on 2008-09-13
I have recently attempt to install jad. [http://www.kpdus.com/jad.html]("Jad"). (java class file decompiler)

And I don't quite understand the readme, I know I'm most likely doing something stupid wrong.

```
1. Installation.



Unzip jad.zip file into any appropriate directory on your hard drive.

This will create two files:



    - an executable file named 'jad.exe' (Windows *)

      or 'jad' (*n*x)



    - this README file



No other setup is required.
```

So I enter "'jad' (*n*x)" into the terminal and the result is "bash: syntax error near unexpected token `*n*x'"

Can anyone point out what I'm doing wrong?

I'm fairly familiar with linux but I've never used that command before.

(I've checked google and used other methods of installation but they all failed miserably)

---

### Post by phidia on 2008-09-13
Can you enter "cd" into the directory where you unpacked jad and type "ls" (without the quote marks)? Post that output here.
Actually though it looks like bash doesn't like the "(" & ")" symbols.

---

### Post by pickles46 on 2008-09-13
> **phidia said:**
> Can you enter "cd" into the directory where you unpacked jad and type "ls" (without the quote marks)? Post that output here.
Actually though it looks like bash doesn't like the "(" & ")" symbols.

paul@lol-awesome:~$ cd ~/Desktop/jad
paul@lol-awesome:~/Desktop/jad$ ls
jad

I have work tomorrow and it's getting late, I'll be home to check it later on. Thanks for the help, it's greatly appreciated.

---

### Post by Gannon8 on 2008-09-13
Just type ./jad from the directory.
You are interpreting the readme a bit to literally

---

### Post by jamesstansell on 2008-09-14
> **Gannon8 said:**
> Just type ./jad from the directory.
You are interpreting the readme a bit to literally

In other words, the "(*n*x)" comment means the command is intended for "unix-like" systems.

---

