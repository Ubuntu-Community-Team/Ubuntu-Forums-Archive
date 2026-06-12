---
title: "Installing Ubuntu alongside Windows 8/Virtual Machine Questions"
date: 2015-02-15
forum: New to Ubuntu
---

### Post by Tom_A on 2015-02-15
Hi.  I have recently downloaded a Ubuntu ISO, and at the time, I would like to install it alongside Windows 8 on my Gateway DX4885 PC, just so I have it as a main operating system if I need it.  I believe that I know how to resize the Windows 8 partition, so I don't think I have much of a problem there.  However, my main question (this might be off-topic, and I apologize if it is) is if it is possible to run Windows 8 in a Virtual Machine in Ubuntu, and if so, how can I create a Windows 8 USB recovery to install it?  When I try to make one, it tries to make me download about a 4GB file from the internet, and unfortunately, my internet is not fast enough for such a download.  I would really like to create one on my computer if at all possible.  I still need to use Windows 8 for certain things (I would like to not use it at all), but I figure that using a Virtual Machine of it as much as possible would be safer, since I could just delete it if a virus gets on it.  Thanks in advance for any help!

---

### Post by mooreted on 2015-02-16
I don't think you can make a virtual machine of an installed operating system, although I have heard of something like that. I could be wrong. I suppose you could buy a Windows 8 DVD and create a virtual machine with that. You can, of course, just install Ubuntu along side Windows 8. It usually works fine.

---

### Post by oldfred on 2015-02-16
If a new system, be sure to do a full backup of Windows and efi partition before install.
Use Windows own tools to shrink the NTFS partition but not to create any new partitions.
Then use gparted or installer to create Linux partitions.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
      
 [http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by gert5 on 2015-02-16
Tom_A,

You could opt for running Ubuntu in the VM instead. I have been very successful using several linux flavors in VMWare Workstation 10 on Win7 host. (SLC linux, Centos, now Kubuntu) works great.

Cheers,
Gert

---

