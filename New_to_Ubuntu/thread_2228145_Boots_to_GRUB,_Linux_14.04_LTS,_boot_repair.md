---
title: "Boots to GRUB, Linux 14.04 LTS, boot repair"
date: 2014-06-05
forum: New to Ubuntu
---

### Post by Dwight_Dau on 2014-06-05
I recently attempted installing Linux 14.04 LTS to my SD card on my Surface Pro.  When I disable secure boot and attempt to boot to the SD card I get a grub menu.  I attempted to run Boot Repair which was unsuccessful, it returned log [http://paste.ubuntu.com/7598827/](http://paste.ubuntu.com/7598827/)

Any ideas?  Thanks!

---

### Post by oldfred on 2014-06-05
I do not see anything specific wrong, but do not know Surface.
 [http://linux.slashdot.org/story/12/12/30/2340208/why-linux-on-microsoft-surface-is-a-tough-challenge](http://linux.slashdot.org/story/12/12/30/2340208/why-linux-on-microsoft-surface-is-a-tough-challenge)

   Surface Pro Ubuntu install:
[http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu)
[http://ubuntuforums.org/showthread.php?t=2183946](http://ubuntuforums.org/showthread.php?t=2183946)
[http://ubuntuforums.org/showthread.php?t=2209247](http://ubuntuforums.org/showthread.php?t=2209247)

Microsoft has never been friendly with competitors. So I would not have high expectations.

---

### Post by Dwight_Dau on 2014-06-07
Thank you for the information!  With some tweaking, I was able to get my surface to dual boot with Windows 8 and Ubuntu 14.04 LTS.  It's not working perfectly but it does work.

After reading the UEFI boot install & repair link, I added an EFI boot partition to the SD card and reinstalled Ubuntu.  The initial restart worked great, I was directed to the GRUB menu and was able to select either Windows 8 or Ubuntu boot.  However , subsequent boot ups take me to the GRUB prompt.  I found that if I entered the exit command I would either boot up directly in Windows or be redirected back the GRUB menu and could either select Ubuntu or Windows. 

I'll assume the next step is Boot Repair.

---

