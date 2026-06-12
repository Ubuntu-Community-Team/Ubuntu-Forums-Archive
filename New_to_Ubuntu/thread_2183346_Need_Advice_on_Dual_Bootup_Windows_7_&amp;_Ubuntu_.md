---
title: "Need Advice on Dual Bootup Windows 7 &amp; Ubuntu 13.10"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by Ant01 on 2013-10-24
I been experimenting with a small server machine AMD Athlon(tm) II Neo N36L Dual-Core Processor × 2 and ubuntu 13.10 but would like to go to the next step and do a dual installation on my laptop which I use for business on a daily basis. Before I go ahead I need some advice on some of the pitfalls.

Specs for Laptop
Windows 7 Home edition
Manufacturer: Asus
Processor: Intel Core Dual Processor i5-2450M CPU @ 2.50GHz 
RAM:  8 Gigs

1. How do I go about with a dual installation and if I want to remove it is there any danger that I will loose everything on my windows installation
2. Is there anyway I can switch between Ubuntu and windows without having to reboot
3. How do I access my files from my windows directories and will they be fully compatible with  Ubuntu Libre Office


I've found ubuntu 13.04 and 13,10 to be unstable and I think by using it on a daily basis I could get to grips with it better. Can anyone recommend some links where I can learn more about using ubuntu and linux,something like ubuntu for idiots,,,,

Thank you

---

### Post by sandyd on 2013-10-24
> **Ant01 said:**
> I been experimenting with a small server machine AMD Athlon(tm) II Neo N36L Dual-Core Processor × 2 and ubuntu 13.10 but would like to go to the next step and do a dual installation on my laptop which I use for business on a daily basis. Before I go ahead I need some advice on some of the pitfalls.

Specs for Laptop
Windows 7 Home edition
Manufacturer: Asus
Processor: Intel Core Dual Processor i5-2450M CPU @ 2.50GHz 
RAM:  8 Gigs

1. How do I go about with a dual installation and if I want to remove it is there any danger that I will loose everything on my windows installation
2. Is there anyway I can switch between Ubuntu and windows without having to reboot
3. How do I access my files from my windows directories and will they be fully compatible with  Ubuntu Libre Office


I've found ubuntu 13.04 and 13,10 to be unstable and I think by using it on a daily basis I could get to grips with it better. Can anyone recommend some links where I can learn more about using ubuntu and linux,something like ubuntu for idiots,,,,

Thank you
1.
[INDENT]1. Go to Control Panel -> Administrative Tools -> Computer Management -> Disk Management
Resize the partitions there to create free space for Ubuntu - the space can stay as unformatted
2. When installing Ubuntu, select 'something else', and use the space you created in windows to create a swap partition (equal to the windows paging file). If you want to hibernate, the swap file should be larger than 8GB. Then, create a partition for root (/).
3. Install Ubuntu

Note that you can just ignore the first step, and go to the second while choosing to resize Ubuntu, but some people have been having issues with windows needing repair after Ubuntu resizes the disk
[/INDENT]

2.
If you install windows in a virtual machine in Ubuntu, you can launch windows whenever you want. Otherwise, you can only boot to one OS

3.
Ubuntu should show and have access to your windows drive. It should show up on the bar on the left-hand side of the screen

---

### Post by Impavidus on 2013-10-24
1: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
If you want to get rid of Ubuntu later there is a small risk you delete the wrong partition and you can damage the Windows boot stuff. Make sure you have backups and Windows repair when deleting Ubuntu.

2: As sandyd indicated.

3: And it's recommended to put your documents not on the Windows C partition, as this makes it really easy to damage Windows. MS Office and Libreoffice are largely compatible, but it doesn't always work.

---

### Post by oldfred on 2013-10-24
Most Windows 7 have BIOS boot with MBR partitioning and use all 4 primary partitions. 
A few newer systems do have Windows 7 in UEFI mode. And some Windows 7 BIOS boot systems will also boot in UEFI mode. You need to be sure to install Ubuntu in same both UEFI or both BIOS boot mode.

If you have all 4 primary partitions used:
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by Antoine_Muskat on 2013-10-24
Thanks for the advice, I have loaded Ubuntu 13.10 and its flying....
Im quite supprised it went so easy but I still have to login to Windows to see if everything is ok. Excuse the confusion but i'm replying with my new login on Ubuntu 1
I can access my windows docs, music & videos easily I had visions that Iwould have to create some type of sharing because of the windows partioning and formating.

I will report back after I've played around but it looks promising. I don't play games so if Libre Office works well I could be a convert. Most of my stuff is in the clouds anyway so I basically need good internet access. Ill need to try my data dongle from my service provider, I hope the drivers load.

Thanks again

---

