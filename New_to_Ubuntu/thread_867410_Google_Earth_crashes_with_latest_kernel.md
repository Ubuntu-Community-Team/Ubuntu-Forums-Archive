---
title: "Google Earth crashes with latest kernel"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by finer recliner on 2008-07-22
After updating to the latest kernel, google earth now makes Xorg crash and restarts X. it worked fine before the upgrade

i have an ATI graphics card and am using the fglrx driver.

here is an excerpt from my Xorg.0.log:
```
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-3)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xd0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1728,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1728,1050) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1728 x 7141
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(II) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
```

there were no timestamps, so i dont know which is the first line of when the crash happened. there is more information in the log file before and after what i posted, but i think this is the most relevant part from what i can gather. if you ask, i'll post a larger excerpt.

can anyone help?

---

### Post by Joeb454 on 2008-07-22
Have you tried booting with the older kernel to see if the problem persists?

---

### Post by finer recliner on 2008-07-29
sorry its taken me so long to reply.

it works with kernel 2.6.24-18, but not the current one (2.6.24-19)

---

### Post by finer recliner on 2008-07-31
bumpz

---

### Post by philinux on 2008-07-31
Works fine here with that kernel, I'm fully up to date.

Could be a graphics card issue.

I'd just use the older kernel till another comes along.

---

### Post by markbuntu on 2008-07-31
The update may have not loaded the kernel modules for the driver. You could reinstall it and that should fix the problem. If you have downloaded the driver from ati and you saved the debs somewhere, you can go to that directory in terminal and use this command:

sudo dpkg -i fglrx-kernel-source_*.deb

to load the driver kernel modules. 

Then reboot and everything should be OK.

I did not have this problem with the -19 kernel but I did with the -20 kernel update and was able to fix it with the above command.

---

### Post by finer recliner on 2008-08-01
i went to System > Administration > Hardware drivers 

my ATI card is usually automagically recognized in the past, however, now this window says that "No proprietary drivers are in use on this system" and does not list my graphics card as a component to enable.

does this mean the 2.6.24-19 kernel does not support the fglrx driver anymore? is there a workaround? will it supported in the future?

my graphics card is an ATI Mobility Radeon X300

thanks all

---

### Post by philinux on 2008-08-01
I would try booting into recovery mode. You'll see a menu, this is the new friendly-recovery. Choose xfix from the menu. Then reboot.

---

### Post by finer recliner on 2008-08-02
> **philinux said:**
> I would try booting into recovery mode. You'll see a menu, this is the new friendly-recovery. Choose xfix from the menu. Then reboot.

i did as you suggested, but still no ATI card detected :(

should i file a bug report somewhere? and drop back to an older kernel for now?

---

### Post by philinux on 2008-08-02
> **finer recliner said:**
> i did as you suggested, but still no ATI card detected :(

should i file a bug report somewhere? and drop back to an older kernel for now?

Yes I would, to make sure the devs are aware and can fix it for the next kernel. Kernel 2.6.24-20 is in the proposed repos, maybe still a bit buggy, so cant be far off being released.

---

