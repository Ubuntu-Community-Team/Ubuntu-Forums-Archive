---
title: "Moving Ubuntu to New System (Upgrade Hardware)"
date: 2011-12-24
forum: New to Ubuntu
---

### Post by just_ken_here on 2011-12-24
Hi
I plan to upgrade my system. My PC is mostly from 2002 - from mobo, ATA, DDR1 RAM, AGP etc.
I have Ubuntu 10.10 and other partitions with grub 1.98 on my SATA HDD (with Adapter to the mobo)

So I plan to just get new mobo (and the whole system) and plug in my existing SATA HDD.
1) Will my system boot and run (Ubuntu & Windows) --without reinstalling or backup ?

Assuming that Linux has the drivers for the new hardwares I am getting.

2) R there any good precautions or suggestions of doing this?

Thanks

---

### Post by BC59 on 2011-12-24
If you get Windows to another computer will crash. It's not recommended. Still you can try.
Ubuntu doesn't have any problem, just uninstall before the proprietary graphic card drivers if you have any and reinstall them on the new computer, according to the new specifications.

---

### Post by BC59 on 2011-12-24
There is a Windows program Sysprep [http://support.microsoft.com/default.aspx?scid=kb;en-us;302577&sd=tech](http://support.microsoft.com/default.aspx?scid=kb;en-us;302577&sd=tech) that could help you...

---

### Post by just_ken_here on 2012-01-10
Why would Windows crash ?
Rn't OSes just another C / C++ binary -> compiled into x86 binaries and run by the processor.

..

Is it because Windows license ??

---

### Post by BC59 on 2012-01-10
Windows is installed on the very computer you install it. Installs drivers for everything. So when you will get the HDD to another computer, will ask to find all the data of the previous computer. In that case comes the blue screen of death.

---

### Post by mastablasta on 2012-01-10
> **BC59 said:**
> Windows is installed on the very computer you install it. Installs drivers for everything. So when you will get the HDD to another computer, will ask to find all the data of the previous computer. In that case comes the blue screen of death.
 
 
not if you boot in safe mode and if you previously uninstall the drivers in use that can cause problems  (graphics, sound, motherboard...). then once in safe mode you can install drivers for new stuff. 
 
also this only works on non OEM version of windows. OEM versions are locked to specific computer and you can unlock them only by contacting Microsoft. And even then they won't always allow it.
 
same thing in linux. if you have any proprietary drivers installed that is.

---

### Post by Bartender on 2012-01-10
As you can see, this is a complex issue.

I've only tried it a few times, but Windows has always blue-screened when I tried to pull the old swaparoo.  As has been mentioned, Windows ties itself to the hardware underneath.  This is all about profit.  Microsoft wants you to buy another copy of their OS.  I've never resorted to calling Microsoft and begging pretty-please but apparently some folks have.  I've heard tales that some were successful.

I've moved a Linux HDD from one computer to another and seen it start right up like nothing was changed.  But the motherboards were of similar vintage.  If you update from a decade-old motherboard to a new one I'm guessing there will be problems.

---

### Post by mastablasta on 2012-01-10
> **Bartender said:**
> As you can see, this is a complex issue.
 
I've only tried it a few times, but Windows has always blue-screened when I tried to pull the old swaparoo. As has been mentioned, Windows ties itself to the hardware underneath. This is all about profit. Microsoft wants you to buy another copy of their OS. I've never resorted to calling Microsoft and begging pretty-please but apparently some folks have. I've heard tales that some were successful.

yeah calling them seems kind of lame. but that is their DRM. stupid. but it is only there on OEM versions. at least that was the case.
uninstalling drivers before doing the move to toher components is a must and should solve the problem. i did it like this when i replaced motherboard, GPU, RAM and added a new CD. HDD is still the same. it's been the same since 1998. :o
 
 > 
I've moved a Linux HDD from one computer to another and seen it start right up like nothing was changed. But the motherboards were of similar vintage. If you update from a decade-old motherboard to a new one I'm guessing there will be problems.
 exactly. drivers (at least some basic generic ones) are in kernel and there is no DRM. a big plus and it makes moving linux OS (especially if it is upgraded to latest image/kernel) easier. if it gives problem reinstall is really fast. 
 
still any proprietary drivers - are best to be removed before the move. just in case.

---

### Post by cybergnome on 2012-11-02
This thread is nearly a year old, but I ended up here, so someone else may too.  As a former Windows power user, I can clarify some of the previous posts.  The comments about the installation being hardware specific are correct.  Windows XP however, included a "Repair Install" option with its installation media.  When this option is selected from the CD menu, the program looks for an existing installation of Windows on the hard drive and then "repairs" it.  This option was to avoid the loss of data a format and reinstall would involve, and although it was probably intended for restoring non-functioning installations, it works well to modify an existing installation transferred to new hardware.  The only data lost is all Windows Updates subsequent to those on the installation media.

Since I haven't used Windows since XP, I don't know if Microsoft continued that feature with Vista and Win 7.

---

### Post by robert shearer on 2012-11-02
BC59 post #3 is correct.
When properly configured Sysprep will allow deployment of an imaged drive.

Licenses must be adhered to and the Sysprep configuration is more than a nightmare... :-(

Though I can confirm, from experience,  that it is possible. :-)

---

### Post by just_ken_here on 2012-11-03
I would close this thread. It is so old.
I have the XP still running on the 2002 board fine.

If you want to add anything interesting feel free.

Thx.

---

