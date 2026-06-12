---
title: "Fortran with lucid lynx"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by Lingadharini on 2012-08-08
Hello Friends,
 I am a newbie to Unix and mine is a dual-boot system with Windows 7 and Ubuntu linux 10.04 ( Lucid Lynx).
 I am really very bored with Windows, so I thought of giving lucid lynx a try.
 I am now trying to learn Fortran all by myself.
 I have got tutorials from the internet. 
 Which is best to try - Fortran 77 or Fortran 95 ?
 Also tell me how and what to install to run a Fortran program in my lucid and how to run - the commands..?
 Thanks in advance.
 Please do help me..I am really desperate and frustrated 'coz I didnt know anything....

---

### Post by MG&amp;TL on 2012-08-08
Fortran is not a good place to start, neither is lucid. You'd be better off with precise (if you can't run Unity, use Lubuntu/Xubuntu) and something like python . But if you insist...

```
sudo apt-get install gfortran

```

^^ Install the compiler

> gfortan <file> -o <name>

will compile <file> into an output file <name>

```
path/to/<name>
```

will execute <name> that you just compiled.

---

