---
title: "Ubuntu 8.04 2.6.24-19-server error 19: Linux kernal..."
date: 2008-10-22
forum: New to Ubuntu
---

### Post by AnotherGoodIdea on 2008-10-22
System:
Toshiba 4005CDS, Pentium II, 233Mhz, 160 Gig Ram, 4.1 Gig HD
BIOS does not support USB boot. Boot order CD-Rom,FFD,HDD
Rosewill USB 2.0 Hi-Speed CardBus Adapter (4 port), two TRENDnet TU-ET100C (USB to Ethernet), SanDisk Cruzer Micro 4 GB,Ubuntu Server 8.04

History:
Initially established as a router, [http://ubuntuforums.org/showthread.php?t=926001](http://ubuntuforums.org/showthread.php?t=926001). Well documented and enjoyed the project. A useful purpose for an old laptop. Could use more info. on Linux Firewall and Webmin setup (documentation). That's another issue.

Current HD is noisy (original)and I would like to run from a USB drive. I realize the Cruzer is slow but that is easily taken care of. Need to create a Boot CD that will load the kernel. Followed the instructions at [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB) ...sort of. Used an Ubuntu 8.04 Server CD for the installs. Worked from the HD and USB Drive.

Results:
Error 19: Linux kernel must be loaded before initrd

[https://wiki.ubuntu.com/Booting](https://wiki.ubuntu.com/Booting)
"The initrd is an "initial ram disk" and contains a file system with programs and modules that enables the kernel to find the root partition. **When the kernel boots, the initrd is already loaded into memory by the boot loader**, so that the kernel doesn't have to think about disk access in the first place. The kernel launches the init script inside the initrd file system, which loads hardware drivers and finds the root partition."

I'm lost with that explanation.

I need to load the kernel from CD and I haven't been able to accomplish this after many tries. Can any one explain what I'm missing here?

Thanks in advance

---

### Post by LowSky on 2008-10-22
try this
[http://zerlinna.blogweb.de/archives/52-Dual-boot-on-external-USB-Drive-with-a-BootCD-with-Bios-not-supporting-boot-from-external-device.html](http://zerlinna.blogweb.de/archives/52-Dual-boot-on-external-USB-Drive-with-a-BootCD-with-Bios-not-supporting-boot-from-external-device.html)

or this
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

---

### Post by AnotherGoodIdea on 2008-10-23
LowSky,
[http://zerlinna.blogweb.de/archives/52-Dual-boot-on-external-USB-Drive-with-a-BootCD-with-Bios-not-supporting-boot-from-external-device.html](http://zerlinna.blogweb.de/archives/52-Dual-boot-on-external-USB-Drive-with-a-BootCD-with-Bios-not-supporting-boot-from-external-device.html)

A HD must be in the computer to boot from the CD.

"Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev"

"Alert! /dev/sda1 Does not exist. Dropping to shell"

"Busy Box v1.1.3"

"(initramfs)_"

I started with clean installs for the HD and USB Drive. USB Drive was loaded without a HD in the computer.

The "alert" makes perfect sense. The USB Drive never came on-line so there was no /dev/sda1.

Enough must be done to bring the USB Drive on-line.

Moving on to your next link. I'll give it one more try.

---

### Post by AnotherGoodIdea on 2008-10-23
LowSky,
The problem is the Rosewill USB 2.0 Hi-Speed CardBus Adapter. Just after I posted last it hit me, try the USB 1.0 port. The system booted and I logged in! I guess in got the instructions translated correctly on the first try.

The port speed will be awful. USB 2.0 is much faster and this drive just might do the trick [http://www.newegg.com/Product/Product.aspx?Item=N82E16820134615](http://www.newegg.com/Product/Product.aspx?Item=N82E16820134615) Anyway, I was on the right track. The cardbus must come up first and then the USB drive. Is there any thing we can do about this?

---

### Post by AnotherGoodIdea on 2008-10-23
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

Step #7 failed
( STEP 7 ) Type in these lines before we start editing out files ...

mount -tproc proc /target/proc <enter>
chroot /target <enter>
su <enter>

"Mount: Mounting proc on /target/proc failed. Device or resource busy."

I guessed that Cntl+Alt+F1 would let me exit the terminal window...

Reboot system... Error loading Grub. Rescue, unable to reinstall Grub.

My intention was to reboot and finish the instructions with methods I already know.

Looks like I'm starting over...again.

Any other ideas?

---

