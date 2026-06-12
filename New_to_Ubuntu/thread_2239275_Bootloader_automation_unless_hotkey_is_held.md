---
title: "Bootloader automation unless hotkey is held?"
date: 2014-08-12
forum: New to Ubuntu
---

### Post by dave140 on 2014-08-12
Hi, I'm very new to linux in general and am trying to accomplish a small feat, any help would be greatly appreciated.  

I know that ubuntu comes with a bootloader but I do not want the bootloader screen to appear by default, I want the computer to auto boot into windows unless I do something while it is loading preferrably holding a hotkey as you would to get into safemode.  I don't know if it matters but currently I have windows 8 installed on my ssd and then I have a 1tb hdd partitioned off 100gb of it for my ubuntu install.  All hardware is extremely new and mid-high end.

Thanks,
Dave

---

### Post by oldfred on 2014-08-13
Did you install in UEFI or BIOS boot mode?

If you have correctly installed Ubuntu's grub boot loader to the hard drive, and installed Windows boot loader to SSD and set SSD as default in BIOS or set Windows as default boot in UEFI, you should have what you want. 
Then to boot Ubuntu you can use one time boot key, f12 on many systems but varies by vendor to boot Ubuntu.

You can also change grub menu to auto boot Windows, but with two drives you do not even need to do that.

---

### Post by chris272 on 2014-08-13
I actually did this on accident in one of my Windows 7 conversions. It is in dual boot with Windows 7 as the primary. However, you do see the grub menu for a few seconds. That menu shows ubuntu on sda5, so any Linux-aware user will know it is there.

---

