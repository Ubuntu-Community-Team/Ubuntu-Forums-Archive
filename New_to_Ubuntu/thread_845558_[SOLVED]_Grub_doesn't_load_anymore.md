---
title: "[SOLVED] Grub doesn't load anymore???"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Promaster91 on 2008-06-30
I recently got sick of Vista and decided to install XP on the partition. The installation went fine until I rebooted the computer and it booted right into XP, no grub. I popped in my live CD and the Ubuntu partition is still there, but grub continues to be MIA. Does anybody know how to get grub back working. Thanks.

---

### Post by WRDN on 2008-06-30
When you reinstalled XP, its MBR (Master Boot Record) has overwritten GRUB.
To get it back, you could use [Super Grub Disk]("http://www.supergrubdisk.org/"). You could also reinstall GRUB from the LiveCD by following [this]("http://ubuntuforums.org/showthread.php?t=224351") guide.

---

### Post by Promaster91 on 2008-06-30
Cool, I will try that.

---

### Post by kansasnoob on 2008-06-30
Unless you have some additional data partitions that you created on your own page 5 of this tutorial should get you back in the game:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Better yet (but a bit more complicated):

Follow the first two sections of this doc:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Promaster91 on 2008-07-01
It said it was successful but when I rebooted this weird message comes up saying that I have an "Invalid partition table"

---

### Post by Promaster91 on 2008-07-02
Ok. I fixed it. More info [here]("http://ubuntuforums.org/showthread.php?t=846244").

---

