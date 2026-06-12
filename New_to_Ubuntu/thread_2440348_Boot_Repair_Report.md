---
title: "Boot Repair Report"
date: 2020-04-09
forum: New to Ubuntu
---

### Post by shubham276 on 2020-04-09
**Attaching URL for the Boot Repair Report:**
[URL="http://paste.ubuntu.com/p/dGKvdMbhP3/"]http://paste.ubuntu.com/p/dGKvdMbhP3/
[/URL]

[IMG]https://drive.google.com/open?id=1IaBg9212PlLSNLDpxKhqe4s6i8sAISHs[/IMG]

Attaching grub menu image every time my OS boots(Lenevo thinkpad E580).

Facing issues with Os that's why happening.

**Listing Facts:**
[LIST=1]
[*]On a day system screen freezes. Unable to do anything like from moving a mouse, typing with keyboard, pressing win+L. 
[*]Force shutdown 
[*]power on, seeing grub menu then a terminal with following options: 
[/LIST]

[LIST=|INDENT=2]
[*]Ubuntu 
[*]Ubuntu 18.04.4 LTS (18.04) (on /dev/nvme0n1p1) 
[*]Advance Options 
[/LIST]
- Then automatically Ubuntu got selected and getting following error:
[IMG]https://drive.google.com/open?id=17k61HOh8FlQQLLB3NDABm4dxf-GZ2WaA[/IMG]
[IMG]https://drive.google.com/open?id=1JndpTe9VKY7vIsTHZkwHZ6_i_QLDOy6u[/IMG]

- Then change bios order and added a boot pen drive  then installed Ubuntu OS on HDD by selecting "Try Ubuntu" and then "erasing everything" option.
- After this again system freeze and getting grub menu image every time my OS boots.
[IMG]https://drive.google.com/open?id=1IaBg9212PlLSNLDpxKhqe4s6i8sAISHs[/IMG]

**Questions**:
[LIST]
[*]Don't know if multiple versions of OS installed. 
[*]Old OS still present in SSD(earlier installed in SSD). 
[*]Bios settings problem 
[/LIST]

---

### Post by yancek on 2020-04-09
You have apparently tried to attach several images which are not showing?

The boot repair report shows on line 564 that you have Ubuntu installed on the 1TB drive with the system on sda2 and an EFI partition on sda1.
On line 565, it shows another install of Ubuntu which is a legacy/msdos install.  It also shows errors on /dev/nvme0n1p5, "can't read superblock".  That might require a filesystem check, not sure.
You need to post the error messages you are getting as it will be very difficult to suggest a solution without them.

---

### Post by CelticWarrior on 2020-04-09
In addition to the advice above:
[LIST]
[*]Make sure the SATA mode is set to AHCI in UEFI ("BIOS") settings.
[*]IF you have Nvidia graphics you need to install proprietary drivers.
[/LIST]

---

### Post by oldfred on 2020-04-09
Report does not show NVMe drive.
You probably need to update both UEFI and SSD firmware.

This may also apply:
UEFI update required for USB-C port issues 2017 thru 2019 models
ThinkPad models including the ThinkPad X1 Carbon (5th Gen to 7th Gen), X1 Yoga (2nd Gen to 4th Gen), and P-series 
[https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/](https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/)

You may have this setting a vendors use same UEFI across many models:
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)

---

