---
title: "kernel update how to ??"
date: 2006-01-20
forum: Repositories &amp; Backports
---

### Post by breezyfox on 2006-01-20
hI Guys
I am new to forum and recectly installed server on my old box without GUI.
When i update and upgrade from apt. it updates what ever programmes i installed, works fine.
But always says two packages held back not upgraded.
linux-image -386
linux-restricted -modules -386.

I probably feel iam still running old linux version and wants to updtae it to new one which i saw at furum as [COLOR="DeepSkyBlue"]"latest stable breezy kernel is 2.6.12-10"[/COLOR].

Any help in this regard is appreciated.

bf

---

### Post by essexman on 2006-01-20
[quote=breezyfox]hI Guys
I am new to forum and recectly installed server on my old box without GUI.
When i update and upgrade from apt. it updates what ever programmes i installed, works fine.
But always says two packages held back not upgraded.
linux-image -386
linux-restricted -modules -386.

I probably feel iam still running old linux version and wants to updtae it to new one which i saw at furum as [COLOR=DeepSkyBlue]"latest stable breezy kernel is 2.6.12-10"[/COLOR].

Any help in this regard is appreciated.

bf[/quote]

Hi Breezyfox

I see this is your second posting on this subject.  The first was on the main [breezy forum]("http://www.ubuntuforums.org/forumdisplay.php?f=90") which was probably the right place and I recommend trying their again, but you will have to give more detail to get help.  First try reading through the [guidlines]("http://www.ubuntuforums.org/faq.php") which I found very useful. Also explain more what set up you have, basic hardware, and Ubuntu version;  key in ```
uname -r 
```at the command line and put the out put in your post.  Also say what command you are using, what you are trying to do, and what steps you have taken (such as listing the repositories you are using).

Best of luck.

---

### Post by breezyfox on 2006-01-20
Hi thanks for quick reply.
the out put is :
2.6.12-9-386

1. i have default repository in my sources and all are commented out except cd
2. i did sudo apt-get update and then upgrade.
3. i have installed apache2 and that was upgraded (lib files)
4. while upgrading it say two packages held back and thos e are linux images as mentioned in my above post.
5. it is old box dell.pentium 2,256 ram,broadband every things works fine.

any solution please amy be i need some other repository.

bf

---

