---
title: "Transferring Drivers from Ubuntu to Windows XP"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-06-16
I currently have a dual boot with Ubuntu 8.04 and Windows XP.  However, Windows is missing most, if not all of the drivers.  Is there any way I can transfer the drivers from Ubuntu onto a CD so I can install them on Windows?  Or will I have to do it the old fashioned way?

---

### Post by ukripper on 2008-06-16
> **subaruwrc01 said:**
> I currently have a dual boot with Ubuntu 8.04 and Windows XP.  However, Windows is missing most, if not all of the drivers.  Is there any way I can transfer the drivers from Ubuntu onto a CD so I can install them on Windows?  Or will I have to do it the old fashioned way?

you can simply access windows drive and copy paste your drivers there.

---

### Post by Dougie187 on 2008-06-16
Do you mean you downloaded the winodws drivers for your laptop in your ubuntu partition and want to transfer those to the windows partition?

Or do you mean that you want to take the drivers ubuntu is using and use them in windows?

If you mean the latter then you can't do that, the drivers that ubuntu uses are not compatible with windows, and so you will have to download the drivers and do it the old fashioned way. However, you can install the ntfs-3g config package
```
sudo apt-get install ntfs-config
```
and simply transfer the drivers from ubuntu to windows for installation.

---

### Post by subaruwrc01 on 2008-06-16
> **ukripper said:**
> you can simply access windows drive and copy paste your drivers there.

How do I do that?

---

### Post by hyper_ch on 2008-06-16
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Dougie187 on 2008-06-16
> **subaruwrc01 said:**
> How do I do that?

Read my post.
Then you will go into your main menu, into system tools, and there is an NTFS-Config program in there. You would select mount internal with write permissions, and hit ok. Then your drive will be on your desktop.

---

### Post by ukripper on 2008-06-16
> **subaruwrc01 said:**
> How do I do that?

Have you got drivers on your ubuntu drive? If yes then open places-->computer and find your windows drive there and open that and select where you want to copy drivers and then boot into windows and install drivers from where you saved them.

---

