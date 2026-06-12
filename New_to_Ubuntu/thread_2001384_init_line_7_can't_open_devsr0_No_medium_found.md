---
title: "/init: line 7: can't open /dev/sr0: No medium found"
date: 2012-06-10
forum: New to Ubuntu
---

### Post by dfrayer on 2012-06-10
Trying to install 12.04 LTS amd64 with my own kernel.

/init: line 7: can't open /dev/sda: No medium found
/init: line 7: can't open /dev/sr0: No medium found


I think the problem is the actual CD is in /dev/sr1.  I can mount manually it from initramfs.  I could probably probe the modules in a different order and the virtual cdrom would be /dev/sr1 but then I wouldn't be able to install from the virtual cdrom.  I'm guessing this would be an easy script fix but I am relatively new to this.  I didn't have this problem in 10.04.3 with a different kernel - but probably because the virtual cdrom did not show up first.


$ lsscsi
[0:0:0:0]    cd/dvd  AMI      Virtual CDROM    1.00  /dev/sr0
[0:0:0:1]    disk    AMI      Virtual Floppy   1.00  /dev/sda
[1:0:0:0]    cd/dvd  MATSHITA DVD-RAM UJ8A0AS  1.00  /dev/sr1
[1:0:1:0]    disk    SEAGATE  ST9300603SS      0006  -       
[1:0:2:0]    disk    SEAGATE  ST9300603SS      0006  -       
[1:1:1:0]    disk    LSILOGIC Logical Volume   3000  /dev/sdb

---

