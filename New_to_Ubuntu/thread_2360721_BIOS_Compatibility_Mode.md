---
title: "BIOS Compatibility Mode"
date: 2017-05-07
forum: New to Ubuntu
---

### Post by sed_faster on 2017-05-07
Hello folks,

This occur ([http://imgur.com/a/WJxMv](http://imgur.com/a/WJxMv)) on machinne where didn't exist a operating systems installed. After I read this message I noticed which I have two paths:

1-If I continue install Debian in UEFI mode and intend install another operating systems maybe I can't will do this and when I need chose which system I intend run this is opition will be not able!

2-If I want install two operating system I should NOT to force UEFI installation, by click "Go Back";

Am I right? 
Thanks

---

### Post by oldfred on 2017-05-07
Do not force.

You have two ways (actually 3) to boot from new UEFI hardware.
UEFI or BIOS/CSM/Legacy.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    And the third way is whether Secure Boot is on, but then on UEFI Secure boot works.

How you boot install media is then how it installs. So if you boot installer in UEFI mode it installs in UEFI mode.
And UEFI uses gpt partitioning and BIOS uses the 35 year old MBR(msdos) partitioning system.
But forcing install in different boot mode, will normally convert drive from/to gpt or MBR erasing drive and all data.

Post this:
sudo parted -l

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
If dual booting only use Something Else and be sure to boot in same boot mode as previous install.
       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

