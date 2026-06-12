---
title: "Unable to write /dev/loop0"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by Ultimatefry on 2013-08-23
Hello! I'm rather new to Ubuntu (I've been using the CD download for 10.10 because 12.04 was too picky), and I'm trying to format my hard drive to NTFS so I can run Windows on it. 
[SIZE=1]
I'm not sure what code I'm supposed to share here...[/SIZE]

---

### Post by ibjsb4 on 2013-08-23
And whats your question?

---

### Post by Ultimatefry on 2013-08-23
Is there any information that I can supply you with to help find out why it won't let me write to it?

---

### Post by ibjsb4 on 2013-08-23
If you want to use the live CD to format your HDD to NTFS you can use Gparted.  Run a live session from the CD and Gparted will be in the menu.

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Ultimatefry on 2013-08-23
Gparted refuses to recognize my HDD.

---

### Post by ibjsb4 on 2013-08-23
Open a terminal (Ctrl + Alt + T) and enter:

```
sudo fdisk -l
```

What it say?

---

### Post by Ultimatefry on 2013-08-23
absolutely nothing

---

### Post by Ultimatefry on 2013-08-23
UPDATE: I didn't know you had to add /dev/loop0 at the end...

```
Disk /dev/loop0: 692MB, 692674560 bytes
255 heads, 63 sectors/track, 84 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd37bea29

Disk /dev/loop0 doesn't contain a valid partition table
```

---

### Post by ibjsb4 on 2013-08-23
Ok, we can see yur HDD.   /dev/loop0 is telling me you have the wubi installer and not the live CD.  Anain, what do you want to do?  Do you want to install ubuntu?  Do you want to install windows?  Why are you trying to format your HDD?  

I will help, but I gots to know what we are up to :)

---

### Post by Ultimatefry on 2013-08-23
I want to install windows. It has no partitions, and when I got the computer it came with, it had no OS.

---

### Post by ibjsb4 on 2013-08-23
If you want to install windows, why do you think you need ubuntu to do this?

---

### Post by Ultimatefry on 2013-08-23
Trying to install it normally wouldn't work, so I'm trying to format the hard drive first.

---

### Post by ibjsb4 on 2013-08-23
Ok, it thats what you want to try.  Like I said, use Gparted thats on the live CD.  **BUT** you do not have the the "Live CD", you have the "wubi" installer.  The wubi install is used to install ubuntu inside windows.

---

### Post by Ultimatefry on 2013-08-23
Where can I get this "Live CD"? All I seem to get is the Wubi.

---

### Post by ibjsb4 on 2013-08-23
> **Ultimatefry said:**
> Where can I get this "Live CD"? All I seem to get is the Wubi.

Intel x86 is for a 32bit processor.

AMD64 is for a 64bit processor.

If you are not sure about what your processor is just go ahead and load the "Intel x86" (the first choice in the link), it will work with either a 32 or 64 bit processor.

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

### Post by 3rdalbum on 2013-08-24
The Windows installer includes a partitioner so you don't need to do any preparation work before running the Windows installer.

Just boot the computer from the Windows CD (you will need to change the boot order in the computer's BIOS in order to do that) and follow the prompts.

---

### Post by Ultimatefry on 2013-08-24
That doesn't seem to do anything, either.

---

### Post by ibjsb4 on 2013-08-24
Did you download the live CD?  If so, go ahead and boot up the live session and then open Gparted.  What does that show you?

How bout posting a screenshot of it.  And remember it will be slow going since you are running off a CD.[ATTACH=CONFIG]245683[/ATTACH]

---

