---
title: "Install (not boot) Ubuntu on USB stick"
date: 2015-02-23
forum: New to Ubuntu
---

### Post by Oliver_Davey on 2015-02-23
Hi all. I tried searching but the result came up with instructions to boot rather than install. Can anyone help me with this? I would like to isolate Ubuntu from my system all together and have it running on a flash drive only (full installation). Thanks.

---

### Post by Bucky Ball on 2015-02-23
You are creating the USB in Windows? Try [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"). That can create a persistence install to USB, which is what you're after. Good luck. ;)

PS: You need a reasonable sized USB for this. 16Gb would be good, but you might get away with 8Gb, depending on where you are looking to store data.

---

### Post by Oliver_Davey on 2015-02-23
> **Bucky Ball said:**
> You are creating the USB in Windows? Try [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"). That can create a persistence install to USB, which is what you're after. Good luck. ;)

PS: You need a reasonable sized USB for this. 16Gb would be good, but you might get away with 8Gb, depending on where you are looking to store data.Thanks Bucky! I didn't think about installing from within Windows - that definitely simplifies things. I'll probably go with a 64gb drive just incase the OS grows on me. :) Much appreciate the help.

---

### Post by Bucky Ball on 2015-02-23
64Gb would be ideal. USB install won't be as fast as a hard drive install, but good way to try things out (you can also boot from the Live media, USB or DVD and choose 'Try Ubuntu' to try it out). Another thing to remember is that USB has only so many read/writes. They won't last as long as a hard drive so you would need to keep back ups if you do a persistence install to USB and decide to use that method, just in case it suddenly dies. Good luck however you choose to go and post if you have issues.

---

### Post by sudodus on 2015-02-23
A persistent live system is a good option as suggested by *Bucky Ball*. An installed system that you asked for is also a good option. Both kinds of systems have their advantages and disadvantages, and in both cases it is a good idea to use a fast USB 3 pendrive. You install to a pendrive in the same way as you install into an internal drive. The only differences are to select another target drive and that you must also make sure that the bootloader will be installed into the correct drive, which is easy if you remove the internal drive.

See the following links
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

[Pendrive speed test]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by kurt18947 on 2015-02-23
> **sudodus said:**
> A persistent live system is a good option as suggested by *Bucky Ball*. An installed system that you asked for is also a good option. Both kinds of systems have their advantages and disadvantages, and in both cases it is a good idea to use a fast USB 3 pendrive. You install to a pendrive in the same way as you install into an internal drive. The only differences are to select another target drive and that you must also make sure that the bootloader will be installed into the correct drive, which is easy if you remove the internal drive.

See the following links
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

[Pendrive speed test]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

This is what I think Oliver_Davey wants.  The safest IMO is, after creating a live DVD/USB disconnect the internal hard drive(s) then boot from the live device. That way nothing will be overwritten. My machines have USB2 only so I'm a little familiar with the speed issues. Doing the inital install can take quite some time -  perhaps 30 minutes+  because USB2 writes can be pretty slow. Once the system is installed on the flash drive, writes are less frequent.  Once a machines boot I don't find the speed *that* much different than a hard drive. I do pretty simple stuff with flash drive installs. I'm sure if I were doing something demanding like video editing I'd find USB flash drive installs pretty frustrating but basic functions - web surfing, office stuff etc. is usable. One big advantage for a 'real' install over a live install with persistence is that 'real' installs can be updated, live USB with persistence in my experience will eventually break after updating. I can also install proprietary printer drivers, video drivers etc. with no issues. 

I would not be surprised if higher cost/better performing USB flash drives would provide a better experience but I've used generic USB2 flash drives (Microcenter brand) and been satisfied. I do remove any factory partitions using Gparted then format as ext4. I believe there's a way to disable journaling on an ext4 partition but I haven't explored it. A possible advantage of disabling journaling would be to reduce the number of write operations, the operation that 'wears' flash cells. One could also use an ext2 file system which doesn't use a journal. I'm under the impression that ext4 is faster/more efficient than ext2. I don't really know though. As long as you are careful to not overwrite what currently exists, using flash drives is a pretty safe way to experiment and learn Ubuntu.

---

