---
title: "GRUB issues, please help."
date: 2014-05-18
forum: New to Ubuntu
---

### Post by Blakeo on 2014-05-18
Hi guys, I'm having issues with the GRUB loader. I use to have Windows 7 on my computer but because I was having issues installing alongside it I decided to wipe the harddrive and install ubuntu to have the whole disk. The only issue was for some reason the grub loader kept coming up at boot even though Ubuntu was the only one installed. To fix that issue I reinstalled windows and now it doesn't have grub coming up anymore. How can I reinstall ubuntu without having GRUB come up? It is annoying because it is not required for one operating system.
Thank you.

---

### Post by coffeecat on 2014-05-18
Well - GRUB is required because it is the Ubuntu boot loader. I think you are referring to the GRUB menu. And the menu is important even with just a single operating system, because you need the GRUB menu to be able to boot into an older kernel if the latest one is causing problems, to be able to boot into recovery mode, or to run a memtest if you suspect a RAM problem. I can assure you that it is much more irritating not to have the GRUB menu showing when you do need one of these things, even though you can invoke it with a certain keypress.

The default grub menu timeout is 10 seconds. Not long to wait. But if that is still too long for you it is a simple configuration change to make the timeout shorter, say 2 seconds, which will allow you to intercept the menu on those occasions that you might need it.

You installed Windows to fix this grub "issue"? That was really unnecessary if you don't want Windows. I assume from your last sentence that you now want to replace Windows completely again, and not have an Ubuntu/Windows dual-boot. Please confirm, because if you want to attempt a dual-boot, you will need the grub menu. I'm fairly sure that the grub menu doesn't display on a freshly installed single-boot Ubuntu installation, and that the menu should appear only after a kernel update, but since my systems are all multi-boots I can't be 100% certain. Perhaps someone else can confirm this.

If you are intending an Ubuntu-only system and would like to reduce the grub timeout, post back and I can give you relevant details.

What version of Ubuntu are you using?

---

### Post by Blakeo on 2014-05-19
> **coffeecat said:**
> Well - GRUB is required because it is the Ubuntu boot loader. I think you are referring to the GRUB menu. And the menu is important even with just a single operating system, because you need the GRUB menu to be able to boot into an older kernel if the latest one is causing problems, to be able to boot into recovery mode, or to run a memtest if you suspect a RAM problem. I can assure you that it is much more irritating not to have the GRUB menu showing when you do need one of these things, even though you can invoke it with a certain keypress.

The default grub menu timeout is 10 seconds. Not long to wait. But if that is still too long for you it is a simple configuration change to make the timeout shorter, say 2 seconds, which will allow you to intercept the menu on those occasions that you might need it.

You installed Windows to fix this grub "issue"? That was really unnecessary if you don't want Windows. I assume from your last sentence that you now want to replace Windows completely again, and not have an Ubuntu/Windows dual-boot. Please confirm, because if you want to attempt a dual-boot, you will need the grub menu. I'm fairly sure that the grub menu doesn't display on a freshly installed single-boot Ubuntu installation, and that the menu should appear only after a kernel update, but since my systems are all multi-boots I can't be 100% certain. Perhaps someone else can confirm this.

If you are intending an Ubuntu-only system and would like to reduce the grub timeout, post back and I can give you relevant details.

What version of Ubuntu are you using?

I am using Ubuntu 14.04, I have installed Ubuntu by itself before without the grub menu coming up.. Is there no way I can bypass this? What I tried to do was install Windows over everything, got rid of the menu but I also got rid of ubuntu. Now I tried to install alongside and it doesn't detect windows. So atm I got windows on my system, but I want both of them.. I have another thread where I am asking for assistance and I think OldFred had some good suggestions that I'm going to try when I get home.

Please let me know about changing some settings on the GRUB menu. Thank you.

---

### Post by Blakeo on 2014-05-21
Bumping this thread still need help, refer to post above this.

---

### Post by oldfred on 2014-05-21
Post link to BootInfo report:
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
With UEFI If you run any fixes from Boot-Repair do not say yes to 'buggy' UEFI fix. That is only for systems where UEFI has been modified by vendor to only allow Windows to boot. Only if boot issue is really the buggy UEFI may we want that fix. Some prefer other work arounds.
If you have mulitple drives do not run autofix as it installs grub everywhere, but use advanced mode to install grub just to one drive.

---

