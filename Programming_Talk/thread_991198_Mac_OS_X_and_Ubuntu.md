---
title: "Mac OS X and Ubuntu"
date: 2008-11-23
forum: Programming Talk
---

### Post by Mbengi Bongi on 2008-11-23
I dual boot Mac OS X 10.4 with Ubuntu 8.04 on my iMac - is there any difference between the Terminals on the 2 OSes?

i.e. If I wrote a shellscript in Ubuntu could I run it on the Mac Terminal.app?

I use BaSH in both cases.

---

### Post by gnusci on 2008-11-23
I think it should work without problems, as far is only bash script code. I do have the two system, I still didnt see any problem... Anyway Terminal is running also **bash**.

---

### Post by jimi_hendrix on 2008-11-23
i think there are difference but they are minute...but enough for there to be 2 guide if you google bash commands...

---

### Post by Mbengi Bongi on 2008-11-23
Thanks for the replies guys,

I have noticed some problems particularly with ANSI escape codes, I was just wondering if anyone else had experienced the same.

---

### Post by snova on 2008-11-23
A terminal is a terminal, for one thing. If there are differences, they have nothing to do with the terminal program itself. It's just a display.

Any differences are consequences of the environment, and any modifications Apple makes to Bash. Obviously a Mac OS X environment is different from an Ubuntu one, but they are both Unix systems at their heart, and that will help.

(Note that I have never used a Mac.)

---

### Post by Kilon on 2008-11-23
> **Mbengi Bongi said:**
> I dual boot Mac OS X 10.4 with Ubuntu 8.04 on my iMac - is there any difference between the Terminals on the 2 OSes?

i.e. If I wrote a shellscript in Ubuntu could I run it on the Mac Terminal.app?

I use BaSH in both cases.

There are some commands missing from MacOsX , if i remember correctly , "make" command is not there you have to install it yourself.

look here

[http://www.ss64.com/osx/](http://www.ss64.com/osx/)

---

### Post by escapee on 2008-11-23
> **Kilon said:**
> There are some commands missing from MacOsX , if i remember correctly , "make" command is not there you have to install it yourself.

look here

[http://www.ss64.com/osx/](http://www.ss64.com/osx/)

make gets installed with the Developer Tools, not recommended to install from source.


Virtually anything you'll use is identical, if something is different it won't be much of a tweak.

---

### Post by Paul Miller on 2008-11-24
OS X 10.5 has bash as its default shell; versions before that use tcsh as the default shell.

---

### Post by wmcbrine on 2008-11-25
> **Paul Miller said:**
> OS X 10.5 has bash as its default shell; versions before that use tcsh as the default shell.I'm not sure when the change was, but it wasn't in 10.5. 10.4 also uses bash.

Edit: It looks like 10.3 was the first to default to bash. (Of course, if you upgraded from 10.2 or earlier, your old account's default wouldn't be changed.)

---

### Post by Mbengi Bongi on 2008-11-25
Yep, It's definitely Bash I'm using.

---

### Post by mssever on 2008-11-25
Some commands have different options. MacOS is derived from BSD, which doesn't use GNU tools. GNU tools--which are used in Linux--have a number of extensions beyond the POSIX standard.

---

### Post by Mbengi Bongi on 2008-12-01
I had a feeling that was the case.

---

