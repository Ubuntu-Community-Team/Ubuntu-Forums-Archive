---
title: "Total noob needs help with some drivers. Boot issues"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Takahashi on 2008-05-19
I am making a total transition to Ubuntu, I have been using it on and off but never made a full switch, Windows XP SP3 finally made my mind, and now I'm here, I am ready to make the switch I just am having a few problems.

I am running 8.04
I do not have a liveCD

First off, I am having trouble with the ATI restricted drivers, on my x1600 AGP8x, Since installing them I get a black screen on boot up, I have been trying to look for a solution but cannot find a simple one. I tried to find a safe graphics mode option when I hit escape in the boot up but only get the recovery options. So far no luck, any way I can change my Video drivers to the defaults?

Second, I am having problems with my external Sound Blaster LIVE 24-bit sound card, I can get CD/DVD's to play sound and same with the system, but no when it comes to VLC and FireFox, any help their?

Thats all the trouble I am having, I really would like to get the full transition done with. 

Thanks!

-Takahashi

---

### Post by Happy_Man on 2008-05-19
For your video issue:

Boot the recovery kernel, and when it all finishes and drops you at a prompt, type ```
sudo nano /etc/X11/xorg.conf
```

Scroll down to the Device Section, and change the driver there from "fglrx" to "vesa". Reboot, and see if that helps.

---

### Post by Takahashi on 2008-05-19
Thanks man, although I still cannot get it to work.

When I boot the recovery I get a menu with about 7 different options of normal and recovery boots along with the mem test. 

When I do go into the recovery boot, I get 4 different options. I went into the root one figuring that is the only one where I can type commands.

When I typed this command out

Sudo nano /etc/x11/xorg.conf

I get a black screen to write up a new file, and thats it. There is no device information present. 

Thanks for your help though, I'll keep looking.

---

### Post by Fixman on 2008-05-19
> **Takahashi said:**
> Thanks man, although I still cannot get it to work.

When I boot the recovery I get a menu with about 7 different options of normal and recovery boots along with the mem test. 

When I do go into the recovery boot, I get 4 different options. I went into the root one figuring that is the only one where I can type commands.

When I typed this command out

Sudo nano /etc/x11/xorg.conf

I get a black screen to write up a new file, and thats it. There is no device information present. 

Thanks for your help though, I'll keep looking.

Don't boot on the recovery kernel if you want to modify X configuration files, just boot normally and, when it fikishes booting (and black screens you), press ctrl+alt+f1 to access a terminal.

---

### Post by Takahashi on 2008-05-19
This I have also tried, and I cannot see a terminal to type in.

I have tried using a USB and a PS/2 keyboard, so I don't know whats going on :(

Thanks for your help though!

---

### Post by Takahashi on 2008-05-20
bump

---

