---
title: "Before dualboot: Backup &amp; partitions on my harddrive"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by linuxnewbie3 on 2013-10-06
Hi,

after trying out Ubuntu with Live-CD several times I want to try to make the next step in getting rid of Windows and becoming a Ubuntu-user.

I think the best way for that is using Ubuntu 13.04 in dualboot. This direct comparision between Windows 7 and Ubuntu 13.04 let's me see, which system serves me better in day by day routine. 
I expect Ubuntu to serve me better and when 14.04 LTS is released I want to only use 14.04 by then.

Before using dualboot I have a few questions, but first a quick overview over my system so you can see from what I'm coming from:
[LIST]
[*]Sony Vaio VPC CP3S1E (i5 2,4 GHZ dual core, 5GB Ram...), with Windows 7 64 bit 
[*]BIOS no UEFI (I read that this is important) 
[*]Harddrive devided in two parts
[LIST]
[*]C: the normal part where nearly all data is, private, programs and system. Total size is 528,GB from which 337GB are free. 
[*]U: Only for me university data. The original reason a made this partition was to have a smaller path when programming in stata. But I want to delete this partition in the progress of installing dualboot and making new partitions. 
[/LIST]
   
[/LIST]

I know that it is important to make a backup before using dualboot. But now I have a few questions about making a backup and making the new partitions.
[LIST]
[*]Is making a system image on an external harddrive enough to secure my system and my personal data? 
[*]I know I should devide my harddrive in several partitions. I know it is possible that both Linux and Windows could use the same data, even Firefox and Thunderbird could synch between Ubuntu and Windows. But how do I do that? Only make a second partition for Ubuntu and Ubuntu uses the data on the windows part or should I make three partitions (1. Windows, 2. Ubuntu, 3. Private Data and Firefox/Thunderbird Cache)? 
[*]Is there any good tutorial to show me how to install dualboot with preexisting Windows 7 part? 
[/LIST]

Please forgive my bad english.

---

### Post by heir4c on 2013-10-06
If you have no recovery dvd than you can make one yourself. (How? I don't now (because I don't use Windows for a long time now) but that can you find via Google)
For making new partitions:
Before you do something, boot up with the live-cd/usb and open a terminal and type:
```
fdisk -l
```
or better (here you see the partitions in MB, with fdisk -l is in 'Blocks'):
```
cfdisk
```
Post the output here. ThanX
So we can see how much partitions there on the disk.
Because, if you have already 4 partition (standard now with Windows I believe) than you must back-up and empty 1 of the partitions to make a Extended partition and Logical Partitions.

---

### Post by fantab on 2013-10-06
First of all, as the post above says, [make a Windows Repair Disc]("http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html"), (that is if you don't have a Windows install DVD).
All partition creation, deletion and resizing of Windows Partitions MUST be done using Windows tools ONLY. All Linux Partitions MUST be managed using Linux tools, like GParted.
If you want to Shrink or resize Windows Partition then see [THIS]("http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html").

For Windows Backup you can have numerous tools to do so. If you ask me, I'd say use [Macrium Reflect]("http://www.macrium.com/reflectfree.aspx")... you read its ['How to' HERE]("http://kb.macrium.com/Knowledgebase.aspx").

Partitions are very personal there are no hard rules. I Dual boot Ubuntu and Windows on one of my machine and heres how I have them partitioned on 1TB HDD:
```
50GB Windows \C NTFS Primary [for Windows System files]
50GB Windows \D NTFS Primary [for my Windows specific Data + that to share with Ubuntu]
25GB Ubuntu EXT4 Primary [for Ubuntu System files]
All the remaining GB EXTENDED PARTITION
4GB SWAP Partition Logical
25GB Free Partition Logical [I usually have another version of Ubuntu installed here]
All the remaining GB DATA EXT4 Logical [to store all my DATA]

```
The legacy BIOS has msdos partition table which only supports 4 Primary Partitions. If we need more we have to make the Fourth Partition as an EXTENDED Partition, which is a Primary Partition and acts as a container for LOGICAL Partitions. We can have up to 100 or more Logical Partitions within an Extended Partition. Laptops with pre-installed Windows can already have 4 Primary Partitions so be careful.. if you force a Fifth in Windows the HDD will turn into a Dynamic disk and won't work with Linux.


Dual Booting is always a good idea for a beginner. There are a lot of Windows Applications that don't have an easy alternative in Linux, or there may be applications or games you are 'used to' in Windows, which you may find hard to run in Linux. (Some Windows Applications can be installed and run in Linux using [WINE]("https://www.winehq.org/about/"). You can see [HERE]("https://appdb.winehq.org/") what applications can run in Linux).

Ubuntu 13.10 is due for release this month. I suggest you install it and familiarize yourself with it. You can install 14.04 when it is out.

EDIT: Installation Guides... (Search the web for more)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html) [info here and the following is old but should give you an idea]
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)


My two cents..

---

### Post by heir4c on 2013-10-06
> All partition creation, deletion and resizing of Windows Partitions MUST be done using Windows tools ONLY.
I did it all the time with gParted and that's going fine.

When creating the Extended Partition you better use gParted because of the difference with the Dynamic Drive Windows used. (I see a tread about that here on the forum last week)

---

### Post by oldfred on 2013-10-06
I think the above cover the partitioning & installing.

But you asked about sharing Firefox & Thunderbird profiles. I have done this for the last 6 or 7 years and have been surprised that even slight version differences have not created issues. But I do try to upgrade Windows versions about the same time as my Ubuntu versions. It was that I did not boot Windows as much, now not at all and Windows versions were getting old.
I also copy my profiles from my desktop to my laptop when I travel. (And laptop was configured for dual use also).
I start Firefox & Thunderbird once, just to create a default profile. Then I edit profile.ini to new path. 
You change IsRelative and change path to mount point you created and new path to profile in your shared NTFS data partition. I create in fstab a mount of /mnt/shared for my NTFS data. And in that partition I have many folders, but one is [COLOR=#000000]mozilla/firefox/profiles [/COLOR]and the xxxxxx.default is the profile from my original Windows install. Not sure where that is with Windows 7. Exactly same process for Thunderbird.

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=[COLOR=#ff0000]0[/COLOR]
Path=[COLOR=#ff0000]/mnt/shared/mozilla/firefox/profiles/wojjex8t.default[/COLOR]

```

If you need help on setting up you shared NTFS with fstab and sharing I can post more info on that. Not difficult but not some editing of fstab required.

 new 
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)
Firefox
[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)

---

