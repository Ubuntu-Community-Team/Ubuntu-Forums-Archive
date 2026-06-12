---
title: "Ubuntu on the second hd"
date: 2013-04-30
forum: New to Ubuntu
---

### Post by agaseman on 2013-04-30
Hello

I am very new in the Forum. 
I had installed Ubuntu 12.10 in the primary SATA HD (Dell desktop) and Win-7 on the secondary HD and in a way that bootoaders were installed on the corresponding HDs. Then by using "sudo update-grub", I was able
to choose Ubuntu or Win-7 to boot into, however the problem is I can not upgrade to 13.04!!? The error message say "there is no /temp partition", what is the solution? or what is the cleanest way to install Ubuntu and Win-7 on separate HD without 
messing with Windows MBR? 

Thanks

---

### Post by fantab on 2013-04-30
Since you have already set up Ubuntu and Windows to boot from separate HDD, lets say its done. 
The cleanest way to install Ubuntu is to download 13.04 and install it on your Primary HDD, which already has Ubuntu12.10. During install just double check that Grub is being installed to correct HDD.

---

### Post by agaseman on 2013-04-30
this is what I did before for 12.10, if I repeat this for 13.04 and use "sudo update-grub" to detect the Windows, I expect to get the same error message when I upgrade to 13.10., right? Or I did something wrong when I installed the 12.10?!

thanks

---

### Post by deadflowr on 2013-04-30
> [COLOR=#000000] what is the cleanest way to install Ubuntu and Win-7 on separate HD without [/COLOR]
[COLOR=#000000]messing with Windows MBR? [/COLOR]


Simply install Ubuntu to the drive it is to be installed on and then, when starting up make sure Ubuntu's drive is first in the boot order and boot Ubuntu, then run 'update-grub'.
Windows will be added, though it won't mess with it's boot configs, as it will be added to chainload, meaning when you boot into windows, grub will push you over to Windows bootloader to boot windows.
As long as the windows bootloader and windows are on the windows drive, you can remove the Ubuntu drive and still boot into windows.

And really, the best way to make sure Ubuntu installs only on the Ubuntu drive, is to manually unplug the windows drive, and then reconnect it when Ubuntu is completely installed. This way you can avoid dealing with figuring out which drive is which.

---

### Post by QIII on 2013-04-30
+1 for unplugging.  It also keeps an "Aw, nuts!  I just installed over Windows!" error from happening.

---

### Post by agaseman on 2013-04-30
I installed ubuntu 12.10 exactly as you said it, unplug the Windows drive and after installing ubuntu I plugged back the Windows HD and ran the updated the grub. But now the Ubuntu does not upgrade?! I can boot into either OS With no problem, but there is an error message when I want to upgrade to 13.04.

---

### Post by fantab on 2013-04-30
Just do a fresh install of 13.04 by formatting the 12.10 partition during install. Even if you fix that error you are having there are no guarantees that your upgrade will be flawless. I always "upgrade' to a new version by doing Fresh and Clean install.
You don't really have to unplug the Windows HDD, if its the second HDD or /dev/sdb. By default, Ubuntu will try to install the Grub to /dev/sda.  I assume that your /dev/sda is Ubuntu and /dev/sdb is Windows. If you don't unplug the Windows HDD then you don't have run "update-grub", Grub will detect Windows during install itself.

---

