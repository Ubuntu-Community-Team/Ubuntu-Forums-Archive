---
title: "Driver for Dell XPS L321X (Current BIOS A04)"
date: 2015-11-02
forum: New to Ubuntu
---

### Post by eddiefiggie on 2015-11-02
Does anyone have a repository I might find drivers for this laptop?  I suspect my internet dropping is connected to this issue.

Thanks!

---

### Post by DK1993 on 2015-11-02
Hi Eddie. Unfortunately I don't think what you seek exists (a repository that has all the drivers you need). However, there are other ways to get the result you want (better drivers). What seems to not be working is the Internet from what you wrote. Is it the WiFi or physical Ethernet connection that is giving you trouble?

And so we can point you in the right direction, can you please paste the results of this command from Terminal in the next post?

```
sudo lshw -short
```

---

### Post by eddiefiggie on 2015-11-02
.This issue is wifi...  I am runnign 14.04 LTS.  Randomly, no matter how close I am to the router, it will simply lose connection.  I then need to disable wireless, the re-enable it.  It will reconnect just fine.  I need to get this fixed.  I can't afford to me in the middle of work then experience this drop of connection.  :(



Here is the result of the aforementioned command:


```
 H/W path        Device     Class          Description
=====================================================
                           system         Dell System XPS L321X (System SKUNumbe
/0                         bus            Motherboard
/0/0                       processor      Intel(R) Core(TM) i5-2467M CPU @ 1.60G
/0/0/1                     memory         64KiB L1 cache
/0/0/2                     memory         256KiB L2 cache
/0/0/3                     memory         3MiB L3 cache
/0/4                       memory         4GiB System Memory
/0/4/0                     memory         2GiB DIMM DDR3 Synchronous 1333 MHz (0
/0/4/1                     memory         2GiB DIMM DDR3 Synchronous 1333 MHz (0
/0/c                       memory         128KiB BIOS
/0/100                     bridge         2nd Generation Core Processor Family D
/0/100/2                   display        2nd Generation Core Processor Family I
/0/100/16                  communication  6 Series/C200 Series Chipset Family ME
/0/100/1a                  bus            6 Series/C200 Series Chipset Family US
/0/100/1b                  multimedia     6 Series/C200 Series Chipset Family Hi
/0/100/1c                  bridge         6 Series/C200 Series Chipset Family PC
/0/100/1c.1                bridge         6 Series/C200 Series Chipset Family PC
/0/100/1c.1/0   wlan0      network        Centrino Advanced-N 6230 [Rainbow Peak
/0/100/1c.3                bridge         6 Series/C200 Series Chipset Family PC
/0/100/1c.3/0              bus            FL1009 USB 3.0 Host Controller
/0/100/1d                  bus            6 Series/C200 Series Chipset Family US
/0/100/1f                  bridge         QS67 Express Chipset Family LPC Contro
/0/100/1f.2                storage        6 Series/C200 Series Chipset Family 6 
/0/100/1f.3                bus            6 Series/C200 Series Chipset Family SM
/0/1            scsi0      storage        
/0/1/0.0.0      /dev/sda   disk           128GB LITEONIT LMT-128
/0/1/0.0.0/1    /dev/sda1  volume         243MiB Linux filesystem partition
/0/1/0.0.0/2    /dev/sda2  volume         119GiB Extended partition
/0/1/0.0.0/2/5  /dev/sda5  volume         119GiB Linux filesystem partition
/1                         power          DELL


```

---

### Post by Vladlenin5000 on 2015-11-02
I suggest you read and follow the troubleshooting instructions in [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) , the sticky at Networking & Wireless. Then post a new thread in that section with a proper title, description of the problem and the results of the script.

---

### Post by eddiefiggie on 2015-11-02
> **Vladlenin5000 said:**
> I suggest you read and follow the troubleshooting instructions in [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) , the sticky at Networking & Wireless. Then post a new thread in that section with a proper title, description of the problem and the results of the script.


Will do.  Thanks for pointing me that way.

---

