---
title: "installing ubuntu without cd on older machine"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by shortridge11 on 2008-10-15
I'm running 8.04 desktop on my home file server.  The install seems to have become corrupted, and i think a fresh reinstall is in order.  Unfortunatly there isn't a cd drive in my house i could use to install it.  Is it possible to mount the install disc as an image and try to reinstall if from that?  This machine is too old to boot from a usb flash drive.  I'm just looking for a way to reinstall without having to hunt down a cd drive.  Any thoughts?

---

### Post by Duck2006 on 2008-10-15
From [www.pendrivelinux.com](www.pendrivelinux.com) You may be able to boot the usb drive from a 3.5 fdd.

[http://www.pendrivelinux.com/2007/11/21/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/2007/11/21/use-a-floppy-to-boot-usb-pendrive-linux/)

---

### Post by LowSky on 2008-10-15
he jsut said he can't use a Flashdrive..lol 

try this,
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by jerome1232 on 2008-10-15
Why not borrow the optical drive from your main unit? That's what I ended up doing on my older machine (it couldn't boot via pxe or usb and I have no floppy drives)

---

### Post by philinux on 2008-10-15
This might be an option.

[http://www.linux.com/feature/124684](http://www.linux.com/feature/124684)

---

### Post by shortridge11 on 2008-10-15
i'm really trying to avoid hunting down an optical drive, and usb installations are not an option.  If there's an easy way to do it over a network, such as from my laptop (ubuntu 8.04) to the server, then that would be ideal.

---

### Post by Duck2006 on 2008-10-15
[http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/](http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/)

It not may be one of these will help.

[http://www.google.com/cse?cx=012285703143635244993%3Ai9yr8qlpb18&q=installing+ubuntu+from+a+network+install&sa=Search](http://www.google.com/cse?cx=012285703143635244993%3Ai9yr8qlpb18&q=installing+ubuntu+from+a+network+install&sa=Search)

---

### Post by C.S.Cameron on 2008-10-15
Is cloning the system from another hard drive an option?

---

### Post by Kellemora on 2008-10-15
Hi SR

Can you pop the case on your computer easily enough?

I ask because it's a whole lot quicker to just mirror a hard drive by chunking it into an existing computer or almost as fast over a LAN.

I have some older computers with nothing bootable in them, meaning no CDs and even if I had a cd it wouldn't be bootable.  But if you have an old floppy drive laying around and an old win98 boot disk, you can make the network active and if the drive is formatted perhaps see it from your Ubuntu machine.  But you need a lot of luck.

For me it's just easier to stick the hard drive in a different computer and either reload Ubuntu to that drive by making it the primary, or doing a mirror to it as a slave from the primary.

Then when you plop it in the other computer, it will readjust the hardware for you by itself, usually.  Or use generic options.  Most of the older hardware seems to be supported, so I've not had much of a problem.

That's how I learned Linux and Ubuntu without messing up my working system.  Then I got brave and my main computers are all triple boot now.

Good Luck!

TTUL
Gary

---

### Post by louieb on 2008-10-15
Not that easy but:
[HOWTO Boot from any .iso file without needing a working CD-ROM]("http://ubuntuforums.org/showthread.php?t=666267") 
and should work for other versions
[HOWTO: Install Edgy 6.10 from an .iso file - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=316093")

---

