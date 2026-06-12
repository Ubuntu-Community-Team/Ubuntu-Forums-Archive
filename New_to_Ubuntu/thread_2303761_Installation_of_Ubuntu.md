---
title: "Installation of Ubuntu"
date: 2015-11-21
forum: New to Ubuntu
---

### Post by rohitvichare on 2015-11-21
I have used Universal Ubuntu installer on USB with image of 15.10 on HP530 with formatted hard disc. 
Installation did not completed, so I aborted it. 
I tried re-installing several times. Once It went to Ubuntu installation but it was blocked at 3rd step (step after connecting wi-fi).

Now I have downloaded 14.04 and re-creating new USB drive for re-installation. 

Lets see for the moment I am blocked. 

Thanks to let me know if Ubuntu re-installation can correct or detect what was earlier incomplete installed.

Thanks for your support 

Rohit

---

### Post by grahammechanical on 2015-11-21
Are we to assume that there is nothing on that hard disk except the broken install of Ubuntu 15.10? If so, then does the live session still load? You might need to use the live session and a utility called GParted to reformat the hard disk before trying to install. GParted is part of the Live sessions default applications. And it will let you create a new partition table as well as formatting the hard disk. These things may overcome what was preventing those repeated attempts to install Ubuntu.

Why the installation did not complete the first time is a different matter. That may or may not still apply. This give the specification of that machine

[http://www.cnet.com/products/hp-530-core-duo-t2400-1-83ghz-1gb-ram-120gb-hdd-vista-business/specs/](http://www.cnet.com/products/hp-530-core-duo-t2400-1-83ghz-1gb-ram-120gb-hdd-vista-business/specs/)

There are a couple of things that concern me about the hardware. a) the fact that only a maximum of 224 MB is allowed for video memory and it is taken from RAM. b) Intel dynamic memory management technology the amount of pre-allocated video memory.

[http://www.intel.com/support/graphics/intel915g/sb/CS-011683.htm](http://www.intel.com/support/graphics/intel915g/sb/CS-011683.htm)

You may need to go into the BIOS and increase the amount of pre-allocated video memory.

> Both the 512K and 1 MB settings assume the system is booting using a Microsoft* operating system.

> **What is pre-allocated memory?**
Pre-allocated memory  is the small amount of system memory made available at boot time by the  system BIOS for video. Pre-allocated memory is also known as locked  memory. This is because it is "locked" for video use only and as such,  is invisible and unable to be used by the operating system. Older Intel®  Graphics Products allow for pre-allocated memory in the system BIOS to  be set to either 1 MB, 8 MB or 16 MB. 512 KB is an option as well, but  is a legacy setting and should not be used. Upon boot, the System BIOS  will pre-allocate the amount selected (1 MB or 8 MB) from the top of the  main system memory, which will be dedicated for VGA/SVGA graphics.

> The maximum amount of graphics memory will depend on the computer's  System BIOS configuration. In most cases, the sum total will not exceed  128MB. On some older computers, the system BIOS does not limit the  graphics memory to 128MB and so users may see maximum graphics memory up  to 224MB.



I would say that that fact makes Ubuntu unsuitable for that machine. You may get better success with Lubuntu.

Regards.

---

