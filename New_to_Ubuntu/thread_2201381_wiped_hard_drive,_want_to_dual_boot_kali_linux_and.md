---
title: "wiped hard drive, want to dual boot kali linux and ubuntu using ubuntu live cd"
date: 2014-01-24
forum: New to Ubuntu
---

### Post by monsterwizard on 2014-01-24
Right now I'm using an Ubuntu live cd and I have wiped my hard drive and I want to dual boot both Ubuntu and Kali Linux equally onto the hard drive. 
How do I properly go about doing this? I mean, I'm not sure how to partition my hard drive. Do I just devide it into two, then somehow put Ubuntu onto one, and Kali Linux onto the other? and if so, how, and in what way do I have to partition each part of my hard drive? Do I have to have two swap partitions, one for both? and what sizes and what type of partitions do I have to make for each? 
I really am a beginner at this stuff, and I don't want to have to keep guessing and walking blindly through this. I seached google and these threads, and even though I found similar situations, I cant find someone who has done the same thing I want to do.
I hope someone can help me,
MrWizard

---

### Post by sudodus on 2014-01-24
Do you intend to hibernate and then switch distro? In that case you need two swap partitions, each of the same size (or larger) in Mibibytes (base 2 or 1024) as the RAM. Otherwise it will probably be enough to have 1 GB RAM shared for both systems.

I would recommend that you do *not* hibernate.

Use ***gparted*** when booted from the live CD to create your partitions. Make more space for the system, where you intend to keep more data. Alternatively you can have a separate ***data*** partition (also ext4, if you are not using Windows or MacOS). The minimum size of the root partitions is 8 GB, but if there is space, I would recommend 16 GB or more for each of them.

If you specify your computer, you can get better advice also concerning the version and flavour of Ubuntu.

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- HDD (size)

---

### Post by monsterwizard on 2014-01-24
I see that I somehow posted the image wrong, and since I am using a live cd, when I try to edit the post, firefox freezes and I can't delete all that image data. So I have no choice but to leave it there and put my laptop info here in another post. 
Memory: 3.6 GiB
Processor: AMD E-300 APU with Radeon(tm) HD Graphics x2
Graphics: Gallium 0.4 on AMD PALM
OS type 32 bit (I originally had a Windows 8 OS installed, so it can have 64 bit, but I opted with 32, having only 3.6 GiB ram right now)
and I have 300 GiB HDD
I'm very sorry for the inconvienience, maybe an admin can take out that pic data for me? Im very very sorry.

---

### Post by sudodus on 2014-01-24
Try to attach the picture instead (you can edit the post to remove the wall of text, that should have been a picture). [COLOR=#ff0000]**Go Advanced**[/COLOR] and **manage attachments**.

It should be enough with 1 GB swap for normal usage. If you know that you will edit big photos or videos, or if you want to have many tabs open when browsing, you can have more. You notice when it starts heavy swapping (everything will be very slow), so you can close some tabs in the browser ...

With a 300 GB hard disk, you can have 20 GB for each root file system, and one 1 GB (or 2 GB) swap partition in common. It leaves a lot of space for the data partition.

You can let one of the 20 GB partitions be a primary partition. Use the rest of the drive to make an extended partition, and create logical partitions inside that extended partition. Start with swap at the beginning of the swap partition.

[ubuntu.....20][extended[swap.1][kali.....20][data ............................................................................ 238]]
(sizes in Gibibytes, base 1024)

In the installer you select ***Something else*** at the partitioning page, and specify manually the partitions you have created. You need not specify the data partition.

*Edit*: To find out about the CPU and RAM size (and other hardware) you can use

```
gksudo lshw|less
```

Exit from less with q.

---

### Post by nothingspecial on 2014-01-24
You can use the "Report Post" button to alert the staff to a something that needs their attention.

---

### Post by Elfy on 2014-01-24
> **monsterwizard said:**
> I see that I somehow posted the image wrong, and since I am using a live cd, when I try to edit the post, firefox freezes and I can't delete all that image data. So I have no choice but to leave it there and put my laptop info here in another post. 
Memory: 3.6 GiB
Processor: AMD E-300 APU with Radeon(tm) HD Graphics x2
Graphics: Gallium 0.4 on AMD PALM
OS type 32 bit (I originally had a Windows 8 OS installed, so it can have 64 bit, but I opted with 32, having only 3.6 GiB ram right now)
and I have 300 GiB HDD
I'm very sorry for the inconvienience, maybe an admin can take out that pic data for me? Im very very sorry.

we've dealt with the drag and drop issue.

You can post images - just use the Manage attachements - not drag and drop

---

### Post by The Cog on 2014-01-24
I took the liberty of jailing the failed attachment post because it's clearly not wanted and it's very big.

---

### Post by sudodus on 2014-01-24
> **monsterwizard said:**
> I see that I somehow posted the image wrong, and since I am using a live cd, when I try to edit the post, firefox freezes and I can't delete all that image data. So I have no choice but to leave it there and put my laptop info here in another post. 
Memory: 3.6 GiB
Processor: AMD E-300 APU with Radeon(tm) HD Graphics x2
Graphics: Gallium 0.4 on AMD PALM
OS type 32 bit (I originally had a Windows 8 OS installed, so it can have 64 bit, but I opted with 32, having only 3.6 GiB ram right now)
and I have 300 GiB HDD
I'm very sorry for the inconvienience, maybe an admin can take out that pic data for me? Im very very sorry.

I think your computer will work better with a desktop environment with a smaller foot-print than standard Ubuntu, I suggest Xubuntu (or Lubuntu if you want a real light-weight system that is very fast and responsive, but also simpler and not so fancy). This is particularly true if you have problems with the graphics. There are proprietary drivers to install for some Radeon graphics chips, but not all of them.

I think it is OK (good) to use a 32-bit operating system. If you have a fast internet connection, I suggest that you download Xubuntu and test it live before deciding what to install. Otherwise you can install from the present iso file and install xubuntu-desktop later on. The engine behind the desktop environment is the same anyway in all Ubuntu flavours.

---

### Post by monsterwizard on 2014-01-24
Ok, this is what I think you mean to the best of my abilities, and I hope I'm doing the picture right,
ok, not sure if the pic uploaded, I'll post and edit if I did it wrong.

---

### Post by monsterwizard on 2014-01-24
Oh, and thank you guys for your help and patience, I hope I don't get too many sighs!

---

### Post by sudodus on 2014-01-24
> **monsterwizard said:**
> Ok, this is what I think you mean to the best of my abilities, and I hope I'm doing the picture right,
ok, not sure if the pic uploaded, I'll post and edit if I did it wrong.

Good attachment :-) You are heading in the right direction, but the kali partiiton should be grown to 20 GB. After that you can create a data partition of the rest of the space.

And you should avoid spaces in ***labels*** as well as in file names. It is enough with ***ubuntu*** and ***kali*** and ***data***. Change that before leaving gparted.

Click on the ***tick icon*** in order to execute the selected commands (to actually edit the partition table).

---

### Post by sudodus on 2014-01-24
> **monsterwizard said:**
> Oh, and thank you guys for your help and patience, I hope I don't get too many sighs!
No worries. We are here to help. The worst case at the Ubuntu Forums is an opening post and after that silence.

---

### Post by sudodus on 2014-01-24
I see another issue: You should make ***ext4*** file systems, not ext2. That can be fixed either in gparted or in the installer at the partitioning page. I suggest that you do it in gparted, it is more visual so it is easier to know what you are doing.

---

### Post by monsterwizard on 2014-01-24
so does the image I posted contain what you were thinking up?

---

### Post by sudodus on 2014-01-24
Yes, but there are a few things to modify (and you should add the data partition, also with ext4 file system).

---

### Post by monsterwizard on 2014-01-24
Ok, so here I am trying  to implement the instructions you gave me, and I have a problem already. here is the picture,....
no root, how big, and where do I put it?

---

### Post by sudodus on 2014-01-24
A. I suggest that you quit the installation and go back to ***gparted*** because you forgot to modify those few things described in my previous posts.

1. The kali partition should be 20 GB, not 2 GB.

2. You have not created any data partition.

3. The file systems need to be changed to ext4 (formated).

*. I can not see if you changed the labels to contain no spaces. Please check that too.

B. Then go back to the installer and ***Something Else***.

1. Select the relevant partition (/dev/sda1 with label ubuntu for Ubuntu), click on ***change ***and select root partition. If you formated it to ext4 in gparted you need not format it now. Otherwise do that too.

2. Then make sure that the bootloader will be installed to /dev/sda

---

### Post by oldfred on 2014-01-24
When you use Something Else and have partitioned in advance you need to click change button to choose / (root) partition, and format. If formatting during install, you do not have to format in gparted, but does not really matter unless you are reusing an existing /home and then you would NOT format it or data would be erased.

---

### Post by monsterwizard on 2014-01-27
OK, I think I have it right this time, I re labeled them to have no spaces, I resized the partition to be 20 GiB, labeled sda1 as root, I believe I have a proper data partition, made the partitions ext4 instead of 2, and made the bootloader to be installed to /dev/sda.
So just to be sure, here is the attachment, before I install.

---

### Post by sudodus on 2014-01-27
> **monsterwizard said:**
> OK, I think I have it right this time, I re labeled them to have no spaces, I resized the partition to be 20 GiB, labeled sda1 as root, I believe I have a proper data partition, made the partitions ext4 instead of 2, and made the bootloader to be installed to /dev/sda.
So just to be sure, here is the attachment, before I install.

Yes it looks good now :-)

---

### Post by monsterwizard on 2014-01-29
Ok, now that I have the partitioning scheme set up well, and I have a bootable live Kali Linux DVD, I'm not sure how to go about dual booting it. Lol. In the installation process, when I choose guided the only option I have is to install it to the whole hard drive, which of course would wipe Ubuntu off of it. Plus, before the installation progam opens, it says I have the wrong kernel for installing it to the hard drive. So I tried going the the Manual installation process, but I just couldn't figure out what to do.

---

### Post by sudodus on 2014-01-29
It is possible to select 'Something else' at the partitioning table when installing Ubuntu, and select manually which partitions to use for the root file system and swap.

I hope you find something similar in the installer of Kali. I don't know Kali and how to install it. If you cannot find out how to  install it for dual booting, you can reverse the process and install  Kali first, and then edit the partition table and finally install  Ubuntu.

---

