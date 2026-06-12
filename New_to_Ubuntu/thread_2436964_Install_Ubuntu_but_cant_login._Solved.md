---
title: "Install Ubuntu but cant login. Solved"
date: 2020-02-16
forum: New to Ubuntu
---

### Post by smitla on 2020-02-16
Ubuntu give this message.

In paste bin.

[https://paste.ubuntu.com/p/r4wTBbpSJN/](https://paste.ubuntu.com/p/r4wTBbpSJN/)

Please help

---

### Post by oldfred on 2020-02-16
Do not know encryption, nor jfs.

Do you have Ubuntu?
I see PepperMint & Deepin & Windows.

It looks like your Ubuntu entry is booting the jfs partition, sda12.
See line 978.
Not sure then if grub needs extra help with .mod files to boot into jfs?

If one of your other installs works, you can manually edit the grub.cfg in sda9. 
The 3 line configfile uses the UUID to find the full grub.cfg of an install.
Since all  your installs use /EFI/ubuntu you only have one configfile to boot with.
Official flavors of Ubuntu also have same issue, but other distributions use different folders in UEFI like /EFI/fedora or /EFI/grub.

There is no Windows entry in UEFI, but there is a Deepin entry. Does that boot?
See line 2106

If not you also can try these to boot as they create own UEFI boot and if system is otherwise ok will directly boot kernel.
rEFInd
       [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) 
    Supergrub
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

