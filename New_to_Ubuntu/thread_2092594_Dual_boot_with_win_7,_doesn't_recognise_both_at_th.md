---
title: "Dual boot with win 7, doesn't recognise both at the same time!"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by YanOri on 2012-12-08
Hi, I'm kinda new to ubuntu, so please bear with me if I get a term or two wrong.
So, I had dual booted ubuntu with my pre installed windows. Af the first boot, I selected ubuntu from boot menu and it loaded as it should. At the second boot, when i had to do some work in windows, I chose windows 7 from the boot menu and i got this error 
'Disk Read error occurred. Press CTRL + ALT + DEL to restart', i did that and the same thing came when i selected windows again.
All this time ubuntu was working fine for me.
Then i googled the issue and found fixing mbr through command promt(from a windows dvd) will load windows properly, so i did that and guess what, windows booted fine for me.
But then I didn't have an option to select ubuntu at all. It was just windows by then.
I tried usuing boot repair disk, that gave me some error as 'boot should be in a different partition' (or something similar)
So this time I re-installed ubuntu, now on a different partition, with '/boot' on a drive of 200 MB, 12GB for ' / ' and 4 GB for 'swap', everything worked fine during the install and now I'm on a fesh install of ubuntu. But the previous problem re occurs, I can't choose windows from the boot menu now. It just gives me back this error 'Disk Read error occurred. Press CTRL + ALT + DEL to restart' . Though i can fix this usung a windows disk, I won't be having access to ubuntu by the time.

Now that ubuntu works fine, all I want now is a proper dual boot. I mean  need to get access to my windows back, without harming the ubuntu install. Is thios possible?
I'm really sorry if i couldn't explain the exact problem to you properly, please do ask me of any info that you might need to help me with this issue.

---

### Post by Gremlinzzz on 2012-12-08
This tutorial on dual boot may help
[http://www.liberiangeek.net/2012/10/dual-booting-windows-7-and-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/10/dual-booting-windows-7-and-ubuntu-12-10-quantal-quetzal/)

---

### Post by YanOri on 2012-12-08
Thanks for replying,
I actually followed the exact same tutorial. What a coincidence!
*That method caused me this error*

---

### Post by Gremlinzzz on 2012-12-08
try checking windows and disk for errors and defrag after.
[http://windows.microsoft.com/en-US/windows7/Check-a-drive-for-errors](http://windows.microsoft.com/en-US/windows7/Check-a-drive-for-errors)

---

### Post by YanOri on 2012-12-08
Sorry for being impatient and deleting ubuntu from my hard disk, I'll be making a fresh install of ubuntu again. I'll revert back if i get this error again. 
Thanks a lot for your help :)

---

### Post by oldfred on 2012-12-08
Post BootInfo from Boot-Repair.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
Also are you running any software in Windows that is DRM licensed? 
Or have some specific utilities from HP or Dell running?

Grub2 has a work around for flexnet, one of the major DRM vendors, but these utilties have also caused issues.
       In Windows 7, had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, flexnet and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)

---

