---
title: "Display shows double images when starting 14.x from usb to do new install"
date: 2014-05-20
forum: New to Ubuntu
---

### Post by fran_3 on 2014-05-20
-  I'm trying to install the latest Ubuntu Desktop on an XP eMachine (replace XP with Ubuntu)

- The computer runs Windows fine, but I want to replace XP since it is no longer supported.

- I've downloaded the lastest v14.x and put the iso on a flash drive and am trying to boot from the USB to do the install.

- It boots up fine from the USB drive on a very old IBM NetVist PC. (when using PLoP Boot Manager to force boot from USB)

- When I try to do the same thing on the target eMachine I get a couple of "problem" messages.

- But, the desktop comes up more or less but the icons on the desktop and the mouse pointer have sort of a double image.

- Same problem when I attempt to boot from a Slax CD (which works fine on other machines)

- I'm guessing it is the video card driver (As viewed in XP: Mfg = S3, Chip Tpe S374, Mem = 1MB, Adpt String = Diamond Stealth, Driver Provider = Microsoft 7/1/2001, Driver Ver = 5.1.2535.0, Default Monitor on Se GTrio 32/64)

The Questions:

1 - The machine is not online... will Ubuntu automatically try and download the proper driver for the video card if I put the machine online?

2 - How can I fix this?

Thanks for any help.

---

### Post by mörgæs on 2014-05-21
Hi, welcome to the fora.

Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by fran_3 on 2014-05-22
Thanks for the help. Can't run the command line... here is the current status...
 
I actually replaced the PCI video card with an AGP video card and dinked with the video card settings in the bios and was able to get the desktop to come up and it now looks fine...

- BUT... the Mouse stopped working when the desktop appeared... AND no response to the Keyboard.

- And no response when I bump the power button on the PC... so I had to hold the power button to get the PC to turn off.

BTW, I'm using Plop Boot Manager on a CD to get the PC to boot from a USB thumb drive with 14.x.

And, I'm choosing 'Try Ubuntu' instead of 'Install Ubuntu' (so the mouse works at this juncture... just not after the Desktop appears)

What next?

And, thanks again for the help.

---

### Post by ibjsb4 on 2014-05-22
You can try nomodeset in the F options.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by fran_3 on 2014-05-22
How do I try nomodeset? Where are the F options?

- Note that when booting from the USB drive I see no way to enter a command.

- The first screen that allows me to do anything is the one that gives me the choice to 'Try' or 'Install' Ubuntu... and there I have been clicking 'Try'

- AND, since the keyboard and mouse don't work when the Desktop appears I can't do anything at that point.

To review:
 
- The video display looks fine now since we switched to the AGP video card...

- The Problem now is the keyboard and mouse don't work once the Desktop appears.

Thanks for any help.

---

### Post by ibjsb4 on 2014-05-22
You do not get this screen?

[ATTACH=CONFIG]253366[/ATTACH]

If this is a ubuntu-desktop install, I think you will find your machine is underpowered for the job.  How much ram do you have?

---

### Post by fran_3 on 2014-05-22
Not normally. But... I discovered if I hit Esc right after the screen first displays the Ubuntu background colors with the small logos at the bottom...

Then I get the menu screen as shown in your last post ...

Then I pressed F6 and clicked on NoModeSet...

Then clicked 'Try Ubuntu without Installing'

And that seemed to fix it... Keyboard and Mouse work.

NEXT QUESTION: If I click 'Install' and replace XP with Ubuntu 14.x ... will I have to go through the same steps of selecting 'nomodeset' during every boot?

And, thanks again for the great help. We are excited about running Ubuntu !

---

### Post by ibjsb4 on 2014-05-22
> [COLOR=#000000]NEXT QUESTION: If I click 'Install' and replace XP with Ubuntu 14.x ... will I have to go through the same steps of selecting 'nomodeset' during every boot?[/COLOR]
Short answer, no.
This is covered in my above posted link.  Please read how to setup nomodeset and then post back with any questions.

---

### Post by ibjsb4 on 2014-05-22
> **ibjsb4 said:**
> If this is a ubuntu-desktop install, I think you will find your machine is underpowered for the job.  How much ram do you have?
I am going offline for a bit, please consider this.  If you still wish for a ubuntu-desktop install, we can try this.

---

### Post by fran_3 on 2014-05-22
1 - There is 1GB of ram and a 2ghz Celron processor in the old XP machine. Is this underpowered for Ubuntu?
2 - You said "we can try this" but there is nothing after that comment so we should try what?
Thanks again for the help.

---

### Post by mörgæs on 2014-05-22
The problem is likely your S3 graphics card. I suggest Lubuntu 14.04 as a first attempt.

Please see the link in my signature for more advice.

---

### Post by Vladlenin5000 on 2014-05-22
> **mörgæs said:**
> The problem is likely your S3 graphics card.


+1

---

### Post by ibjsb4 on 2014-05-22
> **mörgæs said:**
> I suggest Lubuntu 14.04 as a first attempt.

Please see the link in my signature for more advice.
+1  Lubuntu is a good choice, it should be fast on those specs.

[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

---

