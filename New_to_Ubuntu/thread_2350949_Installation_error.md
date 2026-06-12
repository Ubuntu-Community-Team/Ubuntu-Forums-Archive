---
title: "Installation error"
date: 2017-01-29
forum: New to Ubuntu
---

### Post by chinweanyamele on 2017-01-29
Been trying to install Ubuntu fro over a week now...
Gives me the option to select the OS .. Windows 10 or Ubuntu. When I select Ubuntu it gives me the error message (on another screen) ....

 "file:\ubuntu\winboot\winbildr.mbr

Status: 0xc000007b

Info: the application or Operating System couldn't be loaded because a file could not be found ..."

Any help please?

---

### Post by Impavidus on 2017-01-29
Google doesn't know that error, but suggests I (so that means you) may mean ```
file:\ubuntu\winboot\wubildr.mbr
```
That would suggest you tried to install Ubuntu using wubi. Don't. That method is obsolete and doesn't work with Windows 10 with UEFI (which is what pre-installed Windows 8/10 systems always are).

If that's not what you did, could you explain exactly how you tried to install Ubuntu?

---

### Post by chinweanyamele on 2017-01-29
I did try with wubi after trying to install Ubuntu as a virtual machine thrpugh Virtual Box software with errors after the installation completed.

---

### Post by yancek on 2017-01-29
Wubi doesn't work with windows8 or newer or with any UEFI system.  Give it up.  What exactly happened when you tried to install Ubuntu in Virtualbox.  It shouldn't be a problem.  Specific errors you got might help someone to help you.  Did you verify the downloaded iso was good?

---

### Post by chinweanyamele on 2017-01-29
"Cannot create the machine folder Ubuntu in the parent folder G:/boot/grub/x86_64-efi"

---

### Post by hakuna_matata on 2017-01-30
> **chinweanyamele said:**
> 
 "file:\ubuntu\winboot\winbildr.mbr

Status: 0xc000007b

Your Windows is installed in UEFI mode. Unfortunately, in UEFI mode Microsoft has blocked some boot loader running it from Windows boot menu. Therefore old Wubi versions signed by Canonical don't work.

Other programs like EasyBCD have the same issue. As you can see [here]("https://neosmart.net/wiki/easybcd/uefi/"), it is possible to bypass this issue by reinstalling Windows in legacy BIOS mode or by using a virtual machine. But IMHO the best option is to use Grub2 in UEFI mode.

It is easy to get Grub2 in UEFI mode if you use the [URL="https://www.ubuntu.com/download/desktop/install-ubuntu-desktop"]standard installation method.

[/URL]If you only want the Wubi method to install Ubuntu, there is also an unofficial Wubi version which supports UEFI. see [wubiuefi]("https://github.com/hakuna-m/wubiuefi/wiki")

---

