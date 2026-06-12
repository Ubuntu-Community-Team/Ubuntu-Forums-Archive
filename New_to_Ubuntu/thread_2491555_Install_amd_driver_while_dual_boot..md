---
title: "Install amd driver while dual boot."
date: 2023-10-13
forum: New to Ubuntu
---

### Post by rifqilubis on 2023-10-13
So i started to used my second drive for linux. I did install amd driver from their website.  Does it really necessary?
or it isn't? 
because you already have amd driver on windows?

---

### Post by Holger_Gehrke on 2023-10-13
Windows drivers are for Windows. Linux drivers are quite different. But for most hardware the drivers are included with the kernel and that includes the amdgpu driver for AMD graphics. Unless you need the amdpro driver - mostly needed when you're using the gpu for other things then graphics - you shouldn't need to download and install anything as far as drivers are concerned.

Holger

---

### Post by MAFoElffen on 2023-10-13
Or in other words: 
Your Windows OS does use a basic AMD graphics driver, as verified and seen by looking at it in your Windows "Device Manager"... 

Linux, in it's Kernel, also includes an Opensource version of the AMD graphics driver...

As said, your operating systems "are separate" and drivers for one  are not only not seen by each other, nor do they do work for each other... In fact Windows has an ego, and believes it is and should be the sole OS on a computer... That it should also make decisions for you during it's update process. That sometimes breaks a dual-boot system. Just be aware of that. (I have dual-booted for over 13 years now.)

---

### Post by rifqilubis on 2023-10-14
> **MAFoElffen said:**
> Or in other words: 
That it should also make decisions for you during it's update process. That sometimes breaks a dual-boot system. Just be aware of that. (I have dual-booted for over 13 years now.)


it breaks because of an update. Then if that happens, how to fix it?

---

### Post by MAFoElffen on 2023-10-15
Run Boot Repair boot from a Boot-Repair LiveUSB, without doing the actual repair... From that disk, start the browser, and post a thread here with the URL of where the 'boot-info' uploaded to a PasteBin.

Someone here will look at the report and give you advice on what to do. 

Most of the time, it just takes reinstalling Grub (the boot loader).

---

### Post by rifqilubis on 2023-10-17
"Boot repair". is it an iso or app kinda thing?

---

### Post by yancek on 2023-10-17
>  "Boot repair". is it an iso or app kinda thing? 		

Both.  The link to get it is below and you can either get the iso or download the ppa using the 2nd option described on the page and follow the instructions to Create BootInfo Summary.  This is only useful if you are having problems booting and you have not indicated what the specific problem is.  You ask about amd drivers, what's the problem?  As pointed out above, having a driver for windows doesn't help with Linux as they are totally separate operating systems.  Can you boot Ubuntu and windows?  Having problems using Ubuntu?  What problems

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

