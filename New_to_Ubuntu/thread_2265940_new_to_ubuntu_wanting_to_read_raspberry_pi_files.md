---
title: "new to ubuntu wanting to read raspberry pi files"
date: 2015-02-18
forum: New to Ubuntu
---

### Post by davegoodhand46 on 2015-02-18
Evening all, 

I'm looking to be able to read some files from my raspberry pi 2 on a microSD card (to increase the cache) and was advised to use Ubuntu, I'm using windows 8, and have managed to download  the LiLi live usb creator, I've followed all that through and installed (ubuntu-14.10-desktop-i386) I now have a USB 3.0 memory stick with Virtalize_this_key, VirtualBox & a folder called Portable VirtualBox which seems to be as it should be according to the guide I'm using.

 From here is where I am bit stumped I've opened the Virtalize_this_key file and clicked the green show arrow in Virtualbox it seem to me like its loading but I then get this error and I'm note sure how to fix it.

[IMG]http://i59.tinypic.com/dwzb4z.png[/IMG]

If any could offer any help that would be great thanks

---

### Post by TheFu on 2015-02-18
Seems like this is a long way to read some files.

This is how I'd do it:
* On the rpi, enable the ssh-server.
* From the Windows machine, use putty to ssh into the rpi by using the IP and userid on the rpi for login.
* Look at the files.

If those files aren't text or need some special program to view, use sftp/winscp to pull them back to Windows and a program on that OS to view.

Of course, if you actually want to run a virtual machine, then that is fine too. I don't see why any flash memory is needed to run a VM. Just point the VM you create for this to an install ISO file and go. You can either run that way off a liveCD (not saving anything) or have a virtual HDD - 10-15G is fine - and install a nice Ubuntu inside the virtual hard drive. The virtualization subforum is a better place to ask that question. Might be worth watching a few youtube videos on setting up VMs with the tool you decide to use. I've never heard of virtualize-this-key ... but I'm an old guy with virtualization - started using it in the 90s.  We use VMs here for almost everything.  I'm typing into a remote desktop VM right now.

Don't quite understand how you plan to modify the file system on an SD without booting a Linux install onto real hardware. Any other way would be too hard, I'd think. Virtualized Linux is NOT the way I'd attack that issue.  I'd boot off any liveCD from any Linux desktop distro, plug in the rpi SD card and run gparted on it. Just be aware that is a good way to loose data, so if you care, backup the data first.

---

### Post by davegoodhand46 on 2015-02-18
Many thanks, shall give this a go tomorrow

---

### Post by mastablasta on 2015-02-19
if you are still going the virtual box way - you came at it in a bit of a strange way. it could be the USB key you used is too small. however as TheFu mentioned you can just use that USB key to boot into limnux and then use gparted to change your partitions on SD card. Linux boots into live session (the "Try it" option) that will load into RAM and by default will not touch your hard disk.

if you want to access the SD card via virtualbox you might find this guide usefull: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

a few things to note here - 
- ubuntu has 64bit image (AMD64) by default now. this means you need to enable virtualisation in BIOS/UEFI (VT-X or something like that) in order to run it in virtualbox. there should be a 32 bit image (x86) available. if not, I am sure Lubuntu or Xubutnu have them.
- you might need guest additions to mount the SD card in virtualbox
- if you never used virtualbox before, it is easy to use but one has to grasp they are dealing with a virtual PC. so stuff need to be preset well in order for it to run well.

so the first option of using live media is way easier. virtual box will work just as well, but you might need to invest more time in it.

---

### Post by Bucky Ball on 2015-02-19
Putty, as suggested previously. That's all I ever used to access files on the RPi (and now the Odroid).

---

### Post by TheFu on 2015-02-19
**In the OP you say "increase the cache" ... do you mean increase the size for the swap partition?  **

That would mean using gparted (the easiest way) - sure you can do it other ways, but for a point-n-click person, gparted is very useful.  Heck, I'm not a p-n-c person, but would go out of my way to modify partitions using gparted because it is visual and prevents me from making mistakes that could wipe an entire SD card.

---

