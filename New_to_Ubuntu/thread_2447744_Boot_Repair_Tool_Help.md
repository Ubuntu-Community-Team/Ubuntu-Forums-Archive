---
title: "Boot Repair Tool Help"
date: 2020-07-24
forum: New to Ubuntu
---

### Post by frostythedev on 2020-07-24
Paste: [http://paste.ubuntu.com/p/FrXfbwVPf4/](http://paste.ubuntu.com/p/FrXfbwVPf4/)

Hey guys, long story short I had a dual boot of Ubuntu and Windows 10 on an little bit of an old Laptop from 2015 which I was using as a server, after a reboot it seems as if my Windows 10 partion has been completely deleted and I have do idea why, it boots straight into Grub Rescue no such partition and I've tried the methods including 

1. [ls] and setting the boot and prefix to each entry from [ls] but it produces an unknown filesystem error each time I try to insmod normal after each reset, any assistance would be appreciated as I'm trying to save the server if at least only to get the ~100gb of files on it.

---

### Post by oldfred on 2020-07-24
Your sda3 seems to be first issue.
Windows 10 on updates likes to turn fast start up back on which sets hibernation flags and that flag prevents Linux NTFS driver from mounting & seeing all the NTFS partitions.
And with BIOS boot grub will not then boot Windows. 
You have to temporarily restore a Windows boot loader to MBR using your Windows repair disk & its repair console and turn off fast start up.
Then restore grub. But if Linux partition also corrupted it needs repairs. At minimum fsck or e2fsck.

And if you have all that corruption, so you have a failing or failed hard drive?
In Disks on live installer and upper right corner is Smart Status. It can run lots of tests, but all I really know is whether it reports drive is good or failing.

Or install terminal version:
What a Failing HDD looks like
[https://ubuntuforums.org/showthread.php?t=2446974](https://ubuntuforums.org/showthread.php?t=2446974)
gsmartcontrol
sudo apt install smartmontools
[https://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/](https://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/)

---

### Post by frostythedev on 2020-07-25
I'll have a look at doing that now, I'm unsure if a Windows update may have been the cause but I will look into it before day's end and report what I find, thank you.

---

