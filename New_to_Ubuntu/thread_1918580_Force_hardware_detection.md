---
title: "Force hardware detection"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by WebNewbie on 2012-02-01
Hi all, 

Is it possiblr to force hardware detection ?
Example, I have a failing harddrive, it's not detected at boot.
I've tried switching the PC on and off, but it just seems to hang for a while, then boots, with only one drive detected.

I'm booting off a USB pendrivelinux.

---

### Post by mikewhatever on 2012-02-01
Can you elaborate on what you mean by failing. Is it the file system or a mechanical failure? Generally, electrically or mechanically defective hardware should be replaced, and not force-detected.

---

### Post by WebNewbie on 2012-02-01
Hi mikewhatever,

Thanks for the quick response. Don't know if its hardware failure, drive spins OK, no noises. Since I had a power outage, on my windows machine, I've been getting I/O errors, I then stopped using it, when it wasn't showing at on windows.

Disconnected the drive, connected it to my Linux box via USB adaptor, still not recognised, when I'm booting off USB pendrive linux, the boot process hangs a while ( looking for it )I get messages about I/O erros, when the boot process is complete, all I see is my first drive, and USB.

My plan is to image the drive onto a good drive, but i can't do that if it's not seen.

Any ideas ?

---

### Post by mikewhatever on 2012-02-01
After connecting it to a linux box, run **dmesg | tail**. If the device itself is detected, you'll get some relevant output.

---

### Post by WebNewbie on 2012-02-01
Hi mikewhatever, yeah ... I did that. What I got back was page after page of data, relating inode errors.
Lots of info I didn't reall yunderstand. But by reading throught it, I concluded that it was another version of I/O errors.

The thing that confuses me is, the imaging process. I going to use gddrescue, and the faulty device mustn't be mounted. So if no OS sees it, how can i possibly make an image of it ?

---

### Post by mikewhatever on 2012-02-01
Strange, you should only have gotten the last ten lines. How about the output of **sudo fdisk -l**? Can you post it here.

---

### Post by WebNewbie on 2012-02-01
Hi mikewhatever

I'm at work at the mo ... i'll be home in 2 hours or so, i'll post back then the result of **sudo fdisk -l**

As right now I can't remember, and I don't want to take a SWAG at it ;)

---

### Post by WebNewbie on 2012-02-01
Hi **mikewhatever**, sorry it's taken me a while to get back to you, just been participating in a data recovery thread.

Also to do with this problem, but this is more to do with hardware recognition / detection. Anyway, as you wanted to see the feed back from **fdisk -l** this is what I get;

[FONT="Lucida Sans Unicode"][COLOR="Purple"]root@Vigor11 /root % fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005bf5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   970760191   485379072   83  Linux
/dev/sda2       970762238   976771071     3004417    5  Extended
/dev/sda5       970762240   976771071     3004416   82  Linux swap / Solaris

Disk /dev/sdb: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          80    15663103     7831512    b  W95 FAT32

Disk /dev/sdc: 4022 MB, 4022337536 bytes
124 heads, 62 sectors/track, 1021 cylinders, total 7856128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dcd2a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62     7849447     3924693    b  W95 FAT32

root@Vigor11 /root %[/COLOR][/FONT]

My setup is as follows;

/dev/sda/ is my main drive
/dev/sdb/ is my USB PendriveLinux that I booted from, as SystemRescue is on there.
 and /dev/sdc is another USB pendrive that I saved these terminal commands to. In order to move to my windows machine that I'm using now.

As you can clearly see, my faulty drive is not shown.
Usually linux would of mounted it as sdb, and all other devices would of dropped down a letter. Am I correct.

So, my original question, is it possible to 'force' linux to look again, if you know what I mean.

---

### Post by mikewhatever on 2012-02-01
Forcing it to look again would make sense if System Rescue was a person. If a device (not file system) has become inaccessible, it's most probably physically defective, and no amount of detection would fix that.

---

### Post by WebNewbie on 2012-02-02
I like the way you put that.
Yeah, I'd kick his butt, and tell him to look again  ;)

I thought somebody would say that, just needed confirmation from people in know. There should be a 'magic button' somewhere !

thanks

---

