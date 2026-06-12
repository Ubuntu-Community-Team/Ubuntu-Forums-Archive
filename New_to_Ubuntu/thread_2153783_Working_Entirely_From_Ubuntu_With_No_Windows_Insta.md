---
title: "Working Entirely From Ubuntu With No Windows Installation"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by tal1m0n on 2013-06-12
I've played around with ubuntu a little in the past but always got hung up on one issue or another. The most recent attempt I tried to run the game League Of Legends and after playing around with various Wine installations, patches, and other work arounds it still had some serious graphical issues.


Well i'm about to reinstall my Windows 7 OS so this gives me an oppertunity to to try again. But the thing is I don't want to have to mess around with dual bootings because I like organizing my OS and messing around with the placement of everythign, keeping it streamlined and convienent so either one or another. 

I use my windows to play games such as LOL, Civilization 4, Starcraft 2. 

3D modeling and Animation with Maya, Zbrush, etc. 

Being able to switch from dedicated GPU to Integrated for preserving power. 


All of these things would probably be a pain to set up in the Ubuntu enviroment however hopefully I can manage it. 


My question is.... Ubuntu the best for full graphical functionality, along with security, and anonymity? (I've set up VPN's and TOR previously, at least that wasn't difficult.)

And what about the "Encrypt hard drive" feature in Ubuntu. Does that offer the same level of quality as Truecrypt?

---

### Post by Isamu715 on 2013-06-15
[QUOTE=tal1m0n]And what about the "Encrypt hard drive" feature in Ubuntu. Does that offer the same level of quality as Truecrypt?[/QUOTE]
[This article]("https://wiki.archlinux.org/index.php/Encryption#Comparison_table") provides a comparison of encryption methods on GNU/Linux systems, you can see for yourself how encryption used in Ubuntu compares to TrueCrypt. The "Encrypt hard drive" option is **dm-crypt + LUKS** and "Encrypt home directory" is **eCryptfs**.

[QUOTE=tal1m0n]My question is.... Ubuntu the best for full graphical functionality, along with security, and anonymity?[/QUOTE]
If you're comparing with Windows Ubuntu will indeed be the better choice when it comes to security and anonimity. As for **full** graphical functionality it depends on what you actually do, however, you must be prepared to use the command line from time to time, unfortunately, not everything is accomplished with a GUI.

[QUOTE=tal1m0n]I use my windows to play games such as LOL, Civilization 4, Starcraft 2. 

3D modeling and Animation with Maya, Zbrush, etc. 

Being able to switch from dedicated GPU to Integrated for preserving power. 


All of these things would probably be a pain to set up in the Ubuntu enviroment however hopefully I can manage it. [/QUOTE]
If you intend to set up the exact same applications it's very likely to be a pain. Not counting games, most Windows software has a free Ubuntu alternative, like Blender for 3D modeling and animation. Starcraft 2 and Civilisation 4 both have a Platinum rating on Wine so running them shouldn't be a problem. League of Legends is known to cause problems but it may be possible to get it into playable state.

---

### Post by MidnightGrey on 2013-06-16
> League of Legends is known to cause problems but it may be possible to get it into playable state.
Yup, there is a forum post somewhere in LoL forums which explain how to install LoL using WINE and lists all the bugs/missing features in the game (i think the biggest one is you cannot access the Store).

However, you may be pleased to know the developers are working on a linux port of the game.

---

