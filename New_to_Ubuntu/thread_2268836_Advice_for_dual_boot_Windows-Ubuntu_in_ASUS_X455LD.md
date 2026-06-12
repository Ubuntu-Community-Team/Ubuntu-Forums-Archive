---
title: "Advice for dual boot Windows-Ubuntu in ASUS X455LD"
date: 2015-03-11
forum: New to Ubuntu
---

### Post by oliverg83 on 2015-03-11
Hi evereyone, I'm relatively new to linux and this is my first post in this forum

I recently bougth a new laptop [ASUS X455LD]("http://www.asus.com/Notebooks_Ultrabooks/X455LD/specifications/") (it has free OS) and I intend to dual boot Windows and Ubuntu on it. I'm writtting this post to **ask for advice** on the following topics:

**1. Which Windows would be better, 7 or 8.1?** (I'm more inclined to W7, since I don't like the 8.1 new graphic environment and the laptop has no touch screen; also I believe with W7 I will get more control and avoid some hibernation issues I've seen in dual boots. However, the official Asus drivers and support are intended only to 8.1...)
[B]
2. Wich boot would be better UEFI or BIOS? [/B]I've seen several forum posts regarding this topic and I still can't decide. I did install Windows 7 and it seems to have installed some confussion betwen a Bios boot and a gpt partition like in [this post]("http://ubuntuforums.org/showthread.php?t=1987011"). I have no problem in starting again with a fresh install but I need advice on whether boot to choose.
[B]
3. What do you think about the following partition scheme:[/B] The laptop has a 1TB HD. I intend to use 6 partitions, at least, depending on the Windows partition requirements for boot, etc:
 
[LIST=1]
[*]100GB for **windows **system, 
[*]~590GB for **NTFS shared** drive for personal data available to both systems 
[*]1GB for **/Boot** 
[*]8GB for **/Swat** (the laptop has 8GB RAM) 
[*]100GB for **/Root** 
[*]200GB for **/Home** 
[/LIST]

I bought the pc for productivity/gamming.

Thanks so much in advance.

Oliver

---

### Post by Moofus on 2015-03-14
just let me say im not an expert on any of this, but here is what i would do:
[B]
1. [/B]i would recommend 8.1, first of all because thats what the drivers are for, and second is because its newer and when windows 10 comes out, there will be a free upgrade from 8.1.  but, its not a huge difference; if you like 7 better, then that could probably work.

**2.**  I would say UEFI is better because i think its faster to boot and you have more control, or something like that.  it is also newer, so you have more features and speed and stuff.

**3. **i think the partition scheme looks fine to me, its more personally what you want it to do.

---

### Post by oldfred on 2015-03-14
Windows only boots from gpt partitioned drives withe UEFI. Or you can only boot UEFI with gpt partitioning.
Windows & Ubuntu can only boot with BIOS from MBR(msdos) partitioned drives.

Best to have both Ubuntu & Windows in same boot mode, either both UEFI or both BIOS.

Windows has added partition requirements with UEFI. Best to install it first. In BIOS mode it defaults to two partitions, a 100MB boot and the main install.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

New systems to not need a /boot partition for Linux. It just becomes another partition to manage. If installing with server type install or encrypted, then you may need the /boot partition. If you have a separate /home you probably only need 25GB for / (root). And unless hibernating which is not recommended if dual booting, then swap can be just 2GB as you may never use it with 8GB of RAM.

---

