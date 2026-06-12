---
title: "Update Intel Graphics Drivers ?"
date: 2014-02-09
forum: New to Ubuntu
---

### Post by Victor_Sinha on 2014-02-09
Ok I am new...new means like 1 hour new.

I searched a lot and found that there is a Intel driver update for Ubuntu 13.10, but I cannot find anything for Ubuntu 12.10.

My Config.

CPU - Intel 4770K with Integrated graphics - Intel 4600 HD

Now I tried [COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep VGA  
[/FONT][/COLOR]
**00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)**

Is this correct ? Does not looks like correct. Experts please help.

Now if I go to "About this computer" and Select "Graphics". It says 
[B]
Driver: Unknown
Experience: Standard[/B]


Any help will be really appreciated. Thanks.

---

### Post by bcschmerker on 2014-02-10
The information on the GPU *is* correct - Intel® integrated a Media Accelerator onto the main CPU die in the 4th Generation Core&#8482; Processors (LGA 1150), e.g. your i7-4770.  The [Ubuntu-X Team](https://launchpad.net/~ubuntu-x-swat) maintains a Repository at Launchpad&#8482; for Intel® Media Accelerators&#8482;, which can be programmed into APT as follows from the Terminal:
```
sudo add-apt-repository ppa:ubuntu-x-swat/intel-graphics-updates
sudo apt-get update

```
The Ubuntu-X Team can provide additional information on the correct Package(s) for the 4th Generation Core&#8482; and Xeon® E3-1200v3 Processors' internal HD Graphics.

---

### Post by mastablasta on 2014-02-10
furthermore 12.10 reached end of life last year.

use 13.10 or 12.04 with hardware enablement stack.

the GPU came out last year (2013) yet you are asking why there is no drivers on 2012 verison of the OS image.

---

### Post by mörgæs on 2014-02-10
12.10 is supported a few months more, until april 2014.

---

### Post by oldfred on 2014-02-10
With your new hardware, it is not just the video driver, but also the kernel & other supporting software. Intel has offered many updates which only are in most current version or some only in the 14.04 version. So best to use 13.10 and plan on upgrading to 14.04 when released in April.

 Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)

---

### Post by pqwoerituytrueiwoq on 2014-02-10
i would suggest installing 13.10 and using the 3.13 kernel
this will help you install the kernel easly
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)
you will want to use this command for step 4:
[FONT=courier new]KernelUpdateChecker -no-rc -r trusty -v 3.13[/FONT]
you could try the 3.14rc2 kernel ([FONT=courier new]KernelUpdateChecker -r trusty[/FONT]), but ATM USB3 ports will not work

---

