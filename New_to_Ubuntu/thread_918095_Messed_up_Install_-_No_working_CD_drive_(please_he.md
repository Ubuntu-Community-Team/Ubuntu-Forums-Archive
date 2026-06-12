---
title: "Messed up Install - No working CD drive (please help)"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by mpcogjr on 2008-09-12
So I am obviously pretty new at all this and here is my quandary. 

I have a good install of Hardy on an old tower that I'm working on turning into a media server. I have a laptop with a bad cd rom drive in it that I was trying to install another copy of Hardy on so I could use it to eventually control the media center.

I had a copy of xp on it and I used Unetbootin since the cd rom doesn't work. Along the way, something went terribly wrong (probably my own doing). Now whenever I boot the laptop I get a good ol' "no operating system found" message.

So I guess my question is, can I find someway to reinstall linux over a network connection or floppy drive? 

I have a working computer running heron and my gaming computer running xp.

I'm hoping I'm not totally lost. Thank you very much in advance for any help. ;)

---

### Post by crazypenguin2008 on 2008-09-12
you could make a live boot usb flashdrive and install from that.

---

### Post by mpcogjr on 2008-09-12
> **crazypenguin2008 said:**
> you could make a live boot usb flashdrive and install from that.

Unfortunately I'm a bit behind the times in the flash drive department. All I have is a 256 meg drive I had back in college. If all else fails, I suppose I could go buy one, but I am still hoping for a more free solution.

---

### Post by crazypenguin2008 on 2008-09-12
you need atleast a 2GB flashdrive. i know a few people that have done it and it worked great. there are several linux disrtos that can be installed on a flash.

another option is to put the harddive in another notbook and do the install.

---

### Post by renfrew on 2008-09-12
If your laptop won't boot from cd or flash, does it have a PXE or netboot option in the bios?  you should be able to setup the tower as a PXE server and at least boot across your home network assuming you've got a home net...

 I haven't setup a PXE server myself but I've seen a bunch of HOW-TO's on google, none of which I have links to atm as I'm at work :(  I hate to give the ole "have you tried googling it?" kind of advice, but I'm not much more help atm ;)

-renfrew

---

### Post by mpcogjr on 2008-09-12
I believe I do have a netboot option in the BIOS, but I have no idea how to setup a PXE server.

Is that something I can do as an amateur Linux user?

I'll start looking on "the google" for options. If anyone knows of a link with some good beginner instructions I would be much obliged.

---

### Post by halitech on 2008-09-12
does the laptop have a workign floppy drive? (long shot I know but stranger things have happened). If it does and you have a working floppy in any of the other machines, you can download the debian floppies and use that to install over the network

---

### Post by mpcogjr on 2008-09-12
It actually does have a floppy drive. I'm setting up the disks now. Using the guide found here [https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies) to do it. I'll let you know how it goes.

---

### Post by halitech on 2008-09-12
let us know how it goes and if you need any help :)

---

### Post by mpcogjr on 2008-09-12
So I ran into a problem. I used rawrite to set up the floppies with the img files I got from [http://ftp.egr.msu.edu/debian/dists/sarge/main/installer-i386/current//images/floppy/](http://ftp.egr.msu.edu/debian/dists/sarge/main/installer-i386/current//images/floppy/) . I booted the laptop from the first floppy (boot.img). When it asks for the root floppy, the system gets stuck. The "_" on the command line blinks, but nothing happens when I hit enter or type. I tried it several times with the same results.

Am I doing something wrong or do I need to start looking into setting up a PXE server again?

---

### Post by renfrew on 2008-09-16
I can't help too much with the floppies as its been ages since I did a floppy install of Debian.  If you're at all interested in setting up a netboot/PXE/TFTP server on your tower there's a tutorial/walkthrough here: [https://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](https://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install).

---

