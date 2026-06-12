---
title: "Playing with the Terminal... Desktop?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by projecthikari on 2008-07-17
ROAR!!!

I must be doing something wrong. All I want to do is get into my "Stuff" Folder on my desktop...

But I cant seem to GET TO the desktop from my terminal. And, after mounds of fooling around, I'm still not getting anywhere.
A little help?

...I guess the picture is unneeded, but I think my reaction to the situation at the bottom was funny.:lolflag:

---

### Post by silverglade00 on 2008-07-17
Linux and other Unix-like operating systems are case-sensitive. You can even make a Mac case-sensitive. 

You need to cd Desktop instead of cd desktop.

---

### Post by projecthikari on 2008-07-17
> **silverglade00 said:**
> It's case-sensitive. You need to cd Desktop instead of cd desktop.

REALLY?!

...Duh. T_T

Whoo!~ I'm movin' up in the world! *is in her stuff folder.*

---

### Post by eriqjaffe on 2008-07-17
You can also use ~ as a shortcut to your home folder:

```
cd ~/Desktop
```

will get you to your Desktop no matter where you are.

---

### Post by Zalbor on 2008-07-17
And also, don't forget spaces! "cd" is a command, you have to put a space after it and before anything else.

---

### Post by lukjad on 2008-07-17
The same thing happened to me. Since I switched to Ubuntu/Linux it has always been drummed into me that Linux is CaSe SeNsItIvE. And the case is always lower case. The first time I tried to go to the Desktop, I learnt this important rule. Linux Devs like to make jokes and break there own rules. (Or at least that's what I was told.)

---

### Post by markjensen on 2008-07-17
> **silverglade00 said:**
> Linux and other Unix-like operating systems are case-sensitive. You can even make a Mac case-sensitive. 

You need to cd Desktop instead of cd desktop.

With projecthikari's problem solved (case sensitivity), it might be interesting to point out that Windows is a POSIX-compliant OS, and can be set case sensitive too.  At least to some extent.   I use MS SFU (Services for Unix) on most every Windows box I am on, so I can use grep, sed and other useful commandline tools.   But it is trivial to **touch Hello.txt** in a directory where "hello.txt" exists and you have two separate files.  And normal browsing through Explorer or such will only ever open the one, regardless of which file you double-click.

---

