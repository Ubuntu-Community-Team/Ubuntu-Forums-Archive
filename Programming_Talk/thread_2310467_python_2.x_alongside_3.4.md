---
title: "python 2.x alongside 3.4"
date: 2016-01-19
forum: Programming Talk
---

### Post by pasi-nummi on 2016-01-19
Hi,

I'm using Ubuntu 14.04 with python 3.4. For some projects (and their modules) I need also python 2.6-7. Is it possible to have them both side-by-side (preferably with individual launcher icons)?
i've spent hours trying to find info, but nothing seems to work. Command-line start for py2 would also be cool, but I just can't get py2...I also tried to install VirtualBox with Linux Mint and use py2 from there, but my laptop won't allow virtual machines. 
I'm pretty noob, but I'm not afraid of terminal. Any help or pointers to right direction will be appreciated.

Thank Yous in advance!

---

### Post by oldfred on 2016-01-19
How are you using python 3.4?
Ubuntu runs on the internal python 2 version which must be the default. 
Depending on version of Ubuntu you probably have 2.7 which should run any python2 code.

Post this:
  ls -l /usr/bin/python

  ls -l /usr/bin/python3

And if writing python code:

 sheban to specify if default not desired:
#!/usr/bin/env python3 


 Ubuntu 16.04 LTS Will Try To Be Python-3-Only, No Python 2 By Default
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-16.04-Python-3-Hopes](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-16.04-Python-3-Hopes)
Although they also said that back with 12.10, but could not update all the applications to work correctly or internally specify to use python2.

---

### Post by pasi-nummi on 2016-01-19
Yeah, Ubuntu runs on py2.7, but I need to do some programming with it also and I can't open it's IDE or shell since I installed py3.4. My friend's Raspberry Pi (with Raspbian) has IDEs for 2.7 and 3.4 by default. That's something I need...I'm learning py3 and want to keep that also. Dual-booting option for py2 and 3 would be sweet. Maybe different IDE would do the trick?

---

### Post by steeldriver on 2016-01-19
How exactly did you install python 3.4? You didn't need to do that - and, depending how you did it, you may have broken the default python2 installation

---

### Post by oldfred on 2016-01-19
I have used Geany, but it defaults to python2, you have to go into its configuration settings and change its default to python3.
Not sure about other IDE.
Some just use the text editor and correct shebang for version they are using.

---

### Post by pasi-nummi on 2016-01-20
> **steeldriver said:**
> How exactly did you install python 3.4? You didn't need to do that - and, depending how you did it, you may have broken the default python2 installation

I used apt-get install. Did I do permanent damage?

---

### Post by pasi-nummi on 2016-01-20
Yes!!! I downloaded an IDE (PyCharm5) and now I can use py2 & py3. Of course standard IDLE(using Python-3.4) don't get py2. Silly old me...

Big thank Yous to Oldfred and Steeldriver for help!!!

---

### Post by Rick_Astley on 2016-01-20
I was using Sublime Text 2 for a couple of months but got tired of the nag screen to buy it (not paying that much money for an editor), I then found Atom about two weeks ago and I love it!  My 9 year old son likes to do his Python programming on Geany, he's in love with pressing F5 to run his programs.

---

