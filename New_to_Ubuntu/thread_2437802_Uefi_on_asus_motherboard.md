---
title: "Uefi on asus motherboard"
date: 2020-02-29
forum: New to Ubuntu
---

### Post by goofie007 on 2020-02-29
I am new, and I am gradually understanding this great operating system, which, with the community, and, with the free software, has been enjoying it.What can I do to use ubuntu, either by USB disk or DVD to install it on my PC formatted with Windows 10. I had tried it successfully before, but now a message appears that appears on a black screen and says: "MOK key" OR "uefi boot" and an address appears in the bios that says: boot / efi / grub / mok in black screen when starting the system. It's the uefi bios, and I can't install ubuntu.I know there are many problems with this, but an explanation never hurts.I want to install it from scratch. I had already done it before, I repeat, even with uefi and entering a key provided with the disk and within the ubuntu installation.What will happen now.I am a rookie who does and remakes things to learn, and I interact well with computer science, so, yes, basic.

---

### Post by CelticWarrior on 2020-02-29
Just disable Secure Boot and be happy.

---

### Post by oldfred on 2020-02-29
I think it was my Asus motherboard Z97 that had "Windows" or "Other". And fine print said use "Other" for Windows 7 as it does not support UEFI Secure Boot. So UEFI does not specifically say Secure Boot on or off.
Others with newer versions of Asus seem to have very similar UEFI.

Asus Z97 Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2298896](http://ubuntuforums.org/showthread.php?t=2298896)
Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

What model system? What cpu?
What video card or using chip's video?

Mok key is required by user for installing proprietary drivers like nVidia video driver with Secure Boot. Ubuntu cannot certify that a proprietary driver is "Secure", but a user can. 
So easier for now just to turn Secure Boot off.

More details and UEFI install info in link below in my signature.

---

### Post by mastablasta on 2020-03-03
> **goofie007 said:**
> It's the uefi bios, and I can't install ubuntu.I know there are many problems with this, but an explanation never hurts.I want to install it from scratch. 

a common mistake. UEFI is not the issue here (first OS to support UEFI was Linux). The issue is (sometimes) windows secure boot. if you can disable that, all will come into place. otherwise you may need additional steps to install on machine with "secure boot" enabled.

---

