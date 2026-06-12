---
title: "Creating &amp; Mounting partition the proper way in ubuntu 13.10"
date: 2014-01-22
forum: New to Ubuntu
---

### Post by amit_roy2 on 2014-01-22
Hi Everyone,

I'm a complete newbie in the linux field without any prior training or knowledge. Whatever little knowledge I've is from Googling. Now as I decided to move to linux I'll require very much help from you guys. This is my first attempt and if I feel comfortable I'll move my entire windows ecosystem to Linux. Now, I want to install linux on a fresh 500GB hdd where I want to create a 84GB partition for linux OS, another 400Gb for data and 4 GB Swap area while installation (While booting from Ubuntu disk it showed approx 488GB available space).

Now my questions are:

 What mount point to assign to each of these three partitions? 
What file format should I chose EXT4 or NTFS so that instantly after installation I can explore/use both os and data partition? All my other PCs are Windows (NTFS) and I'll also enable data sharing over Wi-Fi Network. And also is there any file explorer for linux similar to Windows Explorer? 
And lastly, in windows I used to unstall Win7Codecs to play all kind of audio and video formats, what should I use in Linux so that I'll be able to play mp4, mkv, m2ts, avi, flv, mov etc.?


Thanx in advance!!

Amit Roy

---

### Post by Mark Phelps on 2014-01-22
> I'll move my entire windows ecosystem to Linux. 

Not sure what you mean by this!  You can't actually move MS Windows stuff to Linux; they are completely different operating systems and environments.

As to sharing data, both MS Windows and Linux can read/write NTFS partitions,  but Linux runs in its own filesystem partition -- which Windows doesn't understand.

To do data sharing between the Windows PCs and the Linux machine, you'll need to look into using Samba.

As for playing videos, you will need to install the codecs needed for each video format.

---

### Post by Impavidus on 2014-01-22
First of all, Linux is not Windows. You can't move your entire Windows ecosystem over to Linux. It's like picking up a piece of tropical rain forest and planting it in the middle of a coral reef, expecting it to florish there too. It won't. The environment is different and the ecosystem will look differently.

84GB for the operating system is much more than you need. If you're careful it fits in 10GB (maybe even 5), but to be on the save side I usually recommend about 25GB. If you don't want a separate partition for your home directory, where you'll store your personal files, you'l have to make it larger. It depends on how you want to use your data partition. The mount point for the OS partition should be /.

To share a data partition with Windows on the same computer using a dual boot, you'l need an ntfs partition. When sharing via the network things are different.

By default you'll get a file system explorer somewhat similar to the one in Windows. I can't be more precise, as I don't know what the Windows one looks like nowadays.

Installing all codecs you want shouln't be too difficult (unless you want some obscure or really patent-encumbered ones). Best to start thinking about that after installation.

---

### Post by grahammechanical on 2014-01-22
When we run the Ubuntu live session we get access to a utility called Gparted. You can use that to partition that 500 GB disk into those partitions that you want. I would suggest that before you install Ubuntu you format the 400 GB data partition to NTFS from Windows using a Windows utility.

When it comes to installing Ubuntu you need to select the Do Something Else option. That will let you select what partitions to install Ubuntu in. At the partitioning screen you make sure that the 500 GB disk is being read. It should be called sdb. Make sure that the Grub boot loader is going to be installed into the MBR of sdb. There is a panel for doing this. The default is sda and that should be your Windows disk. Installing Grub into the MBR of sda will overwrite your Windows boot loader. So, be careful not to let that happen.

Select the 84 GB partition and click ADD. In the dialog box go to the panel called Use As and select Ext4. Then tick the box to format the partition. Then go the Mount Point panel and select / Then click OK to get back to the partitioning page. Repeat for the swap partition but this time give it a mount point of swap.

Now double check where Grub is going to be installed. You do not want to mess up your Windows boot loader. Now click Install.

Grub should detect your Windows installation and put an entry for it in the Grub boot menu. If you now give sdb the boot priority then you should get an option to boot either Ubuntu or Windows You will also have a large partition that can be read by both Windows and Ubuntu.

One more piece of advice from me. When installing Ubuntu do not tick the box to Install Third Party Software. That will activate a proprietary video driver and it may be (just may be) that the first reboot will give you a black screen. I never install using the proprietary video driver. We can always change video drivers afterwards and also install that third party software. It is called Ubuntu Restricted Extras in the Software Centre.

One final thing. Up until the point when you are at the partitioning page and you click Install you can cancel and back out of the install session.

Regards.

---

### Post by amit_roy2 on 2014-01-22
> Not sure what you mean by this! You can't actually move MS Windows stuff to Linux; they are completely different operating systems and environments.

Actually I mostly use MS Office, Tally and Firefox at workplace, Now Libre office & firefox is already available in linux and I have learnt fom googling that I can use WINE to install windows programs (in this case Tally) in Linux. And codec part is just for personal entertainment. I'll decide to completely move to linux if I like the usability, as Linux is obviously tougher than windows. Whatever my requirements are, they are just few clicks away in windows platform but don't anything about Ubuntu. 

And please guide on selecting the mount point while installing Ubuntu. I've gone through some guides but not sure what mount point should I chose for the boot partition and what to chose for the other data partition.

---

### Post by amit_roy2 on 2014-01-22
Thanks @grahammechanical, thats the suggestion I was looking for. 
> When we run the Ubuntu live session we get access to a utility called  Gparted. You can use that to partition that 500 GB disk into those  partitions that you want. I would suggest that before you install Ubuntu  you format the 400 GB data partition to NTFS from Windows using a  windows utility.

> Select the 84 GB partition and click ADD. In the dialog box go to the  panel called Use AS and select Ext4. Then tick the box to format the  partition. Then go the the Mount Point panel and select / Then click OK  to get back to the partitioning page. Repeat for the swap partition but  this time give it a mount point of swap.

And in this particular system I'll be only running linux and not a dual booting with windows. This will be like a trial machine for me for learning linux by my own and with help of you guys I think I'll learn faster than any institute.

And thanks everyone else who took their precious time to comment and guide me.

---

### Post by amit_roy2 on 2014-01-22
[IMG]http://www.techrena.net/images/How-To-Turn-Menu-Bar-On-Or-Off-In-Window_E0A2/Windows_explorer_win7.png[/IMG]

Currently Windows 7 Explorer looks like this!

---

### Post by deadflowr on 2014-01-22
If you're going to install the system as a lone system on the machine, then forget about opening the live session and go straight to the install Ubuntu part.
In the install part when it comes to the part of where to put Ubuntu, choose the option the entire disk.
This will create the necessary file system types and partition layouts without hassle.
By default, I believe it will make one ext4 partition and one linux-swap partition.
the layout typically is 
/dev/sda1 for the Ubuntu
/dev/sda2 for Extended(This is a container partition for logical partitions, it will contain the swap partition, which Ubuntu makes as a logical partition)
/devsda5 for the swap.

---

### Post by whitesmith on 2014-01-22
> **amit_roy2 said:**
> And please guide on selecting the mount point while installing Ubuntu. I've gone through some guides but not sure what mount point should I chose for the boot partition and what to chose for the other data partition.The boot partition is mounted at / With a single hard drive this will probably be sda1. It is safest to create a partition for personal files and mount that at /home. This is essentially what you call a data partition. You don't specify how much RAM you have. If enough (I have 32 GB) you won't need a swap partition at all--unless you plan to work with files of immense size or have tons of stuff open concurrently.

---

### Post by amit_roy2 on 2014-01-22
> **whitesmith said:**
> The boot partition is mounted at / With a single hard drive this will probably be sda1. It is safest to create a partition for personal files and mount that at /home. This is essentially what you call a data partition. You don't specify how much RAM you have. If enough (I have 32 GB) you won't need a swap partition at all--unless you plan to work with files of immense size or have tons of stuff open concurrently.

I've only 2GB.

---

### Post by deadflowr on 2014-01-22
2GB means you can make a swap around 2GB.
Some would say double it, and others will say half it.
So, equal swap to ram is usally good enough.

If you hibernate, then you'd probably make the swap closer to the bigger size(double ram)
If not, then 2GB is plenty.
That's about how much the Ubuntu installer would give it, if you let it do the partitioning.

---

### Post by whitesmith on 2014-01-23
You can get by with 2. Ubuntu is so efficient that you can have a robust system with even less than 1 -- but you will need /swap. deadflowr's estimates of size are on the money. Regards.

---

### Post by amit_roy2 on 2014-01-23
Okay thanx everyone for your help. Today I've successfully installed Ubuntu and its running really smooth. It will take me some time to understand the interface and get things done. The best thing I liked while installing that it detected all my hardware including my D'link Wi-Fi adapter instantly and I just connected to my network even before full installation whereas in windows every time I had install drivers to get it working. 

And the first hiccup I got was the missing Refresh button on right click menu. As an avid windows user I had bad habit of refreshing windows every now and then (Right click and click on refresh).

Now please anyone guide me to install and configure Samba for file sharing with my other windows PCs.

Anyways, thanx again everyone for your kind help!!

---

### Post by deadflowr on 2014-01-23
> [COLOR=#000000]Now please anyone guide me to install and configure Samba for file sharing with my other windows PCs.[/COLOR]

Standard advice on this is to start a thread on that subject.

The most knowledgeable people around won't be looking into a thread about partitioning if they can help on a totally different issue.

As well, you can search the forums on the issue.

But for samba, consider this a quick primer of sorts.
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

It should give you some sense of the setup and help in regards to if you start a thread about it, you'll have some sort of idea of what you're trying to do.
Good Luck.

---

### Post by amit_roy2 on 2014-01-24
> **deadflowr said:**
> Standard advice on this is to start a thread on that subject.

The most knowledgeable people around won't be looking into a thread about partitioning if they can help on a totally different issue.

As well, you can search the forums on the issue.

But for samba, consider this a quick primer of sorts.
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

It should give you some sense of the setup and help in regards to if you start a thread about it, you'll have some sort of idea of what you're trying to do.
Good Luck.

Okay, thanx for the suggestion. First I'll go through the link you provided and try other tutorials available over the net & then if i face any problem I'll start a new thread.

---

