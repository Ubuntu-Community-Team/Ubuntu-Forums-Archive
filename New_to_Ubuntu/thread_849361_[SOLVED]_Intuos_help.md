---
title: "[SOLVED] Intuos help?"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by SIStem_shock on 2008-07-04
I used Wubi to install Ubuntu and I read that ver. 8 should automatically detect a tablet but it didn't. Or rather, it only works as a mouse. The only tut I can find is [http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915) but that says for the Bamboo and I don't think it is what I need. I got my tablet working in Mint by just uncommenting a couple of lines in the xorg.conf and this tutorial says be sure to have several hours available. This is a newer version than the Mint I'd been using, so that can't be right? 
I have a Wacom Intuos 2, USB. I looked for the Wacom Tools package to download in the add programs section, but it isn't there. Isn't there an easy way, like in mint?

---

### Post by SIStem_shock on 2008-07-06
So, does no answer mean that the long complicated Bamboo tutorial really is the one I need for the Intuos?

---

### Post by jualin on 2008-07-06
I guess so pal, considering the fact that 53 users found the post very helpful I guess that after you do those steps the Tablet should work.

---

### Post by SIStem_shock on 2008-07-06
> **jualin said:**
> I guess so pal, considering the fact that 53 users found the post very helpful I guess that after you do those steps the Tablet should work.

Unless those were 53 Bamboo users and not Intuos users, since the post does say it is for the Bamboo. It just seems very odd that the process should have gotten that much more difficult with an updated version, Pal. Weird.

---

### Post by jualin on 2008-07-06
Have you tried using the same steps used in Mint, since Mint is based in Ubuntu maybe the same solution can work. Just a shot in the dark.

---

### Post by SIStem_shock on 2008-07-06
> **jualin said:**
> Have you tried using the same steps used in Mint, since Mint is based in Ubuntu maybe the same solution can work. Just a shot in the dark.

Yes, that is the first thing I tried, but the xorg.conf in Ubuntu didn't even contain any of those lines to uncomment, which is what you had to do in Mint. Being new to this, I didn't know if it was ok to just type them in or not, especially since I couldn't find any mention of anyone doing that in Ubuntu. The fact that Mint is based on Ubuntu is the main reason I didn't think that the solution should be THAT much more complicated in Ubuntu. I could see needing to do all that with the Bamboo tablets because they are new, but the Intuos 2 isn't, and I did read that it should automatically detect all of them except the Bamboo. 
And the welcome letter I got when I signe up here DID say not to be afraid to ask questions.

---

### Post by jualin on 2008-07-06
Don't be afraid to ask questions :). We are here to learn from your problems, to help you and to make eveything as easy as possible. Who knows you may find a better way to do it and you may write a Howto for people with a similar problem. I am searching for a better guide in the forums but I can't seem to find anything. Just hang in there buddy, I am sure you are not the only one with the same issue!

---

### Post by jualin on 2008-07-06
Another thing that you can try is editing your xorg file to the way that Mint suggests. If something goes wrong (no GUI after Reboot) you can enter to the command line using Ctrl+Alt+F2 and reconfigure your xserver by doing > sudo dpkg-reconfigure xserver-xorg

---

### Post by jualin on 2008-07-06
[In this thread]("http://ph.ubuntuforums.com/showthread.php?t=825941") they talk about the Intuos 2 and apparently they got it to work. Maybe you can PM them to ask them what method did they use.

---

### Post by jualin on 2008-07-06
Was [this]("http://www.linuxquestions.org/questions/linux-hardware-18/wacom-intuos-problem-in-ubuntu-gutsy-597112/") the solution in Linux Mint?

---

### Post by SIStem_shock on 2008-07-06
> **jualin said:**
> Was [this]("http://www.linuxquestions.org/questions/linux-hardware-18/wacom-intuos-problem-in-ubuntu-gutsy-597112/") the solution in Linux Mint?

Yes, just uncommenting those lines. It worked fine and was so easy, which is why it seems odd that I'd need to do all that terminal stuff (which I am just likely to mess up some how) to get the same results in Ubuntu. 

I had read that other thread already but that isn't the problem I'm having. When using one monitor, tablet and speaker set with both of my computers (kvm switch) I did always need to reset x anytime I switched back to the Mint one, but the the tablet functioned correctly. I'm not using a switch with this setup, though.

---

### Post by jualin on 2008-07-06
You are welcome!, Sorry I couldn't help you completely. Good luck

---

### Post by jualin on 2008-07-06
Can you post your xorg.conf file?

---

### Post by SIStem_shock on 2008-07-06
> **jualin said:**
> Can you post your xorg.conf file?
OK, I'll try. BTW, I just tried putting in those 3 lines that are in the Mint xorg.conf, but I got a garbled screen and the desktop wouldn't load so I used the instructions to rebuild the x server thingie and it booted back fine. 

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by jualin on 2008-07-06
I think that the Wacom driver have to be installed. I found this [link]("http://twodayslate.wordpress.com/2008/01/20/wacom-tablet-in-ubuntu/") that seems very simple, maybe you can try that one. Basically it tells you how to install the driver.

---

### Post by jualin on 2008-07-06
And I found [this other link]("http://ubuntuforums.org/showthread.php?t=25151") if you have a USB Wacom Intuos. Hope this helps!

---

### Post by SIStem_shock on 2008-07-06
> **jualin said:**
> And I found [this other link]("http://ubuntuforums.org/showthread.php?t=25151") if you have a USB Wacom Intuos. Hope this helps!

This one did the trick! \\:D/ I am now very very happy. Thank you!

---

### Post by jualin on 2008-07-06
Glad it worked!:) Feel free to ask anything else here in the forums. Like I said before we are here to help you. Welcome to Ubuntu! :guitar:

---

