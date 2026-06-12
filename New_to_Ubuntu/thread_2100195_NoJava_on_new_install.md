---
title: "NoJava on new install"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by Wray on 2013-01-01
Newest version install does not include java ? Net video files will not run. Error message says i need to install java.  Haven't been able to do that yet, need help.  I looked for a faq but didn't see one. really need help, i could mess around with this issue for days, and possibly figure it out, but i am sure somebody here has a quick fix.
Thanks in advance

---

### Post by 2F4U on 2013-01-01
There are a lot of different options available with respect to Java, so you can choose what fits your requirements:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Paqman on 2013-01-01
FWIW, OpenJDK is the easiest to install and seems to work perfectly well for the few things I've asked it to do.

---

### Post by iMac71 on 2013-01-01
open a Terminal window with [CTRL]+{ALT]+[T] and paste in it the following command:```
sudo apt-get install -y openjdk-7-jre icedtea-7-plugin
```then press [ENTER] and type your password.

---

### Post by Pjotr123 on 2013-01-01
This is an easy how-to for Sun (Oracle) Java:
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

Should you prefer a repository for it, then the Duinsoft repository mentioned in the how-to is a good choice: I know the maintainer personally, and he's very quick with issuing new updates (usually within a day after Oracle has issued a new version of Java).

Good luck! :)

---

### Post by Wray on 2013-01-01
:o> **iMac71 said:**
> open a Terminal window with [CTRL]+{ALT]+[T] and paste in it the following command:```
sudo apt-get install -y openjdk-7-jre icedtea-7-plugin
```then press [ENTER] and type your password.

I did that and loaded several pages of code and ended with my terminal prompt, so i assume it finished.
However, no joy still cannot play u-tube files - reports "need flash player"

---

### Post by JiuJitsu500 on 2013-01-01
Java is not flash. They are two very different things that work very well in their own respects. Java has almost nothing to do with YouTube videos, or porn... whatever flash you're really watching. :D

Go to the software center, search for "Ubuntu Restricted Extras" and install the entire package. This includes java/icedtea, flash, various codecs, etc... almost everything you need except for encrypted DVD's.

Ubuntu cannot legally give you all of these in a fresh install, but installing yourself afterward is fine after you verify that you acknowledge the terms and policies and such.

*EDIT: Oh, just so you know, Windows and MAc can't really legally do that either. The manufacturers mostly install all that junk on the computers they sell after the OS in a mega-package deal that mostly sucks. Ubuntu has a lot of bloat too, but java and flash do not belong to them, nor microsoft or apple... but when paid for, computers can ship with java and flash and norton and all the other stuff. Ubuntu is free, and much more powerful, like a boss.

---

### Post by Wray on 2013-01-01
I am aware that java is not flash; i thought it may have been loaded with the java package.
i do mostly music videos, if a bewbie happens to show up occasionally, well what can you do!:D:D

I have tried several times to load flash with no success.  Thanks for your suggestions, i'll give it a shot.  For what it is worth i  almost certainly a, newbie but i am also a retired electrical engineer, so i may not be completely clueless, even if appearences occasionally indicate otherwise

---

### Post by iMac71 on 2013-01-01
The easiest way to play flash videos is to install ubuntu restricted extras:```
sudo apt-get install -y ubuntu-restricted-extras
```During the installation process you'll be asked if you want to install the Microsoft Truetype fonts by accepting or rejecting the Microsoft EULA; the positive or negative answer to that question doesn't affect at all the installation of the flash plugin.

---

### Post by JiuJitsu500 on 2013-01-01
I wasn't hating on you wray, I was just putting that out there :)

Some people don't really get why you can't watch flash and do other basic things at times from a fresh install of a FREE OS when compared to that new Mac or Toshiba they got with Windows 8.

Well, duh... you paid for it, which means paying for the hardware, OS, and proprietary software from the vendor, manufacturer, and anyone else who has their hand in getting that computer to you!!! LOL Still, glad you decided to come to the light side of the force here, been on ubuntu specifically for quite some time and haven't looked back unless I want to play battlefield 3 or something like that...

Restricted extras should solve your problems though. As for excrypted DVD's though, just google that. I think as of 12.10, you don't need to add a ppa, just a small library package if I'm not mistaken. but I'm on 12.04 still and need to update my junk :)

---

### Post by Wray on 2013-01-01
> **JiuJitsu500 said:**
> I wasn't hating on you wray, I was just putting that out there :)

Some people don't really get why you can't watch flash and do other basic things at times from a fresh install of a FREE OS when compared to that new Mac or Toshiba they got with Windows 8.


Well, duh... you paid for it, which means paying for the hardware, OS, and proprietary software from the vendor, manufacturer, and anyone else who has their hand in getting that computer to you!!! LOL Still, glad you decided to come to the light side of the force here, been on ubuntu specifically for quite some time and haven't looked back unless I want to play battlefield 3 or something like that...

Restricted extras should solve your problems though. As for excrypted DVD's though, just google that. I think as of 12.10, you don't need to add a ppa, just a small library package if I'm not mistaken. but I'm on 12.04 still and need to update my junk :)
No offense taken. I Installed extras from command line, now am a happy camper.
I have been almost exclusively running ubuntu linux for about two years now and only use windoz for Photoshop, and even there I am slowely moving over to Gimp.  I just don't **** around with software too much, ie.  i'm an old hardware warhorse.
As usual this forum is is the best!   Thanks all.

---

