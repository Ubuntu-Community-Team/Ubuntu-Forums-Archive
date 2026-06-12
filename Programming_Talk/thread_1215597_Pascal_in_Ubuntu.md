---
title: "Pascal in Ubuntu"
date: 2009-07-17
forum: Programming Talk
---

### Post by SKYDOS on 2009-07-17
Hello!
I need Pascal compiler and IDE (like NetBeans), but I DONT need Lazarus
Is there something like NetBeans?

:popcorn:

---

### Post by jonobr on 2009-07-17
Recommend you move this to the programming section,
the guys over there are genius's and :guitar: rock

---

### Post by prshah on 2009-07-17
> **SKYDOS said:**
> I need Pascal compiler and IDE (like NetBeans), but I DONT need Lazarus Is there something like NetBeans?

Don't know about an IDE but you can always```
sudo apt-get install pascal-compiler
```

---

### Post by zolookas on 2009-07-17
You can use [fpc]("apt://fpc") and [fp-ide]("apt://fp-ide") packages, but provided IDE is curses based and looks like Borland's Turbo Pascal.

Here's screenshot i have found:[U]
[[IMG]http://img25.imageshack.us/img25/5568/compiler1.th.jpg[/IMG]]("http://img25.imageshack.us/i/compiler1.jpg/")[/U]

---

### Post by SKYDOS on 2009-07-17
> **zolookas said:**
> You can use [fpc]("apt://fpc") and [fp-ide]("apt://fp-ide") packages, but provided IDE is curses based and looks like Borland's Turbo Pascal.

Here's screenshot i have found:[U]
[[IMG]http://img25.imageshack.us/img25/5568/compiler1.th.jpg[/IMG]]("http://img25.imageshack.us/i/compiler1.jpg/")[/U]

COOL! I have installed it, but I dont know how to run the IDE ((( help pls!

---

### Post by SKYDOS on 2009-07-17
> **zolookas said:**
> You can use [fpc]("apt://fpc") and [fp-ide]("apt://fp-ide") packages, but provided IDE is curses based and looks like Borland's Turbo Pascal.

Here's screenshot i have found:[U]
[[IMG]http://img25.imageshack.us/img25/5568/compiler1.th.jpg[/IMG]]("http://img25.imageshack.us/i/compiler1.jpg/")[/U]

Look pls on attached screens... i have some errors((

---

### Post by zolookas on 2009-07-17
I no longer write anything in pascal, but I will try to help.

If your mouse and copy and paste works inside IDE, that bug does not affect you.

Try installing [build-essential]("apt://build-essential") package as you may have some development libraries missing.
Also try saving your hello world application to a text file (eg. hello.pas) and use fpc to compile it
```
fpc hello.pas
```and see if it fails.

It's late here, I have to go.

---

### Post by SKYDOS on 2009-07-17
> **zolookas said:**
> I no longer write anything in pascal, but I will try to help.

If your mouse and copy and paste works inside IDE, that bug does not affect you.

Try installing [build-essential]("apt://build-essential") package as you may have some development libraries missing.
Also try saving your hello world application to a text file (eg. hello.pas) and use fpc to compile it
```
fpc hello.pas
```and see if it fails.

It's late here, I have to go.

It works! but how can i run this program?

---

### Post by jespdj on 2009-07-17
Try typing in:
```
./hello
```
in the terminal when you're in the directory that contains the executable.

Wow! Flashback to Turbo Pascal, which I was playing with in 1991 or 1992 on my 20 MHz 386SX with 1 MB RAM.

---

### Post by unknownPoster on 2009-07-17
> **jespdj said:**
> 

Wow! Flashback to Turbo Pascal, which I was playing with in 1991 or 1992 on my 20 MHz 386SX with 1 MB RAM.

For some reason, they were teaching it at my highschool back around 2004. It brings back memories, I'm tempted to go play around with it just for fun. :P

---

### Post by SKYDOS on 2009-07-18
> **jespdj said:**
> Try typing in:
```
./hello
```in the terminal when you're in the directory that contains the executable.

Wow! Flashback to Turbo Pascal, which I was playing with in 1991 or 1992 on my 20 MHz 386SX with 1 MB RAM.

It worked! Thanks! but I dont understand why the IDE is not working... ((
It's quite uncomfortable to work with console.

---

### Post by The Cog on 2009-07-18
Try geany. It's a lightweight editor/ide. It's in the repositories.

---

### Post by hessiess on 2009-07-18
> **SKYDOS said:**
> It's quite uncomfortable to work with console.

After learning how to use the command line, you wouldn't say that ;)

You don't need an IDE, almost all of the text editors on Linux have syntax hi lighting for almost everything, and are highly scriptable.

IDE's are bloatwere and overcomplicate everything (IMO).

---

### Post by SKYDOS on 2009-07-19
> **The Cog said:**
> Try geany. It's a lightweight editor/ide. It's in the repositories.

I am going to try it) :D

---

### Post by SKYDOS on 2009-07-19
> **hessiess said:**
> After learning how to use the command line, you wouldn't say that ;)

You don't need an IDE, almost all of the text editors on Linux have syntax hi lighting for almost everything, and are highly scriptable.

IDE's are bloatwere and overcomplicate everything (IMO).

I like console)) but I dont like to edit files, I mean pas files each time i need to correct some errors... it's not so comfortable. but for me console looks much more beautiful now)

Thank you guys :popcorn:

---

