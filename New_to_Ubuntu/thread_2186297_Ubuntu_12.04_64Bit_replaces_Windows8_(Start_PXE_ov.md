---
title: "Ubuntu 12.04 64Bit replaces Windows8 (Start PXE over IPv4; boot-repair; EFI)"
date: 2013-11-06
forum: New to Ubuntu
---

### Post by hf08 on 2013-11-06
1)  I installed <ubuntu-12.04.3-desktop-amd64.iso> over an windows8
    (erase disk and install Ubuntu)
2)  after installation try to reboot shows: Start PXE over IPv4
3)  then I used boot-repair from a live version at USB stick:
    sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
    sudo apt-get install -y boot-repair && (boot-repair &)
    used <recommended repair> and followed the recommended steps
4)  after reboot without USB stick it worked
5)  after a second reboot it shows again: Start PXE over IPv4

6)  repeated step 3
7)  repeated step 4
8)  after step 7 (installed version, no live USB stick) I used boot-repair at the installed version
9)  after reboot it worked
10) after a second reboot it shows again: Start PXE over IPv4

in the boot menu FastBoot and FastStartup are disabled

Boot Info Scripts of the different trials:
[http://paste.ubuntu.com/6370458](http://paste.ubuntu.com/6370458)
[http://paste.ubuntu.com/6370520](http://paste.ubuntu.com/6370520)
[http://paste.ubuntu.com/6370615](http://paste.ubuntu.com/6370615)
[http://paste.ubuntu.com/6370696](http://paste.ubuntu.com/6370696)

What can I do more?

---

### Post by oldfred on 2013-11-06
It looks like you have changed boot order. This is extracted from the UEFI memory.

 BootOrder: [COLOR=#ff0000]0000[/COLOR],0004,0001,0002
Boot0001* UEFI: IP4 Realtek PCIe GBE Family Controller
Boot0002* UEFI: IP6 Realtek PCIe GBE Family Controller
Boot0004* UEFI: CBM2080 Flash Disk 4.00
Boot[COLOR=#ff0000]0000[/COLOR]* ubuntu

But if you are getting network boot then the default still is 0001 for IPv4 or 0002 for IPv6. What does your UEFI menu show?
But some computers have changed UEFI to automatically move the Windows entry to default. That is not per UEFI standard. And if no Windows entry it may do whatever?? One user with that issue just changed ubuntu to windows & it then worked.

---

