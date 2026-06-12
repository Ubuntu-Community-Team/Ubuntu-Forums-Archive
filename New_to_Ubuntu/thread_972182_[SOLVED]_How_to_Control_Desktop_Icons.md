---
title: "[SOLVED] How to Control Desktop Icons?"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by bettyhills on 2008-11-05
I like a clean desktop with only the icons that I really use a lot.

1.  How can I **remove icons** that appear spontaneously? 
 
For example, I carried some files via floppy disk to my new Ubuntu 8.04.1 PC.  In the process of cut and pasting them, Linux left an icon on the desktop shaped like the floppy disk and titled it: "1.5mb media".  How can I get rid of it?

2.  Is there a way to **set a preference in Ubuntu to prevent automatic icon placement** on the desktop in the future?

Thanks for any help.

---

### Post by Peter09 on 2008-11-05
Yes -open a terminal and type

```
gconf-editor
```

go apps->nautilus->icons

---

### Post by EnGorDiaz on 2008-11-05
> **bettyhills said:**
> I like a clean desktop with only the icons that I really use a lot.

1.  How can I **remove icons** that appear spontaneously? 
 
For example, I carried some files via floppy disk to my new Ubuntu 8.04.1 PC.  In the process of cut and pasting them, Linux left an icon on the desktop shaped like the floppy disk and titled it: "1.5mb media".  How can I get rid of it?

2.  Is there a way to **set a preference in Ubuntu to prevent automatic icon placement** on the desktop in the future?

Thanks for any help.

right click it

and unmount drive

---

### Post by bettyhills on 2008-11-05
All I really want to do is remove the icon from the desktop, but keep the flopping drive mounted and usable, just not have it show on the desktop as an icon all the time.

Do I really want to unmount the floppy drive?

---

### Post by Peter09 on 2008-11-05
As I have already said gconf-editor lets you define these icons.

---

### Post by oldsoundguy on 2008-11-05
why not unmount?  The moment you put a disk back in it, it will mount. (same can be said for the optical and usb drives.)

This is not the Linux of old where you had to go to terminal and write a command to mount a drive.

---

### Post by Gannon8 on 2008-11-05
Yes, but while a disk is unmounted, you cannot get data from it (Well, technically you can, but not in Nautilus).

Indeed, gconf-tool does what you are looking for.

---

### Post by snake444 on 2008-11-05
in preferences of something there is option of something like "Automatic Place icon of mounted volumes on desktop", i dont remember where it is but if you find it remove the V

---

### Post by oldsoundguy on 2008-11-05
> **Gannon8 said:**
> Yes, but while a disk is unmounted, you cannot get data from it (Well, technically you can, but not in Nautilus).

Indeed, gconf-tool does what you are looking for.

Of course you can't read from a disk if you unmount it. but the OP was at issue with the icon remaining after the disk was removed .. which it does most of the time unless you unmount it or clear the desktop. If you remove the disk, you can't expect to read from it unless you are The Great Carnac! LOL

Without a disk in the drive, no reason to have the drive mounted.

---

### Post by bettyhills on 2008-11-06
Thank you, all.  

Peter09, gconf-editor is exactly what was needed -- under apps>nautilus>desktop, unchecked "show volumes" to do away with that icon and now I know how to control others.  The issue is solved.  Thanks.

---

### Post by sosaudio1 on 2008-11-26
Added second HDD to my system and don't want to see that icon...but...do want to see other icons. IE removable flash, I want the icon so that I can un-mount and eject. DVD/CD Drive, show mount when disc in drive, disappear when disc ejected...bottom line...the second hdd is permanent so I don't want to always see the icon on my desktop...how do I fix this?

Mount point is /media which I kinda think is my problem...but...is there a line of code that I can add somewhere that will default to it ***not showing*** up?

Rich

---

### Post by sosaudio1 on 2008-11-27
> **sosaudio1 said:**
> Added second HDD to my system and don't want to see that icon...but...do want to see other icons. IE removable flash, I want the icon so that I can un-mount and eject. DVD/CD Drive, show mount when disc in drive, disappear when disc ejected...bottom line...the second hdd is permanent so I don't want to always see the icon on my desktop...how do I fix this?

Mount point is /media which I kinda think is my problem...but...is there a line of code that I can add somewhere that will default to it ***not showing*** up?

Rich

Think I figured it out after some deeper searching..it appears that if you have your mount point in /mnt it will not show up....but...if you have your mount point in /media, it will.

Is there a way to change the rules for specific peripherals? For example, I go into a config file that says "show desktop icon for usb, CD/DVD in tray, digital camera, hdd, then I can comment out the hard drive in media?

If not...it is not a real big deal...but would be nice to see it not be there...with the exception that it not be an all or nothing instance for the icons there.

PEACE OUT
Rich

---

