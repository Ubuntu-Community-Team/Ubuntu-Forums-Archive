---
title: "error no such partition grub rescue"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by lascetic on 2013-07-19
Hello. First, I would like to say that I have no idea about linux, so please try to explain simply and step by step. My girlfriends netbook has dual boot for windows XP sp3 and linux mint. I was trying to do a system recovery to factory settings for the XP OS by running an application within windows. At restart this message appeared on the computer (at BIOS environment):
error no such partition 
grub rescue

The netbook has no optical drive, but has a recovery partition for each OS. Can anyone please tell me what happened and what can I do?

---

### Post by Mark Phelps on 2013-07-19
The Windows application probably didn't work because you loaded GRUB into the MBR when you intalled Mint.  That's likely to prevent it from working.

If you can lay your hands on a XP CD, you might be able to "repair" the MBR back to its original state -- but that is no guarantee that the system recovery will work.

OEM-provided system recovery apps typically require that no changes be made to the partitioning scheme from its original arrangement -- and you "broke" that when you installed Mint in its own partition.

OEM system recovery apps are designed to return the entire machine to the state it was in when you first started it up.

If you contact the netbook seller, you might be able to purchase a set of full-restore CDs (or a DVD) that would allow you to reinstall XP from scratch -- but that will most likely completely reformat the drive, remove all the current stuff on it -- and wipe out Mint in the process.

So, if all you're trying to do is reset XP back to its original state -- without affecting anything else on the drive -- there is really no way to do that -- short of reformatting the XP partition and reinstalling it from scratch.

---

### Post by lascetic on 2013-07-19
Thanks for your response. Unfortunately there is no optical drive and no XP CD. Isn't there a way to do it from the recovery partition? Or at least anyway to have the PC back working?

---

### Post by lascetic on 2013-07-19
I managed to repair the mbr by making a bootable flash drive of Mint. Then I opened the terminal and typed the commands:
sudo apt-get install lilo

sudo lilo -M /dev/sda mbr

I was then able to boot into XP and complete the recovery I had initiated.

However, I am not given the option anymore for dual booting. PC boots straight to XP. Anyone knows how to fix this?

---

### Post by oldfred on 2013-07-19
You may need to install grub again. But if the recovery repairs you did modified partition table it may have changed partition layout or deleted the Linux partition. If partition is missing but data still there testdisk may recover it. 

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[URL="https://help.ubuntu.com/community/LinuxSecureRemix"]https://help.ubuntu.com/community/LinuxSecureRemix

[/URL]
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

[URL="https://help.ubuntu.com/community/LinuxSecureRemix"]
[/URL]

---

### Post by lascetic on 2013-09-07
Sorry for the late response. After the hacking of the site I went on vacation and just came back.

The xp recovery deleted the linux partition. So I had to reinstall mint with the grub and now everything works fine. Fortunately I didn't have much on the linux partition. What really sucks is that I bought the netbook with both xp and linux pre-installed, so I assumed that this was somehow taken care when one does a recovery. Anyway, now's all fine. Thought to let you know, in case other people have similar problem. Glad to see the site back up. Thanks for all the help.

---

