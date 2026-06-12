---
title: "problem with screen booting ubuntu"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by wkwk on 2008-06-01
hi all friends, i'm completely new using linux (i had never used it before), and i still can't use it, ill start telling you the instalation:

first, i got some trouble installing ubuntu 8.04 desktop amd 64 version (my pc is an athlon 64 x2 4200+), when i tried to run ubuntu from live cd the graphics where like old tv graphics when there is no signal conected (lots of horizontal lines of many colors), then i read some info from this forum and i fixed it pressing f6 in the menu and erasing "quiet splash" and adding "vga=791", then the installation was succesful (i installed dual boot, win xp and ubuntu), but when i rebooted the PC, it loaded normally until it reached the GRUB, then i chose win xp and it loaded ok, but when i chose ubuntu, my monitor said "out of sync" (or somethig like that), then  i rebooted my pc and tried to edit the kernel of ubuntu (i think it's the kernel, i'm not sure)by pressing "e", then i did the same i did with the live cd (erasing "quiet splash" and adding "vga=791"), but then my monitor didn't prompt me "out of sync", but the screen was like in the beggining (like old tv graphics when there is no signal conected (lots of horizontal lines of many colors)), then now i dont know what to do to load ubuntu :(, and i really want to learn how to use ubuntu, anyone can HELP me :confused:

thank you friends

PD: sorry for the long tale

---

### Post by shifty_powers on 2008-06-01
two things.

what graphocs card are you using?

and try and download and use the 32-bit live-cd.

oh, and if all else fails, the alternate cd might work for you ;)

---

### Post by wkwk on 2008-06-01
> **shifty_powers said:**
> two things.

what graphocs card are you using?

and try and download and use the 32-bit live-cd.



thanks for answering,

- my graphics card is an ATI Radeon Xpress 1250 (syncmaster) on board

- i tied 32 bit and same thing, but i dont think thats the problem, because both give me the same problem, and 64 bit live cd is working fine with the fixes i mentioned in my first post

anyway, thank you  for answering, anyone who could help me i would thank my whole life

thanks

---

### Post by sayakb on 2008-06-01
At a terminal, do:
```
sudo apt-get install startupmanager
```
Then goto System->Administration->Startup-manager 
From there, try the different resolutions available.

---

### Post by wkwk on 2008-06-01
> **LinuxIsInnovation said:**
> At a terminal, do:
```
sudo apt-get install startupmanager
```
Then goto System->Administration->Startup-manager 
From there, try the different resolutions available.

thank you friend, but i can't see anything on screen, i mean, when i choose ubuntu in the grub, the screen becomes as i explained in my first post

thanks

---

### Post by shifty_powers on 2008-06-01
have you enabled the restrictd drivers btw?

---

### Post by sayakb on 2008-06-01
Sorry.. I thought only the boot screen was blurred. Ok try this: boot into recovery mode (At the GRUB menu) and execute this command at the #
```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Kevbert on 2008-06-01
Have you performed a checksum (hash) on the iso you downloaded and also run the disk check ?  Have you performed a memory check using the memtest option in the grub boot menu ?  
1)Try booting up Ubuntu from grub.  Leave the PC running for a couple of minutes where you get the funny display and then press Ctrl+Alt+F1. Hopefully you'll then get a text screen which will ask for your login user name and password (Enter these) You should then get the grub prompt ($ sign).  Now enter the following:
```
cd /etc/X11
sudo cp xorg.conf xorg.old
```
To back up all your current settings for display, keyboard etc.  Now enter
```
sudo dpkg-reconfigure xserver-xorg 
```
to try to change your monitor, display settings etc.  Enter all settings with care if and when prompted.  Save all settings and reboot.  If this doesn't work you could try changing your monitor and display settings manually.
2) Manual mode.  Repeat everything from 1) up to and including:
```
cd /etc/X11
```
Now enter
```
sudo nano -w xorg.conf
```
Your now in the nano editor.  Look for the following using the up/down arrow keys:
```
Section "Device"
        Identifier "My display card"
```
Delete everthing below this up to EndSection. Now find the next section:
```
Section "Monitor"
       Identifier "My monitor"
```
Delete everthing below this up to EndSection.  No press Ctrl+X to get out of editing mode.  You'll now get a message saying
Save modified buffer...?
Answer Y and then enter to save your modified xorg,conf  
Now reboot the machine and you should get the Ubuntu login screen in low resolution graphics when you select Ubuntu.  More info on xorg can be found [here]("https://help.ubuntu.com/community/FixVideoResolutionHowto#head-e2249d4bcb9fe0dea110f9b82ec7a40716221541")

---

### Post by wkwk on 2008-06-01
thaks friends, i'll try it a few hours later and i'll comment

---

### Post by philinux on 2008-06-01
dpkg-reconfigure -phigh xserver-xorg

This command in 8.04 does not set screen resolutions any more.

However running it may solve the problem.

I think the OP would be better with the alternate text based install cd.

---

### Post by cariboo on 2008-06-01
You could try **Ctrl-Alt +** to cycle through the different resolutions until you get one that will at least let you see where you are.

---

