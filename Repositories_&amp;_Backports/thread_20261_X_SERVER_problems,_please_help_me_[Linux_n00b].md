---
title: "X SERVER problems, please help me [Linux n00b]"
date: 2005-03-15
forum: Repositories &amp; Backports
---

### Post by Shatner on 2005-03-15
Hey guys, I'm sure you've seen this before but I can't seem to find a thread that helps me much. I'm a complete Linux n00b so go easy. Here is what I get after booting up ubuntu:
[screen flashes]
Problem with X Server blah blah..... click yes to view description

Another screen.......click yes to see detailed description

Another......"Cannot currently start X Server, please make sure it is configured right." and there is "OK" as the only option.

After that all I get is the login screen.

I have an NVIDIA GeForce FX 5200, 512mb RAM, Intel Celeron 2ghz processor, and the kernal is 2.6 something.

Any help would be appreciated.

BTW, I think I am running warty wart or something like that.

[btw, I don't know if this is in the right section]

---

### Post by bored2k on 2005-03-15
[QUOTE=Shatner]Hey guys, I'm sure you've seen this before but I can't seem to find a thread that helps me much. I'm a complete Linux n00b so go easy. Here is what I get after booting up ubuntu:
[screen flashes]
Problem with X Server blah blah..... click yes to view description

Another screen.......click yes to see detailed description

Another......"Cannot currently start X Server, please make sure it is configured right." and there is "OK" as the only option.

After that all I get is the login screen.

I have an NVIDIA GeForce FX 5200, 512mb RAM, Intel Celeron 2ghz processor, and the kernal is 2.6 something.

Any help would be appreciated.

[btw, I don't know if this is in the right section][/QUOTE]
 [btw, I don't know if this is in the right section] you can bet not .

That "bla bla bla" can tell us a lot you know ...

If you're running Hoary try login in and typing
 sudo dpkg-reconfigure xserver-xorg

---

### Post by LongTooth on 2005-03-17
bored2k, thanks for the tip- sudo dpkg-reconfigure xserver-xorg. That did the trick. Had the same problem. Used the 'dpkg-reconfigure...' and that took care of my Xserver problems. Once again, thanks.

---

### Post by Shatner on 2005-03-17
i tried that and it didn't work, i need some help plz!

---

### Post by search66 on 2005-03-18
[QUOTE=Shatner]i tried that and it didn't work, i need some help plz![/QUOTE]
 Can you post the *full* error message?  I also suggest googling the EXACT message into Google... You'd be surprised of what you will find.

---

### Post by Shatner on 2005-03-25
yeh, i'll post the full message

---

