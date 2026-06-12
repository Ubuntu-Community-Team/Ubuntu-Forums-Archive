---
title: "Unable to Install Ubuntu 18.10"
date: 2018-11-08
forum: New to Ubuntu
---

### Post by aruninterval on 2018-11-08
When I try to install the Ubuntu in UEFI mode using USB stick in my Dell laptop with preinstalled Windows 10, I get some error message(please see the attachment).

Please help me.

---

### Post by ajgreeny on 2018-11-08
Start by checking the md5sum of the .iso file you used to create the USB install disk to make sure that the file you used is good.
See [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) for all the details.

I also wonder if you booted the USB in UEFI mode; if it booted in BIOS/MBR mode it could account for your problem of missing files.
See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for more info on this.

---

### Post by aruninterval on 2018-11-08
I have a Dell laptop with preinstalled Windows 10 in UEFI mode. I ran a  live Ubuntu usb but it didn't ask me if I wanted to try or Install. I  thought may be it will ask me later. So I went ahead and continued with  the steps. I checked the install thirdy party software and it asked me  to enable secure boot and I did, then I pressed continue. Then after a  minute the home screen appeared with the option of 'Install now'.  Because I didn't want to install it then, I shut down the system,  removed the usb and loggeg in to Windows 10. This was to create  partition. Then I freed some space for Ubuntu. Now when I inserted the  usb again and changed the boot option to 'usb_name', it showed the  following error: Image 1.

---

### Post by oldfred on 2018-11-08
Seems to be a bug.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171)

Just try copying /EFI/ubuntu/mmx64.efi to /EFI/Boot

---

### Post by aruninterval on 2018-11-09
Hi,

Sorry for the misinformation, it was not intentional. The Ubuntu version which I mentioned in the post as Ubuntu 18.04 is actually Ubuntu 18.10. I just noticed it now. So, the problem is solved as I created a new USB disk with Ubuntu 18.04 and performed a clean installation. I can dual boot now in UEFI mode.

PS: The bug is in the Ubuntu 18.10 and I think it's still not resolved.

Thanks for all the help.

---

