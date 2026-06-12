---
title: "Grub / Bootloader / newbie-mistake.."
date: 2013-04-01
forum: New to Ubuntu
---

### Post by tub83 on 2013-04-01
Hello

Yesterday I felt nostalgic and installed the latest version of ubunto on my PC. It is normally run with Windows 7 but a change every now and then is good for you, I hear, so I thought i'd give it a go. At first I had some problems with making a partition which the install of ubuntu could find, after a few mistakes (alot of storage deleted..*sad face*) I finally succeded. I created a partion of 100gb as exFAT and rebooted with my USB-stick and found the drive. I installed ubuntu via some guides I found on the next and everything was running smoothly. I had no actuall reason to log back on until today when I was going to grab some stored data inside windows 7 when I realized it no longer worked. When I boot up the machine I get the following choices:
[ATTACH=CONFIG]240867[/ATTACH]

When I choose the windows 7-one i get the following error:
[ATTACH=CONFIG]240868[/ATTACH]

I am rather new to ubuntu but not so new to windows so from this i understand that there is something wrong with the bootloader of windows. I made some digging and i found out that the boot-info for ubuntu should be placed in C for a dual-OS to work, which i doubt i did when i installed. So, my conclussion is that I made some terrible error while installing ubuntu.

I have no optical reader and I cleaned my USB-stick with my recovery info to be able to install ubuntu so that option is out the window im afraid. I dont think there is anything wrong with windows itself, only the boot-info for it.

Upon boot-menu there is an option for command-line. I read somewhere that there is a command line to repair the boot, it was involving a set root=(60,1)..something but my divono-edge keyboard do not allow me to make the "=" sign Im afraid, so that option is obviously also out the window. The next thing i tried to persude was the edit-command, which gave me the following info:
[ATTACH=CONFIG]240869[/ATTACH]

Now I will hope to find myself a "Sherlock Holmes"-kind of guy to assist me in recovering Windows 7, without loosing Ubuntu. In worst case scenario I can live with loosing ubuntu (since its a fresh install) but i cant afford to loose Windows 7. First thing I'll do tomorrow is to buy myself a secondary drive use for ubuntu in the future.

My hopes are with you lots,

Thanks in advance,
Ulti

---

### Post by nerdtron on 2013-04-01
Boot from a Windows 7 Installation Disc. You can have options on how to repair your windows 7 startup problems using the disc. If I remember correctly, there is an option in to automatically repair startup problems for windows 7 or something along those lines. You won't loose you ubuntu partition either, but your bootloader will be overwritten so you won't be able to boot ubuntu in the meantime.

---

### Post by oldfred on 2013-04-02
I saw an ismod ldm? 
Did you convert to dynamic partitions with Windows? It used to be that Ubuntu would not install at all, but now if you make space it may install but cannot boot Windows as it is in the dynamic partition.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx]("http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx")


 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
 GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

---

