---
title: "No boot disk detected. Need help diagnosing"
date: 2018-11-24
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2018-11-24
Hardware: HP Pavilion P7-1000 with 8GB RAM

I am upgrading my wife's Ubuntu MATE 16.04 to 18.04.1. Just to run a "trial" install, I disconnected the existing SSD, connected a 500GB HDD and did a clean install of 18.04.1 from a bootable USB stick using the "Use the entire disk" option. Everything seemed to work just fine.

Have now disconnected the HDD, reconnected the SSD, and got this text message:

> For Atheros PCIE Ethernet Controller v2.1.0.9 (08/12/11)
Check cable connection
PXE-MOF:exiting Intel PXE ROM
ERROR: no boot disk has been detected or the disk has failed

There was another unused SATA cable which I tried. Same result. Got three other "thought to be good" SATA cables and tried each of these. Same result. Pretty sure it isn't the cables at this point.

Then tried to reconnect the HDD. Got the same result. Seems unlikely that both the SSD and the HDD, both of which were working perfectly when unplugged, had gone toes up.

So I managed to intercept the boot process and got a menu which included a choose boot order (I think it was) option, which I went into, selected Ubuntu, and it successfully booted into the HDD install. So the cables were indeed OK (at least this one was) .

So thinking I was clear to do a clean install of 18.04.1 over the existing 16.04, I tried booting up with the USB to install, it gave me a warning that the install needed at least 8GB, and only 4 (i.e., my USB) was available.

So I started over trying to get the original SSD to boot up under 16.04. No luck. Then the HDD, and now I can't get it to boot. When I hit ESC bringing up PLEASE SELECT BOOT DEVICE, the HDD did show up as SATA1 (listed as Legacy, not UEFI), whereas the same SATA cable on the SSD did not bring up a SATA1.

I am massively confused and frustrated. Seems 1 step forwards, 2 steps backward. I have read that this is somehow the computer trying to do a remote boot over the network, but I don't even know what that means.

I also have a feeling that there is an underlying UEFI/BIOS issue afoot.

Help please. What is going on, and how do I fix it? Thanks.

---

### Post by oldrocker99 on 2018-11-24
Try this: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair).

---

### Post by Autodave on 2018-11-24
If you have always had the drive(s) plugged into SATA1, try moving it to SATA2 and see if it works.  You may have a bad connection.

---

### Post by Odyssey1942 on 2018-11-24
I had been trying to boot by selecting devices. Went into boot order, re-ordered everything properly, and it booted from the USB stick as desired, found the SSD and I am installing over a previous partition. If that goes well, will reformat the entire and repartition to start fresh. 

Thanks to both.

---

### Post by oldfred on 2018-11-24
UEFI forgets UEFI entries for drives that are disconnnected.
You can use efibootmgr from a live isntaller to recreate new entries and delete old entries.
See
man efibootmgr

       Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B
Delete Ubuntu
[http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

Some examples, but you have to adjust parameters to match your system.
       
 sudo efibootmgr -c -L "UEFI Hard drive" -l "\EFI\Boot\bootx64.efi"
sudo efibootmgr -c -w -L ubuntu -l "\EFI\ubuntu\shimx64.efi"  -d /dev/sda -p 1
sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/sdX -p Y
sdX is drive, Y is efi partition , if sda2 for example

---

