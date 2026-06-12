---
title: "Grub missing after Windows Clean Reset. Boot-Repair Fails"
date: 2023-10-26
forum: New to Ubuntu
---

### Post by amoghd9 on 2023-10-26
I performed a clean reset of Windows yesterday and Grub is missing after that. I tried to use boot repair using Live USB but it fails giving me the following error - "An error occurred during the repair. Error: NVram is locked (Ubuntu not found in efibootmgr). Please report this message to [email]boot.repair@gmail.com[/email]. Locked-NVram detected."

Here is the complete log - [https://paste.ubuntu.com/p/PH9CDC872K/](https://paste.ubuntu.com/p/PH9CDC872K/)

Please help!

---

### Post by grahammechanical on 2023-10-26
This is what I see

The EFI system partition is nvme0n1p1 and it has Ubuntu/grub boot files as well as Microsoft boot files. So, I ask, is Windows Fast Startup enabled? It is a form of Hibernation and prevents Ubuntu from loading. Have you tried loading Ubuntu using the UEFI utility boot options?

If you manger to load Ubuntu run this command in a terminal

```
sudo update-grub
```

Watch the printout. Does it include Windows? If so, then run

```
sudo grub-install /dev/nvme0n1p1
```.

Now see if the Grub boot menu appears.

Regards

---

### Post by yancek on 2023-10-27
If you did a factory reset for windows, that is the cause of the problem as Ubuntu was not preinstalled so only the windows UEFI option remains.  Lines 179 and 180 show this, only a windows entry and the flash drive entry.  I don't know why you get the errors on line 9 and 10 regarding efivars not found.  Which release of Ubuntu are you using?

If you can use the Ubuntu install USB or another Linux USB to mount and access  /dev/nvme0n1p5, navigate to the /lib/modules directory and see if there is a directory named  6.2.0-26-generic.
The nvram is locked error is discussed at the link below and possible solutions with an explanation offered.  If you use the methods described on the page, make certain you keep notes of exactly what you did and what the results were in case of problems.

[https://bobcares.com/blog/ubuntu-boot-repair-locked-nvram-detected/](https://bobcares.com/blog/ubuntu-boot-repair-locked-nvram-detected/)

---

### Post by amoghd9 on 2023-10-28
Yes that is precisely the issue. I am using Ubuntu 22.04LTS. I accessed Ubuntu Live USB and accessed /dev/nvme0n1p5. I found the directory 6.2.0-35-generic. What should I do next?

I read this post about the vram but it didn't work for me.

---

### Post by yancek on 2023-10-28
>  
I read this post about the vram but it didn't work for me. 		

It didn't work for me isn't going to help anyone to help you, more specifics are needed such as what exact steps you took and what the resutls were.  Did you disable Secure Boot?  Did you check to see if there was a BIOS password and disable it or use it?  I don't know that resetting the NVRAM settings will help as suggested on the page.  I've never dealt with a problem like this myself.  The first 2 options should be simple enough to do without causing further damage.

---

