---
title: "tar.bz2 files - how to install?"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by Irish1 on 2012-02-22
I'm still unsure about how to use the extract feature in ubuntu.  What do I do with a tar.bz2 file?

In windows it seems easy to install something, but when I extract something in Ubuntu I seem caught in an endless cycle of extracting files and I don't know if it's working or not.

Please help!!

---

### Post by CharlesA on 2012-02-22
You usually only need to extract files from a tar if you are compiling something from source. Most things can be found in the repos by doing a search in the Software Center.

What program are you trying to install?

---

### Post by Irish1 on 2012-02-22
I'm just trying to install new drivers, but this question has always puzzled me.  

Do the repos have items from different manufacturers?

Ya, I'm a newb at all this.

---

### Post by CharlesA on 2012-02-22
Depending on the device, the drivers should already be installed. Is it for a video card?

---

### Post by Irish1 on 2012-02-22
After poking around I noticed that I get this message from my ATI catalyst control cetner:

There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.

I couldn't successfully reinstall it either.

And now I'm trying to install this package and can't:

amd-driver-installer-12-1-x86.x86_64.run

what am I doing wrong?

---

### Post by CharlesA on 2012-02-23
You should be able to install the driver from the software center.

---

### Post by 3rdalbum on 2012-02-23
Use the Additional Drivers program to install the ATI driver. Note: ATI only makes drivers for Radeon HD and later cards. If you just have a regular Radeon (non-HD name) card then you are already using the only driver available.

---

