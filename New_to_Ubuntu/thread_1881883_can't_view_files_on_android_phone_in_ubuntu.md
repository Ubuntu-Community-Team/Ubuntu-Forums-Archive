---
title: "can't view files on android phone in ubuntu?"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by cortman on 2011-11-16
Odd thing happening.

When I hook up my Samsung Galaxy S2 Android phone to my computer, I can open it up in Nautilus and browse around folders and stuff, but none of the files are visible! Even when I right click a folder and select properties, it says it contains no files.
The odd thing is that in Windows 7 all the files are right there and I can move, copy, paste, etc, which leads me to believe something's not quite right with my Ubuntu rather than my phone.
Anyone have any ideas how to fix this?

Thanks!

---

### Post by duke.tim on 2011-11-16
Ubuntu is probably reading the linux privileges and such on the android phone, which windows is ignoring.

Have you tried viewing hidden files ```
ctrl+h
``` or
from the title bar ```
View -> Show Hidden Files
```

also do the files have a "." in front of the filename? like ".podcast"

---

### Post by duke.tim on 2011-11-16
Well I just connected my android phone and I don't think my above post will help.

When connecting to view files on my phone I have to specifically "Turn on USB storage" otherwise nothing will show up.

Also I guess that the proper drivers would need to be installed...but they already should be, especially since it seems like the phone is mounting.

---

### Post by Mark Phelps on 2011-11-16
On my Android phone, when I connect via USB cable, a menu pops up on the phone asking what to do.  I have to select the Disk Drive option and press the OK prompt -- otherwise, it times out.

---

### Post by cortman on 2011-11-18
Well, thanks, guys. I guess I'll see if maybe it is something on my phone.

---

### Post by Mark Phelps on 2011-11-19
OK, I just tried connecting my Android phone -- and once I clicked Done on the phone, Ubuntu (11.10) automatically mounted the "drives" -- and they showed up in the Launcher.

So, if yours is not doing that, it's most likely not going to work.

---

### Post by gandaran on 2011-11-19
> **cortman said:**
> Well, thanks, guys. I guess I'll see if maybe it is something on my phone.
are you connecting with bluetooth or USB?
I have the same problem on ubuntu but only with bluetooth, the drive mounts and I can browse folders but there are no files in the folders.

---

### Post by The Cog on 2011-11-20
The GS2 is a strange animal. To get the USB mass storage working, you have to specifically enable it in the settings. This is the procedure I use:
1: On the phone, go Settings / Wireless and network / USB utilities and press the "Connect storage to PC" button.
2: Connect the USB cable
3: A USB connected screen appears on the phone. Press "Connect USB storage" button
4: I'm on Xubuntu, and for some reason the file browser doesn't appear automatically. So I launch thunar and press F9 to see the drives listing. The GS2 shows up as two USB drives - one (12G) is the "internal" sd card that the phone is built with. The other (16G in my case) is the micro SD card that you can install underneath the battery. I have no problem reading/writing either drive after clicking it to mount it. Screenshot attached, looking at the 12G internal drive.

Note that to add my own ringtones and alert sounds, I had to create a directory called **media** on the 12G drive, and create the directories **notifications** and **ringtones** inside that media directory.

---

### Post by cortman on 2011-11-22
> **The Cog said:**
> The GS2 is a strange animal. To get the USB mass storage working, you have to specifically enable it in the settings. This is the procedure I use:
1: On the phone, go Settings / Wireless and network / USB utilities and press the "Connect storage to PC" button.
2: Connect the USB cable
3: A USB connected screen appears on the phone. Press "Connect USB storage" button
4: I'm on Xubuntu, and for some reason the file browser doesn't appear automatically. So I launch thunar and press F9 to see the drives listing. The GS2 shows up as two USB drives - one (12G) is the "internal" sd card that the phone is built with. The other (16G in my case) is the micro SD card that you can install underneath the battery. I have no problem reading/writing either drive after clicking it to mount it. Screenshot attached, looking at the 12G internal drive.

Note that to add my own ringtones and alert sounds, I had to create a directory called **media** on the 12G drive, and create the directories **notifications** and **ringtones** inside that media directory.

Thanks a lot, Cog! That looks like it should work.

---

### Post by PaulWhipp on 2013-03-14
The problem is the same on my new Galaxy Note II (Android 4.1.1). I can see folders but not files.

Unfortunately there is no USB utilities option so I can't see any way to change the phone's settings so I can view the files. View hidden files has no effect.

Changing the developer USB debugging option also has no effect (although I can use adb at a stretch this way as a very tedious workaround).

---

### Post by codemaniac on 2013-03-14
Old thread closed. Please feel free to start a fresh thread.

---

