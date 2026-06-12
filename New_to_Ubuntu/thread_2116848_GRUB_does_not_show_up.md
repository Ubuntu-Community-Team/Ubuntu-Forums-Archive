---
title: "GRUB does not show up?"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by medajet on 2013-02-16
I have recently installed the 64-bit version of ubuntu on my computer (64-bit) with bootloader installed to /dev/sda/, but for some reason the grub loader does not show up when I boot. The computer boots into Win7 without any prompt whatsoever. I only have one hard drive, and I have used EasyBCD to add a Linux entry, but when I try to boot from the windows bootloader, all I get is a grub4dos prompt. Any help is appreciated. Thanks in advance.

P.S. I have also tried Linux Mint, but that does not work either (the computer boots directly into windows).

---

### Post by oldfred on 2013-02-16
Welcome to the forums.

Best to see details. Did grub not install to MBR because you have one of the few BIOS with bitlocker or virus protection built in and it prevents writing to MBR? Check settings in BIOS.

You may be able to just install with Boot-Repair or post link for BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by medajet on 2013-02-17
> **oldfred said:**
> Welcome to the forums.

Best to see details. Did grub not install to MBR because you have one of the few BIOS with bitlocker or virus protection built in and it prevents writing to MBR? Check settings in BIOS.

You may be able to just install with Boot-Repair or post link for BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

The BIOS is called "Phoenix Securecore Tiano Setup". I have checked the BIOS but it does not appear to have anything related to Bitlocker or virus protection. 

Here is the boot-info.

[http://paste.ubuntu.com/1669247/](http://paste.ubuntu.com/1669247/)

Thanks in advance.

---

### Post by medajet on 2013-02-17
Anyone else has any idea?

---

### Post by oldfred on 2013-02-17
Did you try running the fix from Boot-Repair?

---

### Post by medajet on 2013-02-17
> **oldfred said:**
> Did you try running the fix from Boot-Repair?

I feel incredibly stupid. Boot-Repair fixed the problem. Thank you very much for your assistance in this matter, and sorry for wasting your time. 

Just one last question - how do I switch between Linux OSes? Do I just boot into a live cd, use GParted to delete the linux partitions, and then install the OS?

---

### Post by oldfred on 2013-02-17
You can do that. 

Or if partition layout is what you want you can just use Something Else or manual install and specify which partition is / (root) it will find an existing swap automatically. If you want more than / & swap you have  to use Something Else and then can create other partitions and mount such as /home.

I usually partition in advance, but still have to use manual install to specify which partition is which and format.

---

