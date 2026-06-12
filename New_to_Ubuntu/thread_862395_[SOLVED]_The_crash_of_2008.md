---
title: "[SOLVED] The crash of 2008"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by nuddernuby on 2008-07-17
I guess this one is going to need some serious advice.

On 8.04 (2.6.24-16-generic): Updated through update manager - large number of files.  On next boot up it was evident something had gone wrong:
- No task panels on desktop
- Mouse not working
- Sound not working
- Internet connection not working

- Cannot re-install/boot from CD because of GRUB.
- Can get to terminal window - but don't know what to type in!

ER seriously required.  Any Samaritan around?

---

### Post by jimv on 2008-07-17
GRUB has absolutely nothing to do with booting from a CD.  You need to change the boot order in your BIOS so that your computer attempts to boot from CD before the harddrive.

---

### Post by z.s.tar.gz on 2008-07-17
You can't boot cd from bios? Like it would ask you what to boot from?

But anyways, just looking at it, it looks like you need a new hard drive.
But I don't really know. You probably want to wait for someone more experienced.

---

### Post by DGortze380 on 2008-07-17
GRUB has nothing to do with booting a cd.

put the live/install cd in the drive, reboot hold the "c" key.

if that doesn't work, reboot, enter bios by pressing whatever key your system requires, and changed the boot order to boot cd-rom first.

reinstall.

voila.

---

### Post by Frenske on 2008-07-17
And did you try the recovery kernel!!! Should be in the GRUB!

---

### Post by phoenix_abhi on 2008-07-17
If there is no panel, mouse is not working, how will u go 2 terminal?
I know how !

Find the gnome-panel(or gnome -panel) from user/bin and execute it or run it in terminal or use alt+F2.

Confirm ur upper panel is working or not.

Switching 2 Hardy

NB - Maximum upgrade from 7.10 to 8.04 resulted a failure !!!!

---

### Post by piousp on 2008-07-17
For terminal, just press Ctrl + Alt + F1

To go back to X, its the same: Ctrl + Alt + F7 (seven)

You can try to remove your .gnome dir from your /home

---

### Post by jimv on 2008-07-17
> **DGortze380 said:**
> GRUB has nothing to do with booting a cd.

put the live/install cd in the drive, reboot hold the "c" key.

if that doesn't work, reboot, enter bios by pressing whatever key your system requires, and changed the boot order to boot cd-rom first.

reinstall.

voila.

DUDE.  The C key only works on a Mac.

---

### Post by DGortze380 on 2008-07-17
> **jimv said:**
> DUDE.  The C key only works on a Mac.

not true. I've done it PC's dozens of times.

---

### Post by Nxion on 2008-07-17
> **DGortze380 said:**
> not true. I've done it PC's dozens of times.

I have been a Apple/PC tech for a long time and always know this to only work on Macs. I am curious to know what pc manufacture this has worked on. Maybe I just have never encountered and pc that uses the "c" key to boot off a cd.

Cheers

---

### Post by DGortze380 on 2008-07-17
> **Nxion said:**
> I have been a Apple/PC tech for a long time and always know this to only work on Macs. I am curious to know what pc manufacture this has worked on. Maybe I just have never encountered and pc that uses the "c" key to boot off a cd.

Cheers

Granted it does not work every time, hence the alternate instructions... but it does work sometimes (relatively often in my experience)... 

most recently a cheap build for a friend with a biostar board, an older eMachines desktop, and a year old vaio notebook

---

### Post by nuddernuby on 2008-07-18
One or two points:
- The Smart Boot Manager Files also appear to have been corrupted - hence no access to boot from CD via this channel
- The option of holding down c key did not work
- Yes, I can get into BIOS (after some piano playing during boot up)
- I was hoping to solve this without having to do a fresh install as there is a large amount of data not backed up which will now be lost

Any ideas before I format?

---

### Post by anjilslaire on 2008-07-18
Yeah:
Boot a Live CD , copy the data off, then reinstall.

---

### Post by nuddernuby on 2008-07-18
Thanks, anjilslaire, Will go looking for a live CD.

---

