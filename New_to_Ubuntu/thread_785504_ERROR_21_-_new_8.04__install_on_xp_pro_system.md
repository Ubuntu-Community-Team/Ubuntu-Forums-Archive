---
title: "ERROR 21 - new 8.04  install on xp pro system"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by onebyte on 2008-05-07
I need some serious help. AMD64/ XP 32 Pro System will not boot.  Error 21 message.  

I suspect overwritten MBR in win xp 32 pro that I've been using for about two years on this athlon 64 computer.  I was doing a lot of file shifting and moving to get a free disk to try ubuntu, and lost my acronis ti 11 backup somehow, so I can't use that option.

[COLOR="Blue"]I think what I need most is instructions of how to use the xp 64 install disk to recreate the mbr.[/COLOR]  But I need to check to see what actually happened.  I think I tried doing the install to the wrong disk.  I was trying out a new WD MyBook usb disk, and had saved my backups to it, but I think I chose the wrong install locations (and maybe method too) and did my install to the 
wd removable usb drive.

My rig is a lttle complex:

MSI Neo-Platinum SLI MB with AMD 64 Athlon 3200+ CPU, 2 GB 400 mhz memory
twin sata 80 gb hitachi deskstars using a sata raid 0 stripe from bios divided into 3 logical partitions. c,d,e with xp 32 pro on ntfs primary c, d extended, and e formatted for linux 3. (Using Acronis Disk Director 10)
hitachi 160 gb sata raid single stripe I was using for storage and backups, until yesterday when I decided to try putting the ubuntu thare (if I couldn't get it working on the linux partition on the raid 0 stripe.
dvd/cd drive 
floppu 3.5
USB removable drive 400 gb 
... with possibly corrupted iso image backups on it.  (I think that's where my new ubuntu install went.  I had great difficulty figuring out what drives ubintu wanter to use, and just went with the default.  I don't think I should have done that!  ;-))

I'm going to try plugging the usb drive into my wife's computer (that I'm one now) and see what I can find on it.  Then, depending on what's there, or perhaps regardless of it, I I need to see if I can get my computer to boot by fixing the mbr.  I've done an xp repair install, but it's been years ago, so I will need a walkthru.

Oh, yes, I have a new computer build that I was going to install ubuntu, win xp 32 and 64 amd multiboot them.  I have twin sata disks that I was thinking about doing a raid 0 setup on, but maybe I'll just skip that to keep things simpler during the multiboot tryout.

If anyone can help with some solutions or suggestions for getting back up and running, I'd be grateful.    

1.  Will ubuntu install on a dual sata raid 0 logical partition setup with xp pro already on it?  If so where can I find out how best to do that?

2 . How to get booted up or mbr fixed?

3.  Best way for new computer multiboot setup?

[2 is the highest priority now.]

I'll check back soon.

Thanks

Onebyte

---

### Post by bumanie on 2008-05-07
Assuming you have an xp disk, boot with that and go into recovery console. Choose the number your Win OS is designated (most likely 1) and hit enter. Answer the questions (Admin. password etc)
Then type FIXBOOT --> enter and answer yes --> enter. The FIXMBR --> enter answer yes --> enter Then exit --> enter
(I think they are the steps and I think to reboot xp one puts in exit rather than reboot)

---

### Post by onebyte on 2008-05-07
Thanks Bumanie,  I'll give that a try.

---

### Post by jimv on 2008-05-07
What did you do to make you think that your mbr got overwritten?

---

### Post by onebyte on 2008-05-07
> **jimv said:**
> What did you do to make you think that your mbr got overwritten?

Uhhh... The system won't boot?  It halts on a black screen with grub error 21?  It won't boot into either windows or ubuntu?  It hangs almost immediately after starting to boot from the HD?

I was installing U8.04 on an existing xp working system that I had been using for years.  I had just plugged in a removable Mybook usb drive to back stuff up to, and left it on during the install.  That's where the default chose to back up to, and I didn't realize what it was doing until too late.

I figured it would be better to let the install finish rather than interrupt it midstream.  That may have been a mistake.  It might have been able to undo what had been done.  I don't know.

I guess I should have done more research on installing to a raid 0 configuration, but I've been using it for about two years, and never had a problem installing anything on it, just as you would a single disk.

Live and learn.

---

### Post by jimv on 2008-05-07
Oops, I didn't notice that you tried to install Ubuntu already.

I think you could just install Ubuntu again onto the RAID this time (with the USB drive unplugged) and that will fix grub.

When Grub loads, it looks for a file in Ubuntu under /boot/grub/menu.list that contains information about what OS's are available.  Since it put that on the USB disk, I don't think it can see it.  Reinstalling Ubuntu will reinstall Grub, and Grub will then be able to find the menu.list file.

---

### Post by Zralou on 2008-05-07
Try plugging the USB drive back in, unplugging it will have confused grub.

Sara Lou

---

### Post by Heliman5 on 2008-10-15
oops!

---

