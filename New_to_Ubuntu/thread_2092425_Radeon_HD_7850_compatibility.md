---
title: "Radeon HD 7850 compatibility"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by Platanusoccidentalis on 2012-12-07
Hello all,
I have been unable to successfully install the drivers for this video card. Every time I install the drivers and reboot, only my background screen is left. I have tried this approach: [http://www.itworld.com/software/306225/install-amd-catalyst-1210-driver-ubuntu-1210](http://www.itworld.com/software/306225/install-amd-catalyst-1210-driver-ubuntu-1210) . I did all of this correctly, and it did not work. Someone, please help me! I MISS MINECRAFT!

Thanks,
Platanus

---

### Post by Nightcreeper on 2012-12-07
Did you try going into software sources=> Additional Drivers=> Then choose the proprietory driver, NOT the updated one. I have a 7950 Twin Frozr III in my machine, and it works wonderfully, the updated driver, makes my system crash. Also, I don't know if the driver Architecture is the same for 64 and 32 bit systems, but, I wonder if it is the wrong architecture. I know it says x86 and 64, but, it says x86 twice in that link, not x64 twice.

Also, the original article features complete removal of the existing driver, probably for a good reason. See it here:

[http://www.upubuntu.com/2012/10/install-amd-catalyst-1210-driver-on.html?m=0](http://www.upubuntu.com/2012/10/install-amd-catalyst-1210-driver-on.html?m=0)

Hope it helps.

---

### Post by Platanusoccidentalis on 2012-12-07
Thanks, 
I will try that!

---

### Post by Platanusoccidentalis on 2012-12-07
I get this when I run the install: 

[SIZE=3]Supported adapter detected.
Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers.  /lib/modules/3.5.0-19-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.[/SIZE]

---

### Post by Platanusoccidentalis on 2012-12-07
What does this mean and, more importantly, how do I fix it?

---

### Post by QIII on 2012-12-07
For some reason, Canonical chose not to include some common items in the default installation of 12.10.  You'll need to install the headers, and I'm throwing in some build tools for good measure.  Uninstall any driver you managed to install.

Install the build-essential package and the Linux headers.

```
sudo apt-get install build-essential linux-headers-generic
```

Then install the driver from additional drivers, or manually 

```
sudo apt-get install fglrx fglrx-amdcccle
```

If you want the little bit of hardware acceleration, check out the ATI wiki in my signature and look for the acceleration section.

I suppose the wiki needs some updating, but I haven't gotten to it yet...

---

### Post by Platanusoccidentalis on 2012-12-07
Yes, thank you!
Also, how does one get into the 'root' to remove the annoying "testing use only" watermark?

---

### Post by QIII on 2012-12-07
Use ```
sudo
``` before commands to temporarily raise your privileges.  There are ways to get elevated privileges for an entire session, but I recommend just using sudo before all of your commands.  It will cover 99.9 percent of anything you want to do.

So, if someone's tutorial says "do somecommand as root", you should generally do```
sudo somecommand
```

---

### Post by Platanusoccidentalis on 2012-12-07
Thank you very much!

---

