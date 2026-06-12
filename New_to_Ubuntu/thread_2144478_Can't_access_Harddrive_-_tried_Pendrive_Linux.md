---
title: "Can't access Harddrive - tried Pendrive Linux"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by affeloco on 2013-05-12
Hello everybody,
i'm using Kubuntu on a Sony Vaio 10" Laptop (VPCW12S1E) and cant boot from the Hard-disk anymore.


Firstly, Kubuntu was showing from day to day more problems. Reacting really slow, almost freezing. After a restart it was mostly better, but then i got a message, that theres a harddisk problem and it would run a scan (reminded me of the windows disk scan, after the pc crashed,so i didnt pay much attention). after that it was fine. next day, same thing. i restarted and then got the following grub-message:
*error: hd0 read error.*
*grub rescue:*
Some Commands i found by searching were working, like "ls" but a lot not - and im really far from understanding this command-line thing - as this pc is just borrowed for travelling, but the owner doesnt know more.


So. From the Forum i found out, that i would learn more with running an Os from a stick. I downloaded the [Universal USB Installer ]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") and Kubuntu 13.04.
Now i am at the following point. It does take a looong time (more than 20min) to boot and inbetween this time there come several messages:
firstly it shows shortly some lines of which i just could read "timeout", than comes a kubuntu logo, which stays for some time until i type a key and it switches to this:
*I/O Error*
*Not a typewriter (3x) *
*unmount: cant unmount /cdrom: Device or resource busy*
*I/O Error*
*Not a typewriter (x2)*
*unmount: cant unmount /cdrom: Device or resource busy*
*I/O Error*
*Not a typewriter (3x)*

*Generating locales...*
*en_US.UTF-8...up-to-date*
*Generation complete.*
*timeout: killing *
and then starting a process, from which i just could rembember:
*buffer I/o error on device sda1*
*timeout: killing sbin/blkid - o udev- dev/sda*

The Stick provides a Help Option, which i ran and which was processing some data and showing a Lot and Lot of errors - so, i fear that the harddisk really is physically damaged. But this option doesnt show up anymore, now i can choose between trying and installing kubuntu.
Arriving in Kubuntu after a booting procedure of one hour it doesnt show me the hard-drive.
Regarding to this thread ([https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)) i installed Testdisk and Gpart.
Gpart gave me two read errors and "short read near sector" and seemed to stop.
Testdisk actually ran, but confused me - since i have to decide if and how (intel, linux) the disk is partitioned - it just shows me two values ca. 280 gig / 260 gig. I tried several times and advanced furthest with the Intel Partition Option, but then the whole Thing crashed, resulting in a lot and lot of error messages *- mostly something with device sda,* which seemed to repeat themselves. So as he wants to access a part, cant do it and turns over and over again.
I hoped that it provides a report file, but since everything seems to freeze or crash, cant provide one right now.

Edit:
At some stage Kubuntu just booted wanted a password - but didnt react to any input and also i didnt set any up.
After opening a browser, the terminal and finding the log file the pc crashed with following info:
[I](1442.488915) Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000087
(1442.488915)
(1442.489163) drm_kms_helper: panic occured, switching back to text console
[/I]

**My Questions are now:**
- How can i access the hard-disk - if possible and save data?
- How can i find out if the hard-disk really is damaged?
- If its impossible to sort this out without professional (paid) help, how could i manage to boot Kubuntu from Pendrive   faster than in 40min? So i could use the laptop whilst travelling (5weeks left) and try my luck back home in Germany - i rather not intend to get to a pc specialist here in peru and try my luck with limited spanish :)

apprecciate all comments and input!
thanks a lot!


Edit 2:
I tried using the Systemrescuedisk and choose the option, to try booting from hd. resulting in several attempts to mount *dev/sdb, dev/sda5, dev/sda* and trying those all over again. Final message was:
[I]Cannot find a valid root filesystem (partition having /sbin/init).
Running a mini shell (cannot complete the boot process)
/bin/sh: can't access tty; job control turned off[/I]

---

### Post by affeloco on 2013-05-12
was able to start xfce from the [recusedisk program]("http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick"), after a booting period of about 20mins or more. but gparted which should deliver info on the harddrive doesnt do anything. filemanager (spacefm) shows the disk, but says: *Status: Finished with error (exit status 1)* then theres a field below, which says: [I]udevil: error 64: unable to determine device fstype - specify with -t

[/I]In total, spacefm, shows four drives - [I]
md0 - [/I]* Finished with error (exit status 1)* then theres a field below, which says: [I]udevil: error 64: unable to determine device fstype - specify with -t
sda1 232g - [/I]* same message*[I]
sda2 1024b - same message
sda5 1013m - [/I]* Finished with error (exit status 1)* then theres a field below, which says: [I]mount: /media/sda5-ata-ST9250315AS_5VC8: mount failed: Invalid argument
[/I]and lastly sdb 4G Pendrive - which works.

Further i used this commandline [SIZE=1]*[COLOR=#000000]mount -t ntfs /dev/xxx /mnt/windows -o ro [/COLOR]*[/SIZE]from [http://www.sysresccd.org/]("http://www.sysresccd.org/Sysresccd-manual-en_Mounting_an_NTFS_partition_with_full_Read-Write_support") which delivers the following: E*rror reading bootsector: Input/output error. Failed to mount /dev/sda1: I/O error. NTFS is either inconsistent, or there is a hardware fault, or its a SoftRAID/FakeRAID hardware.* Then theres bla about using chkdsk on Windows or about Fake or Softraid and saying i should activate it and mount a different device under the dev/mapper directory - so, not really helpful.


Yet, i cant see, how i could answer my Questions. So if anyone has ideas, you're more than welcome :)

---

