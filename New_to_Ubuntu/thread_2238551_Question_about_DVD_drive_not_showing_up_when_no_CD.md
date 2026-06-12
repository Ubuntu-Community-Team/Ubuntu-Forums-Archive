---
title: "Question about DVD drive not showing up when no CD/DVD in drive"
date: 2014-08-08
forum: New to Ubuntu
---

### Post by Cindi_Marshall on 2014-08-08
I finally got Ubuntu 14.04.1 to run but now I have another question.

I have a DVD-burner in my Acer Aspire X1430G.  When I have a cd/dvd in the drive when I am booting up it will recognize the drive.  But when I don't have a cd/dvd in the drive, the drive doesn't show up.  Is there any way I can solve the problem?  And yes, the DVD drive does show up as a boot option when I start the system.

Thank you all so much in advance.  So far, I am LOVING Ubuntu and Linux.

---

### Post by grahammechanical on 2014-08-08
> [COLOR=#000000]But when I don't have a cd/dvd in the drive, the drive doesn't show up[/COLOR]

Does not show up where? Is this once the Ubuntu desktop has loaded? Open the Disks utility. Or put a CD/DVD disc in the drive and see if an icon of a disc appears in the launcher. Open the File Manager and see if CD/DVD disc is listed under Devices in the left pane.

What do you want to do and what is not happening? Do you want to play an audio CD or a video DVD? 

Regards.

---

### Post by Cindi_Marshall on 2014-08-08
> **grahammechanical said:**
> Does not show up where? Is this once the Ubuntu desktop has loaded? Open the Disks utility. Or put a CD/DVD disc in the drive and see if an icon of a disc appears in the launcher. Open the File Manager and see if CD/DVD disc is listed under Devices in the left pane.

What do you want to do and what is not happening? Do you want to play an audio CD or a video DVD? 

Regards.

Yes, the Ubuntu desktop loads fine, but on the left hand side where all the icons are when there is no CD/DVD in the drive the icon doesn't show up.  The CD/DVD drive doesn't show up anywhere in the devices if there is no CD/DVD in the drive.  Where do you find the Disks utility?

Thank you for helping me with this in advance.

---

### Post by mcduck on 2014-08-08
That is the normal behaviour, so everything is working as it should.

The file manager doesn't show *devices*, it shows* file systems*, and since a CD/DVD drive without any inserted disc doesn't contain a file system you could access there is no reason to show anything. I'm sure the drive itself is recognized by the system, if it wasn't it wouldn't appear even when you insert a disc.

Anyway, to find the Disks utility you can just open the Dash menu (using the Ubuntu button in the launcher panel or by pressing the Windows key) and search for "disks".

---

### Post by Cliff_Simonds on 2014-08-09
To open the drive you have to go to the Disks utillity like the other two said, then down to CD/DVD drive, and in the upper right hand corner is an arrow pointing upwards that opens the drive tray...

---

