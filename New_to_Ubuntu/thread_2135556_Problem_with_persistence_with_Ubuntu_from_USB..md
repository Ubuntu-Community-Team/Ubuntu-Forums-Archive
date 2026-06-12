---
title: "Problem with persistence with Ubuntu from USB."
date: 2013-04-14
forum: New to Ubuntu
---

### Post by tuc17831 on 2013-04-14
[COLOR=#000000][FONT=Verdana]So this has been troubling me for a few days. I want to use Ubuntu from a live USB with persistence but I can ever get anything to actually persist when I boot up again. I have tried a combination of things. I have tried Ubuntu 12.04 and 12.10. I tried with Unetbootin and Universal USB Installer each time setting the persistence around 2GB. I wanted to use it for my Windows 8 laptop so I was using the 64bit version as Ubuntu suggested. I am able to boot from the USB and use Ubuntu fine. But when I reboot everything is gone. I tried setting up administrator account hoping everything would save to that. But I reboot it doesn't even recognize my account name or password. I then tried this on another laptop with [/FONT][/COLOR][Windows 7]("http://www.amazon.com/Windows-Premium-64bit-System-Builder/dp/B004Q0PT3I/ref=sr_1_2?ie=UTF8&qid=1353684038&sr=8-2&keywords=windows+7")[COLOR=#000000][FONT=Verdana][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][/FONT][/COLOR][COLOR=#000000][FONT=Verdana] and persistence still does not work. I do not know what I am doing wrong. Any idea of what could be the problem would be greatly appreciated. Thanks![/FONT][/COLOR]

---

### Post by monkeybrain2012 on 2013-04-14
I have made may live usbs with persistence but always in Linux. If you create you live usb in Windows, try this (I have never used it but looks sophisticated)

[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

---

### Post by C.S.Cameron on 2013-04-14
Do you end up with a file named casper-rw on the USB?
It is the persistence file and has a 4GB limit.
if so check syslinux.cfg, it should contain the word persistent thus:

append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent

You can also make a persistent USB using casper-rw partitions:

This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1GB FAT32 partition, (on the left side of the bar).
Created a 2GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext2 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

---

### Post by squakie on 2013-04-15
Also, what size is the USB media being used?  My own experience has been that when I use too small of a USB device, having selected persistence makes no difference and isn't created.  It seems it calculates how much space the Ubuntu installation is going to take and if that plus the size of persistence is larger than the media it just doesn't create the persistence "file".  Just my experience.

---

### Post by zemega on 2013-04-15
Hi, this is my solution to booting Ubuntu from USB. But this is not a Live version, but a full install on a USB. I used 2 USB drive, one to load the Unetbootin and the ISO. The second one is where I full install Ubuntu 12.04. I used 16GB, because I don't need much programs, only basic one. I do suggest you use 32GB one. The solution is you boot using the unetbootin. When you got to insed Ubuntu, insert the USB drive you want to install Ubuntu, and install it into there. You can do some selection like partioning and swap size, but I don't think I would need to, and I didn't. After that, you can just use that dive to start Ubuntu practically anywhere else. Even old computer that Ubuntu 12.04 refuse to install can boot into 12.04 from the USB drive.

Now, let me share you my problem. I used a thin type USB drive, the one with no  connector casing(?). So wometimes when I accidentally budged the USB drive, the connection is lost, Ubuntu 12.04 sort of hang, and you have to restart your computer. I do suggest that you find USB drive that is not the thin type. better yet, something like this [http://www.sandisk.com/products/usb/drives/cruzer-fit/](http://www.sandisk.com/products/usb/drives/cruzer-fit/) .It fits right into the USB port, and stay there safely.

Problem No 2. Sometimes the system sort of freeze for a bit, not the whole Ubuntu, but the appllications. But this is booting from USB 1.0 port. If you use USB 2.0 port, I believe this will be lesser. Better yet, use USB 3.0 drive and port, that will be faster than normal HDD I believe.

---

