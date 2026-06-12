---
title: "Deleting Distro's"
date: 2013-06-26
forum: New to Ubuntu
---

### Post by Silverbullet52 on 2013-06-26
Hello all, I have Mint and Lubuntu running on the same machine. Is there a way to delete one of the distro's.

Thanks

---

### Post by oldfred on 2013-06-26
Boot into the one you want to keep. Make sure its grub is the one in the MBR to boot from. If both on sda:

       sudo grub-install /dev/sda

Then you can delete the other partition and it will still boot.

Or:
      
 An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

---

### Post by Bucky Ball on 2013-06-27
That's a neat tool, oldfred. I'm going to install the uninstaller and have a look. ;)

---

