---
title: "System won't boot after USB install."
date: 2013-08-14
forum: New to Ubuntu
---

### Post by Macklorf on 2013-08-14
I have not yet used Ubuntu as an operating system, so I apologize in advance if my question seems really stupid. 
I did a clean install from a live USB made with Unetbootin. I can get the computer to boot from the usb, and Ubuntu is installed on my hard drive. (Samsung 830 128GB)
All my attempts to do a standard boot of Ubuntu result in a blank screen or a purple screen. I tried going into advanced options, and then selecting "Ubuntu with linux 3.8.0-19 generic" but the screen gets stuck on "loading initial ramdisk..."
When I boot from "Ubuntu with linux 3.8.0-19 generic (recovery mode)", the last few lines are like this


BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
EDD information not available
Freeing unused kernel memory: 784k freed
Write protecting the kernel text: 6252k
Write protecting the kernel read-only data: 2432k
MX-protecting the kernel data: 3988k
Failed to execute /init
Kernel panic - not syncing: No init found. Try passing init= option to kernel. see linux documentation/init.txt for guidance

I did a quick check of my hard drive with gparted when I booted from the live USB, and it seems to be in good working condition. I'm not completely ruling out the possibility of hard drive failure, but I can benchmark it and look at the files in it.
Here are my system specs:
Cpu: i5 4570
Motherboard: MSI b85m-E33
RAM: corsair 1x8GB
HD: Samsung 830 128GB ssd.

Thanks in advance for your input.

---

### Post by DuckHook on 2013-08-14
Hi Macklorf and welcome to Ubuntu and the forums.

On these forums, there is no such thing as a stupid question. Or rather, the only stupid question is the one not asked.

You likely have an incomplete install. The boot process cannot find your initrd.img so cannot create the initial ram disk. The result is a kernel panic. Since this is a virgin install, I assume that you have no critical data that you need to recover. Therefore, the best course of action is to download a new ISO, create another liveUSB and reinstall from scratch. Do not use your existing LiveUSB since it may be corrupted. Make sure you check the MD5 checksum on the new download so that you know it is good. The best way to get Ubuntu images is via torrent because it is self-checking and more reliable. Checksum the image on the LiveUSB too.

Installation instructions for Ubuntu (including how to do checksums) are [here]("https://help.ubuntu.com/community/Installation").
Bittorrent download site is [here]("http://www.ubuntu.com/download/alternative-downloads").

Good luck and let us know how it goes!

---

### Post by Macklorf on 2013-08-14
Thanks a lot! Everything works fine now.

---

### Post by DuckHook on 2013-08-14
happy Ubuntuing!

---

