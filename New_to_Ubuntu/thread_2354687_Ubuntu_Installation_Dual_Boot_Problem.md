---
title: "Ubuntu Installation Dual Boot Problem"
date: 2017-03-05
forum: New to Ubuntu
---

### Post by ozmenberkcan on 2017-03-05
Hello Guys,

I have windows 10 installed on my computer and I am trying to install ubuntu 16.04 from USB. However it freezes on the purple loading screen (F11 also doesn't function). Only message that seemst to be like an error is: "can't request region for source". 
I have been looking through forums but yet I couldn't find a solution. 

Thank you
Computer: 8gb memory / i7 6. gen / Nvidia 950m

---

### Post by Bucky Ball on 2017-03-05
Welcome. If you get this far, are you ticking the 'install updates' and 'install third-party proprietary drivers' (or something like that) at boot? Do you have an ethernet cable plugged in?

Try installing and do not tick the two boxes mentioned above. Hopefully that should get it installed.You can update afterwards and install whatever drivers you need then, too.  Once it is installed, though, it may pay to have an ethernet cable handy, but need to know more about how you're trying to get online.

Let us know how you go without those two boxes ticked during install.

---

### Post by oldfred on 2017-03-05
Are you booting installer in UEFI boot mode? If Windows 10 system, then that is UEFI and you want Ubuntu in UEFI boot mode.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

If booting with nVidia, you usually need nomodeset.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by ozmenberkcan on 2017-03-05
**acpi_osi=**solved the problem. Thank you guys

---

### Post by Bucky Ball on 2017-03-06
Great. Please mark as solved. 'Thread Tools' at top right of page or last link in my signature for how.

---

