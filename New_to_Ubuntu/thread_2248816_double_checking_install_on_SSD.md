---
title: "double checking install on SSD"
date: 2014-10-17
forum: New to Ubuntu
---

### Post by snowmobiler on 2014-10-17
So i have been running Ubuntu 14.04 on some old PCs and laptops. I am going to install it now on a small SSD and I just wanted to double check something. The laptop is AHCI supported and all that. i found that you should not let Ubuntu create a swap space. I have 4Gb of RAM in the laptop I am using. So when it comes to the part of doing a clean install on the drive, I believe I should choose the "something else" option in order to create partitions. I am going to leave the root and home together (not a big deal for me). Do I just create the one partition, or do I in a sense have to create a swap space with mininmal to no size to it? Since if you don't choose the 'something else' option, Ubuntu auto creates swap equivalent to RAM. Just want to make sure if I only create one root/home partition, it isn't 'smart enough' to create a swap space and it just creates the one partition. 

Thanks!

---

### Post by yancek on 2014-10-17
If the computer you are going to be installing to the SSD has a swap you don't need another one.  If you get a message indicating it can't proceed without creating a swap then do it.

---

### Post by oldfred on 2014-10-17
If you have 4GB of RAM swap or no swap is just about a moot point. It will not be used.

The logic behind not having swap on SSD was that many writes wear out SSD faster. But if swap is not used it does not matter. Plus newer, better SSD now have lives similar to hard drives (but not forever).

If only using Ubuntu, not Windows I also suggest the newer gpt partitioning scheme. If you may get new system and transfer SSD to new system, then I might include an efi partition even if not used. And with gpt booting in BIOS mode you need a tiny 1 or 2MB unformatted partition with the bios_grub flag. 
Windows only boots from gpt drives with UEFI. Ubuntu will boot with UEFI or BIOS from gpt. And both Windows and Ubuntu only boot from MBR(msdos) with BIOS.

---

### Post by snowmobiler on 2014-10-17
Fred,
All I am going to do is load Ubuntu. I've got a plethora of systems running windows etc. This is my play laptop. It's got a standard 80GB drive that i just installed Ubuntu only on. My plan was to just do the same with the new SSD. Put it in and load. I don't need to get all fancy yet with different types of boots etc. I am still learning linux. So what has happened on my other systems is that Ubuntu uses 70+GB for root/home and then puts a swap at the end. One old laptop has 1GB Ram and Ubuntu auto put a 1GB swap at the end. ALL i want to do is have the one partition and make sure there is no swap created.

[http://ivanblagojevic.com/how-to-install-ubuntu-14-04-lts-on-an-empty-hard-disk-tutorial/](http://ivanblagojevic.com/how-to-install-ubuntu-14-04-lts-on-an-empty-hard-disk-tutorial/)

above is the tutorial I would follow for manually partitioning. So I ordered a 120GB SSD. Instead of the first option which will erase an empty drive and auto format (create swap too), is my best/easiest option to manually create a 20GB root partition and a 100GB home partition? That is what I would be leaning towards.

---

### Post by whitesmith on 2014-10-17
If you go with a "standard install" Ubuntu will always create a swap partition. As **oldfred** said, you don't need that if you have 4GB of storage. It won't do any harm (because it's not used), but it won't do you any good either. I would go for a custom installation and not use swap at all.

---

### Post by oldfred on 2014-10-17
Several examples with screen shots of Something Else install. You have to use Something Else if you want anything other than the standard / & swap install.

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

