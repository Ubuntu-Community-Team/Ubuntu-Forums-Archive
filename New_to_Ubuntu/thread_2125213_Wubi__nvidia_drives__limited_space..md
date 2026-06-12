---
title: "Wubi / nvidia drives / limited space."
date: 2013-03-13
forum: New to Ubuntu
---

### Post by za3bolla on 2013-03-13
Hey guys, its my first time dealing with Linux so, be patient :D 
I have a problem with file system, I tried to download a game from steam but it says that there is no enough space. So i changed the download location but it refused it since it was NTFS ( Another partition)
I change the file system of that partition to ext4 and now its owner is set to root. And I can not create any folder there and it is read only. I need to solve that to make it read and write.
Another thing is today I was downloading updates and it said no enough space clear cache of previous updates and I did clear the cache no problem with that. The thing is, When I installed Ubuntu using Wubi installer I selected an empty partition with 22 GB space. So what gives ?!

Last but not least, will it be a problem if I install the 310 experimental drivers for my GTX 275 ?!

My system : 
Core i5 2400
GTX 275
1.5 TB 
60 GB SSD for windows 
500 GB HD for ubuntu, 1 partition 22 GB installed ubuntu there with Wubi( Still NTFS ) , one ext4 with the problem I just told u , the other is empty NTFS

---

### Post by ajgreeny on 2013-03-13
This is a limitation of wubi, I'm afraid.  Even though you gave your 500GB disk/partition over to ubuntu, wubi is limited to just a 30GB file size, I think, and you will not be able to simply enlarge that as far as I'm aware.  Wubi is not really meant for a ling term dual boot system installation, but is really just to check that your hardware is OK for the OS.  Assuming that it is running well, apart from this glitch, I suggest you do a proper partitioned installation.

It is possible to migrate your wubi installation to a full partitioned installation, but I have never used wubi so wil leave you to search for the way to do so from [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by grahammechanical on 2013-03-13
> [COLOR=#000000] will it be a problem if I install the 310 experimental drivers for my GTX 275 ?![/COLOR]

This gives you a clue: "experimental." The only way to find out the answer is to try it. May be Yes. May be No. Regards.

---

### Post by za3bolla on 2013-03-13
> **ajgreeny said:**
> This is a limitation of wubi, I'm afraid.  Even though you gave your 500GB disk/partition over to ubuntu, wubi is limited to just a 30GB file size, I think, and you will not be able to simply enlarge that as far as I'm aware.  Wubi is not really meant for a ling term dual boot system installation, but is really just to check that your hardware is OK for the OS.  Assuming that it is running well, apart from this glitch, I suggest you do a proper partitioned installation.

It is possible to migrate your wubi installation to a full partitioned installation, but I have never used wubi so wil leave you to search for the way to do so from [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198")

OK I tried that and did some extra job to do it. changing it the partition I used with Wubi to type 82 and stuff like that.
Now I think it is called a swap partition, can I format this partition to be available to me in windows ?! 
And I need explanation on how to install ubuntu from scratch.
I tried it before but it did not work with me that's why I used Wubi.

I read that in order to install ubuntu I need to have host, swap and root partitions!!!

---

### Post by TK999 on 2013-03-13
If you have in excess of 4 GBs of RAM, you probably won't need swap at all. When you install Ubuntu, the graphical utility offers you some choices, such as installing alongside Windows, and selecting such an option takes care of partitioning automatically. The partition setup you read about is just one option, as you can set up Linux systems with various partition schemes, all of which work fine.

As for your question if a Linux swap partition interchangeable with Windows: I think not. Windows uses hiberfile.sys and pagefile.sys for the purpose of swap.

---

### Post by za3bolla on 2013-03-13
I have 8 GB of memory so I do not need swap.
How can I claim change it to be normal storage for either windows or ubuntu?
About installing alongside windows, does not this install ubunut on the same drive or partition as windows's ?
And if not, what will it do when I select it, Windows is on a SSD and Ubuntu is on HD.

---

### Post by TK999 on 2013-03-13
First, when booting from the CD/DVD/USB media, select "Try Ubuntu" and run gparted from a terminal; you can delete the swap partition with this and set up something else (like resize an existing one). As for selecting install options, check out the documentation at [https://help.ubuntu.com/12.10/installation-guide/amd64/d-i-intro.html](https://help.ubuntu.com/12.10/installation-guide/amd64/d-i-intro.html) .

---

### Post by za3bolla on 2013-03-13
Now, I removed Ubuntu completely from my PC. And re-installed the old fashion way. Installation was smooth no problems at all except, when I rebooted to boot ubuntu for the first time, it did not boot and showed an error and saying GRUB Rescue > 
What shall I do now ?!
I searched google and found out about boot repair. The thing is, will it mess my windows ?! Or does repair Ubuntu and linux distributions only ?!

---

### Post by za3bolla on 2013-03-13
BTW Windows Boots fine, I'm on windows now. Ubuntu is the one that is not booting.

---

### Post by TK999 on 2013-03-13
GRUB should autodetect your Windows and set up so that you'll have a menu to choose which OS to boot. But even if it does not, the Windows data is not harmed, only the boot record, which can be fixed either by adding the Windows entry into GRUB manually or fixing it with the Windows install medium (which in turn breaks GRUB).

Thus, I think you should try running boot-repair and see if that remedies it.

---

### Post by za3bolla on 2013-03-13
OK before I try it, may I ask you to tell me how to add windows entry into grub :D 
just in case something happens, I want to be ready for it.

---

### Post by ajgreeny on 2013-03-13
> **za3bolla said:**
> OK before I try it, may I ask you to tell me how to add windows entry into grub :D 
just in case something happens, I want to be ready for it.
Simply open a terminal in your ubuntu OS with Ctrl+Alt+T, and run the command ```
sudo update-grub
``` That will search your computer for all operating systems and add them to the grub menu for you.

---

### Post by mörgæs on 2013-03-13
Next time please ask your questions one by one. It makes it easier for others to follow the topics.

---

### Post by za3bolla on 2013-03-14
I have a question here related to grub, its now version 1.99 should I update it to latest version or keep it as it is ?!
Both windows and Ubuntu are now showing in GRUB boot menu 
Thanks for the help guys :D

---

