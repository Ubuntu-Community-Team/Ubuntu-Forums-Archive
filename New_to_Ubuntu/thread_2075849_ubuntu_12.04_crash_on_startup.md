---
title: "ubuntu 12.04 crash on startup"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by hansnn on 2012-10-24
I just managed to install ubuntu 12.04 alongside my windows 7 op.
I am on ubuntu as i'm writing this and it's working just fine (at least to open firefox and enter this page )

But the only way i can enter ubuntu is by starting it in recovery mode, and then click "continue normal boot" or something similar (not excact quote but i think you know what i mean.)
If i don't enter recovery mode first, the system will crash at the purple screen. I think it is right before some kind of loading screen or Ubuntu logo, but i'm not sure as i've never seen it.
The screen will be purple with horizontal lines of random colors, and if i press ESC the bottom half of the screen turns black with some white dots moving downward (text?)

I also had an error message appear while i was on the desktop, but i restarted the system so i don't have it available at this time. It was something about an internal error, ValueError.


I installed Ubuntu with a live CD, ISO downloaded from Ubuntu.com.


SYSTEM SPECS 

I have a nVidia geforce gtx 580 graphics card, but when i look at my system specs in ubuntu this is what shows up under graphics:
VESA: GF110 Board - 12610002

CPU: Intel® Core&#8482; i7-3770 CPU @ 3.40GHz × 8 

Motherboard: MS-7758 (v1.x)

Excuse my lousy system spec overview..


Also when i go to system settings > displays, it appears that i am on a laptop. Which i am not.



Just tell me what more information you need and i will get it.

Thank you plenty in advance.

---

### Post by ajgreeny on 2012-10-24
Next time you boot up the machine, at the grub menu, with the ubuntu you wish to boot highlighted, hit the "E" key to edit the grub boot details.  Use the cursor keys to go to the line that has "quiet splash" at or near to the end, and add **nomodeset** to that line after those two words.  Now hit F10 to boot, and you may get a proper GUI.

I think your problem may be the nvidia graphic card, and you may be able to sort the problem after booting by installing the appropriate additional driver, which you can do from the dash and searching for "drivers".

---

### Post by hansnn on 2012-10-25
Setting nomodeset fixed the problem, thanks a bunch :)

---

### Post by ajgreeny on 2012-10-25
If updating your graphic driver does not solve the problem permanently for you it is possible to add the **nomodeset** option to the file at /etc/default/grub by editing the line ```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
``` and adding nomodeset to that between the quote marks.
```
gksudo gedit /etc/default/grub
``` will allow you to edit that system file.

---

