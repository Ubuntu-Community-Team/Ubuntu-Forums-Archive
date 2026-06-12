---
title: "Ubuntu dual boot won't load anymore"
date: 2023-10-22
forum: New to Ubuntu
---

### Post by goes7557 on 2023-10-22
I have been using dual boot with ubuntu 22.04 and windows 11 for half a year now.
When opening my laptop today I din't have the option to boot into ubuntu. It gave me this error code:

Malformed Security Header
Failed to read header: Invalid Parameter
Failed to load image: Invalid Parameter
start_image() returned Invalid Parameter, falling back to default loader
Malformed Security Header
Failed to read header: Invalid Parameter
Failed to load image: Invalid Parameter
start_image() returned Invalid Parameter

and then it booted directly into winsows.
Thank you in advance for any help.

---

### Post by oldfred on 2023-10-23
Did Windows do an update? It probably did.
And did it also update UEFI firmware which reset to defaults. And that turned on UEFI Secure Boot.
If Ubuntu installed in UEFI mode, but not Secure Boot, you get those type of errors if Secure Boot then turned on.

If not using proprietary drivers like nVidia, you can use live installer to install Secure boot versions of kernel, grub & drivers. Use live installer & Boot-Repair or chroot into system & reinstall grub & kernels.

Otherwise check UEFI settings & turn off Secure Boot.

From live installer you can check.
```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ mokutil --sb-state [/COLOR]
SecureBoot disabled 
Platform is in Setup Mode
[/FONT]
```[FONT=monospace]
[/FONT]

---

### Post by yancek on 2023-10-25
Not sure what you are saying in your last post.  Does that mean you reinstalled both windows 11 and Ubuntu?  Do you have an Ubuntu (or other Linux DVD/USB) you can use to try to troubleshoot?  What happens when you try to access the BIOS firmware?  Do you get warning/error messages?  Obviously you would have been able to do this previously to boot and install Ubuntu.

When you ran the command suggested in post 2, did it show Secure Boot on or off?

---

### Post by montessori on 2023-10-26
Same here, and i never resolved.

---

