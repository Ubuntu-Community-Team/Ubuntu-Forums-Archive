---
title: "HOWTO: Turn Ubuntu 7.10 (Gutsy) into Ubuntu Studio"
date: 2007-12-31
forum: Outdated Tutorials &amp; Tips
---

### Post by HotCocoa on 2007-12-31
Here is my first howto. Enjoy! :)
  Okay, this is what I did to convert my existing Ubuntu 7.10 to Ubuntu Studio.
  ```
sudo apt-get install ubuntustudio-desktop ubuntustudio-gdm-theme ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-default-settings ubuntustudio-icon-theme ubuntustudiolauncher ubuntustudio-graphics ubuntustudio-look ubuntustudio-menu ubuntustudio-screensaver ubuntustudio-sounds ubuntustudio-wallpapers ubuntustudio-video usplash-theme-ubuntustudio ubuntustudio-theme
```
That should install all the Ubuntu Studio packages and their dependencies. (ubuntustudio-desktop removes ubuntu-desktop as a dependency) If you do not have the required packages they depend on, just allow apt to install them. Now for the removing of the regular Ubuntu components. 
```
sudo apt-get remove gtk2-engines-ubuntulooks gutsy-wallpapers human-theme ubuntu-artwork ubuntu-minimal usplash-theme-ubuntu
```
  You see? Nothing to it! Now you should be completely running Ubuntu Studio after a reboot!

---

### Post by -grubby on 2007-12-31
I've reported this to be moved to tutorials & tips (don't worry, you shouldn't worry about getting any infraction or anything) 
btw, nice guide :)

---

### Post by Sef on 2007-12-31
Moved to tips and tutorials.

---

### Post by HotCocoa on 2007-12-31
Thanks, Nathan. Doing my best over here :)

---

### Post by exploder on 2007-12-31
Very nice! My compliments for a good tutorial!

---

### Post by dummyhead3 on 2008-01-03
Will this mess up my configuaration???

---

### Post by Drunky on 2008-01-03
This does not include the real-time kernel.

You can also see the [Ubuntu Help Wiki Page for Updating from Gusty to Studio.]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy")

---

### Post by dummyhead3 on 2008-01-03
I tried it, and it did screw up my configuration, in grub, I now have 8 choices of OSs instead of the former 6. The first one fails to star X andt GDM, the second one is the recovery version, the third one is what I had before but with Ubuntu Studio applications the fourth one is it's recovery mode. The 4 others are Win$hit and a previous kernel version (that I never tried...). I don't want the first two showing up because the new entery's normal mode became the default option and also I do not want to clutter up GRUB with a bunch of stuff.
Talking about GRUB, for some reason it thinks that I bought my computer with not only vista preinstalled but also XP wich actuall exists is on a 10 GB partition (very wiered...)

---

### Post by ~LoKe on 2008-01-04
> **dummyhead3 said:**
> I tried it, and it did screw up my configuration, in grub, I now have 8 choices of OSs instead of the former 6. The first one fails to star X andt GDM, the second one is the recovery version, the third one is what I had before but with Ubuntu Studio applications the fourth one is it's recovery mode. The 4 others are Win$hit and a previous kernel version (that I never tried...). I don't want the first two showing up because the new entery's normal mode became the default option and also I do not want to clutter up GRUB with a bunch of stuff.
Talking about GRUB, for some reason it thinks that I bought my computer with not only vista preinstalled but also XP wich actuall exists is on a 10 GB partition (very wiered...)

```
gksu gedit /boot/grub/menu.lst
```

Look for this line:
> ## ## End Default Options ##
Under that you should see 8 blocks, each block is for a different kernel.  If the first two  are the ones causing problems, comment them by adding a # in front of them.  Example:

> #title           Ubuntu 7.10, kernel 2.6.22-14-generic
#root            (hd0,1)
#kernel          /boot/vmlinuz-2.6.22-14-generic #root=UUID=79b94531-e9c2-423f-b10e-19d1f6eab496 ro
#initrd          /boot/initrd.img-2.6.22-14-generic
#quiet[/quote]

---

### Post by HotCocoa on 2008-01-04
> **dummyhead3 said:**
> I tried it, and it did screw up my configuration, in grub, I now have 8 choices of OSs instead of the former 6. The first one fails to star X andt GDM, the second one is the recovery version, the third one is what I had before but with Ubuntu Studio applications the fourth one is it's recovery mode. The 4 others are Win$hit and a previous kernel version (that I never tried...). I don't want the first two showing up because the new entery's normal mode became the default option and also I do not want to clutter up GRUB with a bunch of stuff.
Talking about GRUB, for some reason it thinks that I bought my computer with not only vista preinstalled but also XP wich actuall exists is on a 10 GB partition (very wiered...)

very strange to me, dummyhead3. When I did it it did not mess anything up.

---

### Post by magicman5421 on 2008-01-04
I read that Ubuntu Studio has a special kernel. Will this also overwrite my curent kernel, or is that impossible to do without reinstalling the os?

---

### Post by HotCocoa on 2008-01-04
> **magicman5421 said:**
> I read that Ubuntu Studio has a special kernel. Will this also overwrite my curent kernel, or is that impossible to do without reinstalling the os?

Yes, magicman. It will change the kernel to Ubuntu Studio and remove the old Ubuntu one.

---

### Post by Salpiche on 2008-01-04
> **dummyhead3 said:**
> I tried it, and it did screw up my configuration, in grub, I now have 8 choices of OSs instead of the former 6. The first one fails to star X andt GDM, the second one is the recovery version, the third one is what I had before but with Ubuntu Studio applications the fourth one is it's recovery mode. The 4 others are Win$hit and a previous kernel version (that I never tried...). I don't want the first two showing up because the new entery's normal mode became the default option and also I do not want to clutter up GRUB with a bunch of stuff.
Talking about GRUB, for some reason it thinks that I bought my computer with not only vista preinstalled but also XP wich actuall exists is on a 10 GB partition (very wiered...)

I had the same problem last week when I did the switch, so you are not the only one. Just do what ~LoKe's advised and you will be ok. (that is if you haven't done it yet)

---

### Post by HotCocoa on 2008-01-04
Huh.  Like I said, It didn't happen to me, so I'm not exactly in a position to fix it.

---

### Post by Salpiche on 2008-01-04
> **HotCocoa said:**
> Huh.  Like I said, It didn't happen to me, so I'm not exactly in a position to fix it.

It's all good! it happen to me on one out of three computers so I think that it's hardware specific, in two home brew computer, it worked fine even without 
> sudo apt-get remove gtk2-engines-ubuntulooks gutsy-wallpapers human-theme ubuntu-artwork ubuntu-minimal usplash-theme-ubuntu  
just removing ubuntu-desktop and ubuntu-sounds which is done automatically, on the one HP Pavilion I had that same problem.

---

### Post by HotCocoa on 2008-01-05
Actually, I DID do this on a homebrew computer.
2.40 GHz processor, Intel 32-bit
nVidia GeForce FX 5200
WDC DVD drive
LG CD-R-RW drive
and a built-in soundcard (can't remember my chipset at the minute)

---

