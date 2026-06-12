---
title: "New user - need help with video driver"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by KLR_rider on 2008-07-27
I think Ubuntu is having a hard time with my computer's integrated graphics controller.  I wasn't able to install with the live CD, the screen would just go black, so I used the alternate CD to install.  The display still goes black when I launch Ubuntu.  Now I think I need to install a Linux driver for my graphics.  I wrote down what I've got (Intel 82865G graphics controller) and downloaded what I hope is the right driver from Intel's website (it's a .gz file) onto my USB drive.  How do I install this driver using the Recovery Mode? (That's the only thing I can get to work from GRUB).  Thanks in advance for your help.

Mark

---

### Post by PmDematagoda on 2008-07-27
Can you please post the output of:-
```
cat /var/log/Xorg.0.log
```
if possible?

---

### Post by KLR_rider on 2008-07-27
> **PmDematagoda said:**
> Can you please post the output of:-
```
cat /var/log/Xorg.0.log
```
if possible?

OK, here's a noobie question...
I ran the command you specified, and the output is quite large (I can't see the whole thing on the screen).  How do I scroll up to see the beginning of it?  Or maybe there's a certain string you're looking for?

Thanks!

---

### Post by rockstarrem on 2008-07-27
You should be able to just highlight it all and scroll up then right click and copy and paste.

---

### Post by KLR_rider on 2008-07-27
> **rockstarrem said:**
> You should be able to just highlight it all and scroll up then right click and copy and paste.

I'm working from recovery mode, and the mouse doesn't work at all.

Thanks

---

### Post by PmDematagoda on 2008-07-27
> **KLR_rider said:**
> I'm working from recovery mode, and the mouse doesn't work at all.

Thanks

Try printing the output to a file with:-
```
cat /var/log/Xorg.0.log > Xorg.log
```

Do you dual-boot with Windows by any chance?

---

### Post by 3rdalbum on 2008-07-27
If you use this command:

```
less /var/log/Xorg.0.log
```

you will be able to scroll up and down the file. Specifically, we'd be looking for any lines beginning with (WW) or (EE) or anything that sounds like an error.

---

### Post by KLR_rider on 2008-07-27
Thanks for taking the time to help me out!

I have a dual-boot system with Ubuntu and Windows XP.

I ran this command: ```
cat /var/log/Xorg.0.log > Xorg.log
``` which I assume creates a file called "Xorg.log" that has all this info.  Problem is, I don't know how to view or do anything else with this new file! (I'm really clueless about Linux and just about anything command-line related :confused: )

I also ran this one: ```
less /var/log/Xorg.0.log
``` OK, now I can see the output.  Here are the error messages I found:

[FONT="Lucida Sans Unicode"](WW) The directory " /usr/share/fonts/X11/cyrillic" does not exist. Entry deleted from font path.

(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000203 to 0x00000207

(WW) intel(0): PIPEASTAT before: status: VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS

(WW) intel(0): PIPEASTAT after: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS

(WW) intel(0): EXA greedy migration mode enabled

(WW) AIGLX: 3D driver claims to not support visual 0x23

(WW) AIGLX: 3D driver claims to not support visual 0x24

(WW) AIGLX: 3D driver claims to not support visual 0x25

(WW) AIGLX: 3D driver claims to not support visual 0x26

(WW) AIGLX: 3D driver claims to not support visual 0x27

(WW) AIGLX: 3D driver claims to not support visual 0x28

(WW) AIGLX: 3D driver claims to not support visual 0x29

(WW) AIGLX: 3D driver claims to not support visual 0x2a

(WW) AIGLX: 3D driver claims to not support visual 0x2b

(WW) AIGLX: 3D driver claims to not support visual 0x2c

(WW) AIGLX: 3D driver claims to not support visual 0x2d

(WW) AIGLX: 3D driver claims to not support visual 0x2e

(WW) AIGLX: 3D driver claims to not support visual 0x2f

(WW) AIGLX: 3D driver claims to not support visual 0x30

(WW) AIGLX: 3D driver claims to not support visual 0x31

(WW) AIGLX: 3D driver claims to not support visual 0x32[/FONT]

One other thing, when I attempt to start Ubuntu, I can see the Ubuntu logo and orange status bar, then the display goes black, and after a few seconds I get a message from (I think) the monitor's firmware that says:

[FONT="Lucida Sans Unicode"]OUT OF RANGE
VGA IN: 1024X768
HSYNC: + 68.5 KHZ
VSYNC: + 84.7  HZ
CLOCK:  184.0 MHZ[/FONT]

Don't know if that helps or not.  Thanks again everyone!

---

### Post by PmDematagoda on 2008-07-28
Perhaps the xorg.conf file is messed up, try this:-
1) Boot Ubuntu in Recovery Mode.
2) Once you reach the menu, select "xfix".

After that is done, see if your problem is now solved.

---

### Post by KLR_rider on 2008-07-28
> **PmDematagoda said:**
> Perhaps the xorg.conf file is messed up, try this:-
1) Boot Ubuntu in Recovery Mode.
2) Once you reach the menu, select "xfix".

After that is done, see if your problem is now solved.

I ran xfix, then tried to start Ubuntu, unfortunately it still has the same problem.

---

