---
title: "Booting with NV 9600M GS"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by seattle vic on 2008-10-16
I just bought an ASUS M70VM-C1 laptop, with an NVidia 9600M GS.  When I use the Gutsy DVD I have to boot, it gets to a dialog box that says "Ubuntu is running in low-graphics mode", and then gives me options to either continue to run as is or select a driver.  There are no 96XX drivers listed, and no matter what I choose the boot locks up.  Even if I just continue and don't mess with selecting a driver I get the same result.

Any suggestions?

Thanks in advance,

Vic

---

### Post by mikewhatever on 2008-10-16
Gutsy is definitely too old for the 9000 series, as well as Hardy, I suspect. Hopefully, the upcoming version, Intrepid Ibex, will support the 9000s. The nvidia driver for Linux was released reccently, but I'm not sure it's going to make it into Intrepid's repositories. 
[http://www.phoronix.com/scan.php?page=article&item=nvidia_17780&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_17780&num=1)

I guess my suggestion is, download an Intrepid beta CD and test it.

---

### Post by eternalnewbee on 2008-10-16
> **seattle vic said:**
> I just bought an ASUS M70VM-C1 laptop, with an NVidia 9600M GS.  When I use the Gutsy DVD I have to boot, it gets to a dialog box that says "Ubuntu is running in low-graphics mode", and then gives me options to either continue to run as is or select a driver.  There are no 96XX drivers listed, and no matter what I choose the boot locks up.  Even if I just continue and don't mess with selecting a driver I get the same result.

Any suggestions?

Thanks in advance,

Vic
What do you mean "When I use the Gutsy DVD I have to boot"?
Do you mean you have no os preinstalled?

---

### Post by seattle vic on 2008-10-16
> **eternalnewbee said:**
> What do you mean "When I use the Gutsy DVD I have to boot"?
Do you mean you have no os preinstalled?

Well, vista is loaded, but I booted up from the DVD with the intent of making it dual boot.  Are you suggesting that I run the setup program while vista is running?  Would that make any difference as far as the lack of a compatible driver?

---

### Post by seattle vic on 2008-10-18
> **mikewhatever said:**
> Gutsy is definitely too old for the 9000 series, as well as Hardy, I suspect. Hopefully, the upcoming version, Intrepid Ibex, will support the 9000s. The nvidia driver for Linux was released reccently, but I'm not sure it's going to make it into Intrepid's repositories. 
[http://www.phoronix.com/scan.php?page=article&item=nvidia_17780&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_17780&num=1)

I guess my suggestion is, download an Intrepid beta CD and test it.

Thanks.  I did try Intrepid, and the video popped up immediately at 1920 x 1200; very cool.  However it did not recognize any wireless signals.  Dead.  So also made a Hardy iso disk and that booted up also, although at vesa resolution, which I can fix.  However it also didn't see any wireless, so I guess I need some help with that.  I'll do a new post shortly.

Vic

---

### Post by mikewhatever on 2008-10-19
Intrepid is definitely the way to go, unless you want to use vesa for graphics. The 177.80 driver supposedly have the official 9000 series support and is included. [http://packages.ubuntu.com/intrepid/nvidia-glx-177](http://packages.ubuntu.com/intrepid/nvidia-glx-177)
8.10 should come out of beta in only 10 days, and with 2.6.27 kernel, it should provide more wireless support then Hardy, and once installed, you can troubleshoot it.

---

