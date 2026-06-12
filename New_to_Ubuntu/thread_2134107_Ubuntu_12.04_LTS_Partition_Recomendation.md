---
title: "Ubuntu 12.04 LTS Partition Recomendation"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by ChochiWpg on 2013-04-10
Hi Everyone,

I have been doing a lot of reading and researching over the past week with regards to Ubuntu.  I have also been playing around with Ubuntu on the LiveDVD and I think I am ready to give it an install via dual boot option.  I would like to create a 100GB Partition for Ubuntu and use the built in partition tool that comes with the LiveDVD and create the partitions myself.

In my research over the past couple of days I have read that it is recommended to create a /Root, /Home and a /Swap partition.  I have also read that the /Swap partition should be at least 2x the amount of RAM if your system RAM is 2GB or under.  If over 2GB you should allot 2 + 2GB of RAM.  So in my case, since I have 4GB of RAM I should allot 6GB total for /Swap.  Is this correct?

I just wanted to know people's opinions of how I should partition the drives and how many GB I should allow for each partition?  System info below.

HP Pavilion
AMD Phenom 8550 Triple-Core Processor 2.20GHz
4GB RAM
Currently running Windows Vista Home Premium 64bit edition

Thank you in advance for everyone that helps me out.  Much appreciated.

---

### Post by fantab on 2013-04-10
First thing to check with your present partition scheme is, How many 'PRIMARY' Partitions do you have? With MBR/DOS partition table ONLY 4 primary partitons are allowed. So you may have to SHRINK the Windows partition to gain space. When you work on Windows partitons it is best to use Windows tools. And before you 'shrink' the Windows, NTFS partitions make sure that you've run Defragmentation Tool, at least a couple of times.

Now for the Linux partitions, you should use ext4 file-system (unless you have a better option) to format your Linux partition with. On completion your Linux partitions should look something like:

20-30GB ext4 Logical/Primary **'/'** (Mount-point '/' and NOT '/root')
2-4 GB **SWAP** (If you Hibernate your machine then the SWAP size should be equal to or more than your RAM in GIB not GB)
Rest of the available GB ext4 Logical/Primary **'/home'** (/home partiton is where you will be stroing all your DATA and User files, the size depends on your need).

I personally don't use '/home' so my 'home' folder is installed in '/'. Instead of /home I use just a plain linux partition with ext4 file-system and store my DATA on it. But since this will be your first install I wouldn't recommend it to you just yet.

Before you install Ubuntu check/search on these forums if your 'GRAPHICS CARD' has any issues against it. or just tell us what graphics you have and we can help you. Also check the 'wireless' connection.

Good Luck...

---

### Post by ChochiWpg on 2013-04-10
> **fantab said:**
> First thing to check with your present partition scheme is, How many 'PRIMARY' Partitions do you have? With MBR/DOS partition table ONLY 4 primary partitons are allowed. So you may have to SHRINK the Windows partition to gain space. When you work on Windows partitons it is best to use Windows tools. And before you 'shrink' the Windows, NTFS partitions make sure that you've run Defragmentation Tool, at least a couple of times.

Now for the Linux partitions, you should use ext4 file-system (unless you have a better option) to format your Linux partition with. On completion your Linux partitions should look something like:

20-30GB ext4 Logical/Primary **'/'** (Mount-point '/' and NOT '/root')
2-4 GB **SWAP** (If you Hibernate your machine then the SWAP size should be equal to or more than your RAM in GIB not GB)
Rest of the available GB ext4 Logical/Primary **'/home'** (/home partiton is where you will be stroing all your DATA and User files, the size depends on your need).

I personally don't use '/home' so my 'home' folder is installed in '/'. Instead of /home I use just a plain linux partition with ext4 file-system and store my DATA on it. But since this will be your first install I wouldn't recommend it to you just yet.

Before you install Ubuntu check/search on these forums if your 'GRAPHICS CARD' has any issues against it. or just tell us what graphics you have and we can help you. Also check the 'wireless' connection.

Good Luck...

Thank you for your prompt reply.  Currently my system is running with the partitions that were provided out of the box.  D:/ which contains the Factory Image and is approx 13GB in size.  And a C:/ Program Files partition which is approximately 583GB.  Of those 583GB I have 200GB of free space remaining.  I wanted to use 100GB worth of the remaining space for Ubuntu.  

From your response above it sounds like it is possible and can be done through the Ubuntu built in tool.  Also I should mention that I will be getting a portable external drive and transferring approx 220GB worth of data to the drive from my Windows partition, freeing up more space.  I will also place a backup image of Windows on the external drive as well.

I am not sure what type of graphics card I have, I will have to check when I get home from work.  Also, it's a desktop computer so it is using a wired connection.

You mentioned that /home stores all your data and user files.  From my understanding '/' stores all the system files but also any applications/programs you download would go here as well?  Or do the programs get stored in /home?  Thanks.

---

### Post by 3rdalbum on 2013-04-10
/ stores all system files, plus all programs you download. /home stores the documents and settings for each user of the computer.

I must say, you're making things awfully difficult for yourself. For your first installation of Ubuntu, I'd recommend simply using the Ubuntu installer's "Install side-by-side" option. When you start the Ubuntu installer, it will recognise that you have Windows already and give you the "side-by-side" option. When you select it, you'll be prompted to drag a simple slider to the left, to downsize that Windows partition.

Drag the slider until you've got 100 gigabytes sorted out for Ubuntu, and then just continue with the installation. You'll get one partition for / and /home, and a second partition for swap that is appropriate for your system.

That's the easiest way of doing it, and realistically the most flexible way as you don't end off with the situation that "I need more space in my /home, but the only space left is in /". Some people still recommend separate / and /home, but only because of historical reasons. In the past, doing a clean install of Ubuntu would also erase /home unless it was in a different partition. That's not the case anymore.

Just keep it simple. Stick with one partition unless you have a really good reason.

---

### Post by ChochiWpg on 2013-04-10
> **3rdalbum said:**
> 
Drag the slider until you've got 100 gigabytes sorted out for Ubuntu, and then just continue with the installation. You'll get one partition for / and /home, and a second partition for swap that is appropriate for your system.


This I didn't know, I thought that when you select the option to install side by side it just creates one big partition for Ubuntu.  I didn't realize it automatically separates the partition into / and /home (for one partition) and /swap (for a second partition).

If that is the case maybe it is the better option?  I was just concerned about keeping my data separate from my system files.  I thought that it is a better idea to set it up in that manner so that if anything becomes corrupt with system files than your partition that holds your data will still be safe and intact?

I will definitely keep your suggestion in mind as it seems like the much simpler solution.

I tend to over analyze the situation and want to make sure all my ducks are in a row before proceeding.  I just want to understand what is being setup and the best way to do it.  Thanks again for your suggestion.

---

### Post by fantab on 2013-04-10
Back up your important DATA before you proceed with Ubuntu. Also, create a Windows repair disc, if possible. These are precautions you must take before fiddling with your Partitions.

Yes, choosing the option to 'Install Ubuntu alongside Windows' does create, /, /home and Swap. This is simplest. However, I would suggest that you do it manually, its not that complicated, to have a better control of your HDD space. Also, doing things manually is a good way to start understanding and learning Linux. It is difficult to learn when we are 'spoon fed'. You can follow [this guide]("http://www.liberiangeek.net/2012/10/dual-booting-windows-7-and-ubuntu-12-10-quantal-quetzal/"), if you choose to go manual route.

My two cents...

Edit: Added More Links.
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
[https://www.youtube.com/watch?v=3HANcetKsqc](https://www.youtube.com/watch?v=3HANcetKsqc)

The information on these links is a bit old, but its a good guide.
[Formating and creating partitions with Gparted from LiveDVD/USB]("http://members.iinet.net.au/~herman546/p22.html")
[Formating and creating partitions with Ubuntu- Installer]("http://members.iinet.net.au/~herman546/p23.html")

---

### Post by ChochiWpg on 2013-04-10
Thanks fantab,

I will take a look at the guide and take everything you said into consideration.  The manual option doesn't seem overly difficult, but at least I know there is an option that will simplify the process and repartition the drives appropriately for you if you choose to go that route.

Thank you very much 3rdalbum and fantab for your help.  Much appreciated.

---

