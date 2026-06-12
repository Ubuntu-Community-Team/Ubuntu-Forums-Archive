---
title: "Issues with UEFI and booting"
date: 2015-03-20
forum: New to Ubuntu
---

### Post by alex_smith2 on 2015-03-20
Laptop is a gateway nv510p04u

Running Ubuntu 14.02.

Recently bought the laptop and have issues getting it to boot usb or cd.

New to this UEFI stuff and to ubuntu in general.

I was able to disable secure boot but when I try to switch the bios the only option I can select is UEFI (I was told I need to boot into legacy).

Any ideas? thanks.

---

### Post by alex_smith2 on 2015-03-20
I know this really isn't an Ubuntu related issue but any advice would help!

---

### Post by sudodus on 2015-03-20
Welcome to the Ubuntu Forums :-)

It is possible to install and run Ubuntu in UEFI mode (in most PC computers). Start by reading these links and links from them, try and ask more detailed question ...

[https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

There is a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295"). 


[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by grahammechanical on 2015-03-20
If the machine is already running Ubuntu 14.04 then why did you disable secure boot? Ubuntu was the first Linux distribution to be able to install on machines with secure boot enabled.

If the machine has UEFI and Ubuntu was installed in EFI mode then switching to legacy or BIOS mode will stop Ubuntu working. If Ubuntu was installed in EFI mode or any other OS for that matter, then a DVD or USB memory stick with an OS on it would also need to be run in EFI mode.

It also follows that the OS that we are wanting to install would also need to be EFI compatible.

Regards.

---

### Post by alex_smith2 on 2015-03-20
Sorry I should have clarified this. I am trying to uninstall Ubuntu and reinstall Windows 8, but I can't do that without booting from cd/usb.

---

### Post by gordintoronto on 2015-03-21
Windows always wants to be the first installation. Within Windows, you can shrink the Windows partition to make space for Ubuntu.

+1 to keep secure boot.

There will be a "magic" key you can press at power-on to select the boot device. Maybe Del, maybe F12, maybe ESC, or something else.

---

### Post by Vladlenin5000 on 2015-03-22
> **alex_smith2 said:**
> Sorry I should have clarified this. I am trying to uninstall Ubuntu and reinstall Windows 8, but I can't do that without booting from cd/usb.

Operating system aren't to be uninstalled... You need to boot from the Windows installation media then select the previous partitions where Ubuntu currently are, remove them and create a new partition or partitions for Windows using its own installer and nothing else.
If you need detailed information about the process I suggest you consult a Windows forum.

---

