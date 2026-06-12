---
title: "GUI has disappeared"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Chris62 on 2008-11-23
I was hoping that I wouldn't be back here for a while but here I am. I have a dual boot Windows XP/Ubuntu 8.10 Machine. The Windows part of the machine uses an NVIDIA GeForce 9500 GT graphics card.

When I was looking at the Hardware Drivers  in "System/Administration" in Ubuntu I saw that it recommended one of three NVIDIA drivers so I thought I would try it because in my old computer which was also dual boot and which also had a GeForce (6200) graphics card it was recommended to try an NVIDIA driver which I did with a much improved display.

Unfortunately doing the same thing with the new computer has resulted in the loss of my desktop. When I boot into Ubuntu all I get now is a command line prompt.

Could someone tell me how to get the GUI back and how to deactivate the NVIDIA driver from the command line? I am assuming that if I deactivate the driver things will return to the way they were. I have already tried the following:

cd /etc/X11
sudo cp xorg.conf xorg.old
sudo dpkg-reconfigure xserver-xorg

but it didn't work, mainly, I suspect, because I didn't know the answers to some of the questions it asked.

If it is relevant. the monitor is an HP w1907v wide screen LCD monitor

Could someone please help?

Many thanks

---

### Post by krtica on 2008-11-23
Maybe you could try to edit xorg.conf

```
$ nano /etc/X11/xorg.conf
```

and check which driver you use.
Maybe you could try to use vesa to start GUI and then try to fix problem with nvidia drivers.

:confused:

---

### Post by AnoPoli on 2008-11-23
Have you tried the Alt+F7 to see what is happening back there?

---

### Post by fooman on 2008-11-23
i would try booting up and at the grub menu...choose recovery mode.

that should bring you to a menu...try the "xfix" option.  see if that gets you to the desktop.

---

### Post by Chris62 on 2008-11-23
Thanks krtica that revealed that it is using "nvidia" driver. Unfortnately I don't know the name of the Ubuntu video driver so I am not sure what to replace "nvidia" with. I am not sure whether it was my attempt to use the NVIDIA driver is the cause of the problem or whether it is a coincidence that this happened after trying to use it

---

### Post by Chris62 on 2008-11-23
AnoPoli, ALT+F7 does nothing and CTRL+ALT+F7 produces a blank screen

---

### Post by Chris62 on 2008-11-23
Thanks fooman, xfix didn't

---

### Post by krtica on 2008-11-23
Try to put "vesa" instead of "nvidia"...

---

### Post by Chris62 on 2008-11-23
Thanks krtica but that didn't work. When I rebooted after doing that I just got "Ubuntu 8.10 chris-desktop tty1" followed by "chris-desktop login:" on the screen. When I tried the Recovery Boot up I tried xfix again and also 'repair'broken packages. At one stage I got a message to the effect that there was a 'zombie' process operating, but nothing was fixed.

I think the answer is going to be to re-format the drive containing Ubuntu and possibly to reinstall ubuntu, or possibly just leave it empty and use it as a backup drive for Windows

---

### Post by fooman on 2008-11-23
> **krtica said:**
> Try to put "vesa" instead of "nvidia"...

try "nv" instead of vesa or nvidia

---

### Post by Chris62 on 2008-11-23
Thanks krtica and fooman,

I tried both suggestions but neither had any effect. When it boots I end up with a screen that says "Ubuntu 8.10 chris-desktop  tty1" followed by
"chris-desktop login:"

When I tried to edit xorg.conf with gedit, it said "Cannot open display" and somewhere along the line there was a message that there was a "zombie" process.

I have spent nearly a week, one way or another, trying to make things work in Ubuntu and am thinking now that the best thing would be to re-format the drive containing Ubuntu (it is on a drive of its own) and either re-install it or else just leave it as a backup drive for Windows. I am beginning to thing that Ubuntu is not for me!

---

