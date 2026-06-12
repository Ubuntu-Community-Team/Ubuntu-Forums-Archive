---
title: "Installing Nvidia drivers"
date: 2015-08-22
forum: New to Ubuntu
---

### Post by sam32 on 2015-08-22
I'm trying to install Nvidia's graphics drivers on a fresh installation of Ubuntu 14.04.3, following the directions here: [http://us.download.nvidia.com/XFree86/Linux-x86_64/352.30/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/352.30/README/index.html), and am running into two problems. I'm working with driver 352.30 from Nvidia.

  The first problem is that the installer isn't recognizing my GTX 970  as supported, even when it's on the list of supported cards. I can  continue with the installation through this issue though, but I think it  might be contributing to my second problem. My Windows partition is  able to pick up my card though.

  The bigger problem is that it gets part way through installation,  then gives me: "ERROR: Unable to load the kernel module.". The help file  at the link above has some suggestions for what to do if you get:  "Unable to load the kernel module 'nvidia.ko'.", but nothing for my  error, which has been the case for all of the help I've found online.

  Any help would be much appreciated!

---

### Post by blm-ubunet on 2015-08-22
You would be well advised to not use the nVidia driver direct install method.
Need to install kernel headers & other build tools.
You probably do not have the prerequisite packages installed.
And each time the kernel updates the graphics driver breaks.

A far easier, cleaner & more reliable method is thru' ppa:
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa?field.series_filter=trusty)
Need to heed the warnings in the introduction text (in ppa) about upgrade procedures ...

---

### Post by Iflana on 2015-08-23
I recently tried to setup that exact driver, but was advised not to use the RUN files from nVidia.  The reason was basically having to redo all of the manual setup each time there was an update in Ubuntu.

What I ended up doing was adding a PPA, that had newer drivers than the OS installation came with.  They also worked properly, unlike the ones that came with Ubuntu.  The one that I used a week or so ago was [mamarley]("https://launchpad.net/~mamarley/+archive/ubuntu/nvidia").  The page shows it's now depreciated, and links to [graphics-drivers]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa") instead.  Both PPA have the 352.3 drivers by the looks of it, though I settled on the 355.06 after having issues with an Ubuntu system update when running the 352.3.

---

