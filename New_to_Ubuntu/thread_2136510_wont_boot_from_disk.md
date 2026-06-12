---
title: "wont boot from disk"
date: 2013-04-17
forum: New to Ubuntu
---

### Post by atomic drizzle on 2013-04-17
I bought version Ubuntu 12.10 in a magazine, but I cant get it to boot.  I have Kubuntu(32bit) already installed, but wanted to use Ubuntu.  Every time I restart my computer, and even when I try to boot from BIOs, it just takes me to my Kubuntu login.  I have assigned the Cd drive as primary boot device, and it still wont boot, even when I manually try to boot from CD, it just takes me to the Kubuntu login.  When I look at the CDrom drive in File Manager, its empty, even with the Bootable Disk in.  I read some forum answers that tell me to have acpi = off, but I cannot find that option in BIOs setup.  ive been using Kubuntu for a while, but I just use the GUI, so im not familiar with command line.
Ive been all over forums and I cant find an answer that fixes my issue, please help.

---

### Post by Gone fishing on 2013-04-18
As when you look at the CD it appears to be empty the most likely explanations are it is a bad CD - can you see files on the CD on another computer? or your CD drive isn't working does it work with other CDs?

If it is just the CD is bad you can download an image from the Ubuntu website and then burn an image to CD or even burn to a flash drive using the start up disk creator utility.

---

### Post by atomic drizzle on 2013-04-18
yeah, the CD drive works.  I can access the CD on another computer.  I attempted to use Dban to wipe my drive, but was unable to Boot from that disk, same problem not booting from CD drive.   I had assumed I burned it wrong, gave up and just went with loading a new OS without wiping the drive.

---

### Post by atomic drizzle on 2013-04-18
If I was to download and burn a new disk, Id be using K3B, do I just burn image?

---

### Post by Gone fishing on 2013-04-18
Yep K3B has a good tool for burning images but you could also use Startup Disk Creator or Unetbootin to create a bootable USB. Startup Disk Creator is built into Ubuntu just find it in the dash, sometimes it doesn't work but Unetbootin always works and is in the repositories you can also use it to make an Opensuse etc bootable USB.

---

### Post by atomic drizzle on 2013-04-18
ok, Ive established that my Cd drive is reading disks (a movie and a music CD) and that the boot disk itself works, but I cannot get my computer to recognize any bootable disks.  i have burned multiple OS(all KDE derivatives) to disks, all of which are recognized on my roomates laptop, but not my computer.  ive got a Compaq presario SR5262NX, with a pentium E2160, 2048MB and a 320GB harddrive.  Graphics card is a intel graphics media accelerator 950, CDrom is a lightscribe dvd/cd burner.   

In a possibly related note, im now getting an error when attempting to move files to Trash.  it keeps telling me that Trash is full, but it has no files in it and when I go into Properties and calculate the size, its 0 files, 0 bytes.

---

### Post by atomic drizzle on 2013-04-18
I also cannot boot into System Recovery.  What the eff?

---

### Post by Gone fishing on 2013-04-18
I'm wondering if part of the file system (/home partition?) is being mounted as read only. I can't understand why you can't boot from the CD (a BIOS setting?) I would make a boot usb drive and boot from that, it might be worth getting the system to run fsck on boot create a empty /forcefsck file and fsck should run on next boot.

---

