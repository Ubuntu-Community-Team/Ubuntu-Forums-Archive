---
title: "I need a trusted link for dual-booting ubuntu, i have a win 8.1 64bit"
date: 2014-08-18
forum: New to Ubuntu
---

### Post by Jansen_N.J on 2014-08-18
i have a win. 8.1 Pro 64bit, i want to dual-boot it with ubuntu, i need a trusted tutorial which describes step by step (earlier-disasters-made-me-nervous) :)

---

### Post by deadflowr on 2014-08-18
[Oldfred's UEFI Installing tips]("http://ubuntuforums.org/showthread.php?t=2147295") should be a good starting point for you, at least.

---

### Post by Gordonbp531 on 2014-08-18
1. Make free space on your HDD using Windows partitioning tools - do NOT use GParted to do that.
2. Boot from Live CD or USB.
3. When you click on Install now, the setup utility won't see Windows. Don't worry - use the "Something Else" option.
4. Install Grub on the EFI Partition (use the Discs tool wwhen booted up in the Live CD/USB to determine which partition is the EFI partition)

You should be good to go.

---

### Post by ajgreeny on 2014-08-18
There is an excellent guide to installing, thugh not specifically with Win8 at [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

Have a good read through and be prepared to ask more questions; I don't use windows any more, so can't really help any more on that, but I do have Xubuntu 12.04.5 running brilliantly on a UEFI system.  Do not be afraid of IEFI either, as there is plenty of info on that, starting with the ubuntu page at  [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI")

---

### Post by dave131 on 2014-08-19
Before you start - always defrag the disk in Windows - whether it says it needs it or not - at least twice.  Then backup any and everything you might need in case things get all messed up.

---

### Post by Jansen_N.J on 2014-08-19
thank you all :)

---

### Post by dave131 on 2014-08-19
And a really important thing to remember:  if you need to shrink an existing partition to make room for Ubuntu, always use the Windows tools to do so before starting the Ubuntu install.  I believe if you search (in Windows 8) for administrative tools and/or disk management that should come up.  Reboot the PC (it may require more that once) to be sure Windows "knows" the disk has shrunk and can still access the file system.  If you need any specific help on any of this - from defragging the disk, shrinking a partition, to specific help on any given step of the install just ask.  It's best to say "I'm at xxxx and need to know what to do" or some such thing.  If you need step-by-step for this there are guides, some of which have been pointed to.

Since this is Windows 8, DO read the links already posted to oldfred's information on UEFI (it will be the default with Windows 8).  The main points there will be to go into the BIOS setup and turn off secure boot and, if an option, fast boot.

---

