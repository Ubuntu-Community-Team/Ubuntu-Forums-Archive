---
title: "black dots"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by shayvasa on 2008-05-29
hi, i have a problem. since i installed the new ubuntu i have these black dots in the top of my desktop. heres a picture of my desktop, look up and youll see them. any idea of how to remove them?

---

### Post by stalkier on 2008-05-29
> **shayvasa said:**
> hi, i have a problem. since i installed the new ubuntu i have these black dots in the top of my desktop. heres a picture of my desktop, look up and youll see them. any idea of how to remove them?

Ok I might be totally wrong here but I believe this has something to do with your video drivers. Do you have the ATI or NVidea restricted Drivers enabled? If not, you may want to try that. Go to  System - Administration - Device Drivers. Choose to enable the video drivers. You may have to restart the system.

---

### Post by shayvasa on 2008-05-29
i have them enabled already

---

### Post by chewearn on 2008-05-29
It could be hardware problem?  Try cleaning up the inside of your PC, especially the contacts between PCI cards, dimm sockets and motherboard.

---

### Post by philinux on 2008-05-29
No it's graphics, I've had this and it's compiz.

Turn compiz/desktop effects of reboot then re-enable it.

---

### Post by shayvasa on 2008-05-29
how do i turn it off?

---

### Post by FuturePilot on 2008-05-29
System&#8594;Preferences&#8594;Appearance. Click the Visual Effects tab

---

### Post by shayvasa on 2008-05-29
it didny work, i turned off compiz, rebooted and the dots are still there

---

### Post by Zacariaz on 2008-05-29
try and turn of your ati/nvidia drivers, if the problem is still there after a reboot you can be fairly sure it's a hardware problem and if not, it maybe actually help anyway when you re install them.

---

### Post by shayvasa on 2008-05-29
theyre still there, and it cant be hardware problem cause its a new comp

---

### Post by Malac on 2008-05-29
> **shayvasa said:**
> theyre still there, and it cant be hardware problem cause its a new comp
I beg to differ.
Just because it is new hardware does not mean it can't be the hardware.
I have lost count of the number of support calls that contain the words "it can't be xxxxxx, it's brand new". It then turns out that is what it is.
Try changing the card with one from a friends machine or another one you have, also check cables to screens too for kinks or bad twists.

---

### Post by shayvasa on 2008-05-29
never mind, its too much work just because of some dots, but thanx any ways

---

### Post by Addie MacGruer on 2008-09-19
Hi there shayvasa

I get this as well (Ubuntu HH, all up-to-date, Intel Q6600, Nvidia 8800GT, nvidia drivers loaded).  Faster than rebooting the Xserver to get rid of them is to switch to a tty and back: press

ctrl-alt-F1
ctrl-alt-F7

in quick succession removes them.  Will try and narrow it down further.

1. 'brown' desktop appears
2. 'black dots' appear
3. log-in noise plays
4. configured desktop appears.

I seriously doubt it's hardware: everything else is perfect; it displays reproducibly, it always disappears for good after restarting / toggling off of X; opening the gnome menus under them moves them for a while before they move back.

Addie.

---

### Post by philinux on 2008-09-19
I just recently had this and found that after a kernel update my hardware driver was not in use. Check in system>admin>hardware drivers.

---

### Post by Orange_and_Green on 2008-09-19
Perhaps it's also worthwhile to check if the monitor's cable is well inserted into both the monitor's socket and the video card's socket.

Last week we had a monitor that was displaying weird things and I "fixed" it by pushing the plug into the video card socket tight :lolflag:

---

### Post by pyromanic123boom on 2008-09-19
Well what kind of monitor are you using and how old is it?
Just an idea that it could maybe be dead pixels? I've never had this problem but I know it can happen.

---

### Post by Addie MacGruer on 2008-09-24
Found the problem!  It's the vga setting when I first start up that causes it.  Did sudo vim /boot/grub/menu.lst, changed my kernel line from:

kernel /boot/vmlinuz-2.6.24-19-generic root=... ro quiet

to

kernel /boot/vmlinuz-2.6.24-19-generic root=... ro quiet vga=773

They're all gone now.

It's also in this thread here:

[http://ubuntuforums.org/showthread.php?t=784045](http://ubuntuforums.org/showthread.php?t=784045)

Addie.

---

### Post by Crafty Kisses on 2008-09-24
The weird thing is it could be dust, try dusting everything out. I had a similar issue to yours awhile back and all it was, was dust, so get a can of compressed air and read the directions before you use it, and start dusting everything out and lets see if that solves the issue.

It also could be your video card just getting older or failing, see if the fan is working on the video card and what not, just check the normal life signs of a video card. I'd also like to see the output of this command:
```
glxinfo
```It could also be a direct rendering issue too, so that's why I want to see that command.

---

