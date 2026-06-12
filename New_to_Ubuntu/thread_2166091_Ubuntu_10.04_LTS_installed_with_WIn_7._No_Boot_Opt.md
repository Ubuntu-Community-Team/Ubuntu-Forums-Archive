---
title: "Ubuntu 10.04 LTS installed with WIn 7. No Boot Option for Ubuntu"
date: 2013-08-07
forum: New to Ubuntu
---

### Post by butt3rs84 on 2013-08-07
Greetings all,

   I'm very new to the Linux world. I've got a custom rig running an Intel processor. I installed Ubuntu 10.04 after having installed Win7 on a Samsung SSD. I installed Win 7 on about 60gb of space and have around 190 to play with. If I set Ubuntu as the first boot option it still boots to Windows. I've attached a screen shot of my bios layout. I've tried to make a bootable dvd and USB but, with those it would never recognize that Windows was installed. Last night I wiped my SSD and reinstalled WIN7. Today I installed Ubuntu but, I still can't get it to boot up. I am just not sure what I'm doing wrong. Please let me know if you can help. 

Regards,
butt3rs84

---

### Post by Cheesemill on 2013-08-07
That's a UEFI setup that you've got and so 10.04 won't work (it was released before UEFI existed).

You need to install a version of Ubuntu that is still supported such as 12.04 or 13.04 but first read this as installing on a UEFI system varies from manufacturer to manufacturer.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2013-08-07
If you installed Windows 7 from a DVD, it probably installed in BIOS mode with MBR partitioning, not UEFI mode with gpt partitioning. You can convert a Windows DVD install to flash drive and add the UEFI capability if you want UEFI. Ubuntu will boot in eithe UEFI or BIOS mode from UEFI menu. And how you boot installer is how it installs. Both Windows & Ubuntu have to be same mode, both BIOS or both UEFI.

I am not sure that 10.04 even supports trim and therefore SSDs. I think 10.04 was 2.6.32 and you need at least 2.6.33.

---

### Post by butt3rs84 on 2013-08-08
Thanks guys, I will install Win 7 in UEFI mode and then install Ubuntu 13.04 in UEFI mode and let you know how it goes.

Regards,
Butt3rs84

---

### Post by butt3rs84 on 2013-08-08
As an aside I already have Ubuntu 13.04 set up on a flash drive. How do I tell if Windows was installed in UEFI mode?

---

### Post by oldfred on 2013-08-08
If drive is gpt partitioned Windows will only boot in UEFI mode. And you will have an efi partition.

sudo parted -l

       Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

