---
title: "Ubuntu Precise 12.04 - Speedtouch 330, PPPoE"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by mitescugeorgedan on 2012-06-12
Hello there. Until about 2 days ago, I've had Ubuntu 10, and my internet was working perfectly. Since I've upgraded to 12.04, I'm trying to find ways to get my Speedtouch 330 working. I've tried from SL-modem to this link over here [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch]("http://ubuntuforums.org/%3Chere%3Ehttps://help.ubuntu.com/community/UsbAdslModem/SpeedTouch")    . I haven't found UbuDSL anywhere to download, the links are broken. Any solution is appreciated. :)

---

### Post by sanderj on 2012-06-12
Well .. [https://sourceforge.net/projects/ubudsl/](https://sourceforge.net/projects/ubudsl/)

But my real advice: get a second hand ADSL ethernet modem/router for 20 Euro ... it will save you a lot of time.

---

### Post by mitescugeorgedan on 2012-06-13
I've tried to compile it, it gives error, and they're not related to dependencies.

I'm starting to reconsider the second hand modem option.

---

### Post by tell me why on 2012-09-25
I have had a similar problem and installing [COLOR=Green][https://launchpad.net/ustouch/trunk/0.1/+download/speedtch330-0.1.tar.gz](https://launchpad.net/ustouch/trunk/0.1/+download/speedtch330-0.1.tar.gz)[/COLOR] resolved it,
now I am trying to share this conection with another pc (winxp) but I cannot yet. There are something wrong
with my network manager that I cannot figure out.

If you only need the ubuntu machine maybe this can help

But, please read this log before your attempt:
> 
USpeedTouch - Easy installation of SpeedTouch 330 USB Modems
bY Marco Rodrigues - [http://Marco.Tondela.org](http://Marco.Tondela.org)

1. Purple Modem
2. Gray Modem
0. Exit

Choose option: 2
dpkg: warning: downgrading br2684ctl from 1:2.5.1-1.2build1 to 20040226-1.
(Reading database ... 158390 files and directories currently installed.)
Preparing to replace br2684ctl 1:2.5.1-1.2build1 (using .../br2684ctl_20040226-1_i386.deb) ...
Unpacking replacement br2684ctl ...
Setting up br2684ctl (20040226-1) ...
Processing triggers for man-db ...
[COLOR=Red]dpkg: warning: downgrading libatm1 from 1:2.5.1-1.2build1 to 2.4.1-17.1build1.
(Reading database ... 158391 files and directories currently installed.)
Preparing to replace libatm1 1:2.5.1-1.2build1 (using .../libatm1_2.4.1-17.1build1_i386.deb) ...[/COLOR]
Unpacking replacement libatm1 ...
Setting up libatm1 (2.4.1-17.1build1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
** Boot block from firmware/mgray.eni:
   CRC: 0x69636579
   Length: 935
** Firmware block from firmware/mgray.eni:
   CRC: 0x0223733c
   Length: 775509

Installing firmware files in the system...

Enter your username (e.g: [EMAIL="sn000000@simplesnet.pt"]sn000000@simplesnet.pt[/EMAIL]): 


---

