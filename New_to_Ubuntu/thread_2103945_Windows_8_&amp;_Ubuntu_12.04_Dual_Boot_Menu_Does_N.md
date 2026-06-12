---
title: "Windows 8 &amp; Ubuntu 12.04 Dual Boot Menu Does Not Load"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by Michellle on 2013-01-11
[cross-posted on askubuntu: [http://askubuntu.com/questions/240059/windows-8-ubuntu-12-04-dual-boot-menu-does-not-load]](http://askubuntu.com/questions/240059/windows-8-ubuntu-12-04-dual-boot-menu-does-not-load])



Hi everyone, 



  I've read abt the ton of complications/problems ppl are facing with UEFI when installing Ubuntu alongside Windows, but I haven't been able to find a solution to the one I encountered. 
  

I have a Windows 8 OS and we installed Ubuntu 12.04 next to it. However, the dual boot menu did not pop up upon reboot. It loaded Windows directly. (Secure boot & rapid technologies are disabled). 
  

After some research & forum reading, we verified that Ubuntu was indeed present in the EFI partition and we ran boot-repair. Eventually, the boot menu appeared, but it did so at every second reboot (from a shutdown not a restart). 



Then, it disappeared again and the laptop goes directly into Windows. 
  

When the dual boot menu appeared, we went into Ubuntu and life was good so the installation -or some parts of it- worked... But how do i now get the dual boot menu to appear as it's supposed to? 
  Furthermore, I read that with Windows 8 the dual boot menu becomes graphical... But we just had the regular old list. 
  

Any tips?? 
  

Thanks! 

PS: This is a PORTEGE ultrabook Z935

---

### Post by oldfred on 2013-01-11
Post link to Boot-Info report.

If you boot directly to UEFI menu and boot the ubuntu entry does it not continue to use that entry?

---

### Post by Michellle on 2013-01-11
I don't have the UEFI option for boot :-SSS

---

### Post by oldfred on 2013-01-11
Boot installer again in UEFI mode and install Boot-Repair to your installer flash drive or DVD when booted.

Run Boot-Info report and post link.

---

