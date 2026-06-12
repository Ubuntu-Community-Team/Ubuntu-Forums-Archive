---
title: "Update from 12.04 to 12.10 broke Unity"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by PoLoMoTo on 2013-01-27
After I upgraded from 12.04 to 12.10 Unity doesn't appear to work.  I have run a bunch of commands such as reinstalling Unity, resetting Unity and several other that I can't really remember.  Everything I try seems to come back to display 0 not working.  When I log in (log in screen looks fine) all I get is my cursor and wallpaper, nothing else.  Any ideas?

*Upgrade

---

### Post by 64Buntu on 2013-01-27
is the desktop slow when you first load it?

---

### Post by offgridguy on 2013-01-27
> **PoLoMoTo said:**
> After I updated from 12.04 to 12.10 Unity doesn't appear to work.  I have run a bunch of commands such as reinstalling Unity, resetting Unity and several other that I can't really remember.  Everything I try seems to come back to display 0 not working.  When I log in (log in screen looks fine) all I get is my cursor and wallpaper, nothing else.  Any ideas?
Technically this is not an update but an upgrade, problems after upgrading to 12.10 are not
uncommon.  you could try a thread search.
Also there is no 'down grade'  if you wanted to go back to 12.04, you will have to reinstall.

---

### Post by PoLoMoTo on 2013-01-27
> **64Buntu said:**
> is the desktop slow when you first load it?

No, its pretty quick.  It also never does the log in tone, not sure if that's a unity thing too.

> **offgridguy said:**
> Technically this is not an update but an upgrade, problems after upgrading to 12.10 are not
uncommon.  you could try a thread search.
Also there is no 'down grade'  if you wanted to go back to 12.04, you will have to reinstall.

Yea I'll go edit the first post sorry if it caused any confusion.  I have tried several search none specifically here though, I'll try again in a few minutes.  I would really rather fix this than reinstall but I guess if I have to I will.

---

### Post by mlentink on 2013-01-27
Most likely related to your video driver, as 12.10 did away with the Unity-2D fallback. There are quite a few threads about this.

---

### Post by 64Buntu on 2013-01-27
> No, its pretty quick. It also never does the log in tone, not sure if that's a unity thing too.

oh i had problems with unity being very slow and having items missing(like side bar ect)

@mlentink your signuture is classy

---

### Post by bogan on 2013-01-27
Hi1, PoLoMoTo,

Right Click in the Desktop>Change Desktop Background> All Settings>Software Sources> Additional Drivers Tab.
Activate Video driver. Reboot

If that does not work, try 'Ctrl+Alt+F1', that should give a TTY, Text  Terminal, and a login prompt. Enter your username and press 'Enter',  then your password - it will not show & 'Enter'.

Post the output of:      ```
uname -r 
lspci -nnk | grep -iA3 vga 
/usr/lib/nux/unity_support_test -p
startx 
```and explain how far things get for more instructions.

[ If necessary 'Ctrl+Alt+F7'should return you to the GUI screen.]

Chao!, **bogan.**

---

### Post by Frogs Hair on 2013-01-27
12.10 has no Unity 2D if you didn't notice. The reset command for Compiz and Unity  has changed on 12.10 also. 

[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

---

### Post by PoLoMoTo on 2013-01-28
Sorry I just decided to reinstall, hadn't seen any of the newer posts when I decided on it.

---

