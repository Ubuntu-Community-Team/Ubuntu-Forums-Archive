---
title: "Problem With installation from a USB Device"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by Gollum234 on 2013-01-14
Hi! As the forum suggests I'm reaaaaally beginner with this.

I tried to install Ubuntu in my laptop from a USB device they gave us at the uni. I previously only had Win7 installed.

I followed the instructions after booting from the USB, and everything seemed fine. It made the partition borrowing 100Gb from the C: drive, no problem.
After completing the installation, I restarted but it started Win7 as usual, and never asked for other booting posibilities. 

I looked in Disk Managment in Win to see if the ubuntu partition was there, and it was, but it didn't say boot as C: After trying several times, I decided to eliminate that partition and reinstall, but when I tried to boot from the USB it say id something like "error device not found" and then left me with the grub rescue promt.

I went again to disk managment in win7 and used the unallocated space previously used by linux, to make the 2 partitions again although I did not format them. Now when I restart and try to boot from the USB the GNU GRUB starts and lets me choose to start Ubuntu, Ubuntu recovery, memtest and win 7. And Linux does boot, but only if the USB is connected, so I don't know where is it booting from, I'm so confused...

Now I only want to be able to boot from the USB to make a new installation of Ubuntu, How can I Accomplish that? And why didn't it work in the first time, any ideas?

Cheers!

---

### Post by hydn79 on 2013-01-14
To boot from USB you have to select that from BIOS.

This should be helpful:
[http://www.pendrivelinux.com/usb-bios-boot-options/](http://www.pendrivelinux.com/usb-bios-boot-options/)
[http://www.hiren.info/pages/bios-boot-cdrom](http://www.hiren.info/pages/bios-boot-cdrom)

---

### Post by NikTh on 2013-01-14
Hi ,
do you have a Live media of Ubuntu ? (CD/DVD/USB) 
If yes , then boot from there and follow the instructions here : [boot repair](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu) to repair your boot. 
Probably grub boot-loader installed on usb , but this is not correct. Grub should be installed on MBR , /dev/sda. 
Boot-Repair will do this job for you (automatically).
Thanks

---

### Post by Gollum234 on 2013-01-14
I think the problem is that one I was installing the boot menu was installed in the flash USB, and not in the HDD, because now I tried that USB on another computer and I have the same error.

Can my theory be possible? Is there a way to fix it? 

Thanks!

---

### Post by Gollum234 on 2013-01-14
Ha! I was writing my reply at the same time. 

Thanks NickTh!!! Solved

---

