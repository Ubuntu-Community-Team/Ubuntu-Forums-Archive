---
title: "Installing Graphics Drivers Help"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by Mortarius on 2013-01-23
I just decided today on giving Ubuntu a try and so far I love the look of it. I am completely new to all of this and so far have only installed Ubuntu Restricted Extras. When I look at the Details of my pc, I notice that it doesn't display my Graphics Card, it only says 'unkown'. I tried Googling how to install ATI drivers for Ubuntu 12.10, but I don't really understand most of the posts I read. My laptop has an ATI Radeon HD4200.

Another question I have is how do I manage to play World of Warcraft? I heard of Wine and was wondering if I just need to install that to run it?

And lastly, if anyone has some general tips for someone completely new like myself on where to start off it would be highly appreciated.

Thanks for any and all help.

---

### Post by Lightning Dragon on 2013-01-23
Hello and welcome to the world of Linux! ):P

A good place to start to learn about Ubuntu is the [Ubuntu Pocket Guide and Reference book]("http://www.ubuntupocketguide.com/index_main.html") which is a few years old, but the basics have remained the same. There is also the [Ubuntu Manual]("https://wiki.ubuntu.com/ubuntu-manual"), or if you ever become serious about this and would like to learn about it, there is this [here]("http://www.amazon.com/Ubuntu-Unleashed-2013-Edition-Covering/dp/0672336243/ref=sr_1_1?ie=UTF8&qid=1358992940&sr=8-1&keywords=Ubuntu+12.10+book").

As for WINE, yes, it is possible to play WoW through WINE. There is another option, too, called PlayOnLinux and a buyable option called Cedega for like 15$. There are hundreds of sites to read through, but I will direct you to some of the ones I think have the most helpful information on them.

[The Ubuntu Forum Thread of "How to" Concerning World of Warcraft and WINE.]("http://ubuntuforums.org/showthread.php?t=579378")

[Ubuntu World of Warcraft Guide]("https://help.ubuntu.com/community/WorldofWarcraft")

[WoW Wikia Page]("http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine")

And here are some videos and links I found just recently that are worth looking into;
[http://www.youtube.com/watch?v=DIzgUq4Lpa4](http://www.youtube.com/watch?v=DIzgUq4Lpa4)
[http://www.linuxforums.org/forum/wine/62932-howto-installing-world-warcraft-wine.html](http://www.linuxforums.org/forum/wine/62932-howto-installing-world-warcraft-wine.html)
[http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/](http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/)

As for configuring your ATI GPU, I personally cannot offer any assistance, but I can point you towards the Ubuntu ATI driver installation page. :)

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by offgridguy on 2013-01-23
Some great links, Lightning Dragon.

---

### Post by Mortarius on 2013-01-23
Thanks a lot for the reply, I will definitely read through those links and check out the videos.

---

### Post by 3rdalbum on 2013-01-23
Unfortunately ATI no longer makes a driver to work with your graphics card. You are using the open source driver, which is the only one you can use.

If you need better 3d acceleration, you could buy a recent Nvidia graphics card (they stay supported for ages) or install Ubuntu 12.04 instead, which has an older version of the ATI driver that works with your graphics card.

DO NOT attempt to install any other graphics driver on Ubuntu.

---

### Post by Mortarius on 2013-01-23
Okay thanks. I do have another question, when I did this dual boot it  seemed to have copied a lot of files and folders from my Windows 7 OS.  Is it possible to clear out my Ubuntu partition basically like a format?  I only need the files on my Windows 7 OS, not the Ubuntu and there are  way too many to sit and manually delete everyone one.

And while I am on that subject, is there a simple way to backtrack my version of Linux to 12.04?

---

### Post by dcottingham on 2013-01-23
I would guess that the reason you see all the files from Windows is that Ubuntu has mounted your Windows partition. If I have that right, it's not a copy and you'll be sad if you delete it. If you really don't want to see it, you can unmount the partition.

---

### Post by Mortarius on 2013-01-23
When you say unmount, do I just delete the partitions and expand my C: again? What do I delete I have:

100 MB     Healthy (OEM Partition)
14.65 GB   NTFS Recovery
348.36 GB  NTFS OS ( C: )

Then two blank ones: (I'm guessing these are the Ubuntu?)
227.32 GB (Healthy Primary Partition)
5.74 GB   (Healthy Primary Partition)

I'm asking because I want to use 12.04 instead of 12.10 and don't know what the easiest way is to revert to it.

---

### Post by 3rdalbum on 2013-01-23
There is no "revert" or downgrade option. You can boot from the 12.04 CD and install Ubuntu 12.04 onto the existing Ubuntu 12.10 partition, leaving you with 12.04 instead of 12.10.

---

### Post by Mortarius on 2013-01-23
Okay I will give that a try.

Thanks for all the help!

---

### Post by MadmanRB on 2013-01-23
Yeah 12.10 is troublesome with that card, I should know as I have one.
But if it is working I would not worry about it, the only thing that sucks is no HD audio but I can live without.

---

### Post by Lightning Dragon on 2013-01-24
Hello,

Unfortunately you cannot downgrade. You will have to do a fresh install of 12.04 from a burned DVD or through a USB, or perhaps a DVD/CD you can get from the internet or magazines.  Personally, if I were you, I would make the switch to 12.04, but that is just me. (:

---

### Post by Mortarius on 2013-01-24
So I am currently going through the 12.04 install menu and I am at the Installation part. I selected 'Other' and it brought me to a page with /dev/sda devices. What do I need to do to install 12.04 over 12.10. These are on the list:

/dev/sda1 fat16 104mb
/dev/sda2 ntfs    15.7gb
/dev/sda3 ntfs    374.0gb
/dev/sda5 ext4   244.1 gb
/dev/ada6 swap 6.2gb

There are checkboxes next to each in a Format column. Also options:
New Partition Table
Add
Change
Delete
Revert

Sorry for all the questions, I'm just afraid to break something.

*Edit* I also see a drop down at the bottom which lists Windows 7 Loaders and Ubuntu 12.10.

---

### Post by Lightning Dragon on 2013-01-24
Hello,

Are you using one HDD to install this one, or have you installed Ubuntu 12.10 and Windows on *separate* drives each? Or you are looking to erase Windows 7 *entirely*? If so and if you are using the Graphical installation (which are you using?), please see this installation guide;

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

In the guide you will see this image ([http://pix.toile-libre.org/upload/original/1349879961.png](http://pix.toile-libre.org/upload/original/1349879961.png)) and the middle option that warns the installer that choosing that option will "Erase" everything on the HDD. That's the option you use if you want to install over your current Ubuntu and Windows 7. But that will mean you will lose all your files and information.

The top option is if you want to install alongside the other OS.

---

### Post by Mortarius on 2013-01-24
It's only one harddrive and i wish to keep Windows 7 as a dual boot. I am just trying to install 12.04 over 12.10. I think i need to just select the 12.10 Boot Loader from the drop down below, but I don't know if i have to format anything?
And it is the graphical installation from a dvd image.

---

### Post by c2tarun on 2013-01-24
> **Mortarius said:**
> Okay I will give that a try.

Thanks for all the help!

Hey Mortarius, since you are very new to Ubuntu, I want to give you a friendly advice. Please read this book once: [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html) . However it is not necessary at all to read this book, but it'll really help you in understanding the basic working of Ubuntu and how it is different with Windows.

---

### Post by Lightning Dragon on 2013-01-24
Hello,

> **Mortarius said:**
> It's only one harddrive and i wish to keep Windows 7 as a dual boot. I am just trying to install 12.04 over 12.10. I think i need to just select the 12.10 Boot Loader from the drop down below, but I don't know if i have to format anything?
And it is the graphical installation from a dvd image.

I could not find a tutorial or image reference to guide you through installing over a previous Ubuntu alongside Windows. However, I do believe this should be sufficient to your needs.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Please read "Install Ubuntu After Windows" or the entire page if you wish to be sure. The link also links to further guides explaining how to partition drives, if needed, and more. 

If you see an option to install over the previous Ubuntu, then I'm pretty sure that's the correct one to use.  But perhaps another member or staff has a link to such a tutorial, I do not sadly. ):

---

### Post by 3rdalbum on 2013-01-24
At that screen you need to click the Ext4 partition (sda5) and press the Edit button at the bottom. Change the mount point to / (a forward slash). Continue installing and that's it!

---

### Post by audiomick on 2013-01-24
> **3rdalbum said:**
> At that screen you need to click the Ext4 partition (sda5) and press the Edit button at the bottom. Change the mount point to / (a forward slash). Continue installing and that's it!

Yes, I believe this is right. The installer will find the existing swap partition (sda6) and include it in the install.

---

### Post by Mortarius on 2013-01-24
[INDENT]Alright, what should I change the 'use as' option to? With it being set to 'do not use paetition' it wont let me change the mount point. These options are given:
Ext4 journaling file system
Ext5 journaling file system
Ext2 file system
ReiserFS journaling file system
btrfs journaling file system
XFS journaling file system
FAT16 file system
FAT32 file system
swap area

[/INDENT]

---

### Post by Mortarius on 2013-01-24
Also do I check the 'format' checkbox as well?

---

### Post by audiomick on 2013-01-24
For the partition that the OS should be installed to, use as Ext4 and format. For all the others DO NOT FORMAT.

You may have to choose a mount point for the swap, but you can only choose swap as the mount point, so it is not confusing.

---

### Post by seeker.k3 on 2013-01-24
You can see the Windows files, because you can see that partition; they wouldn't be copied across. You can't see Ubuntu when you're in Windows, but you can see Windows from Ubuntu. Mounting just means removing access to that partition. It's a very minor operation that writes a tiny amount of data into the directory called /media. In Ubuntu, the path to the mount points is /media, so for Windows it's /media/OS. You need to look at the table to see what's going on: $ sudo fdisk -l

To mount:
```
 sudo mount -t ntfs /dev/sda2 /media/OS 
```To unmount:
```
 sudo umount /media/OS 
```Notes: the command is umount, not unmount. The file sys type for Windows is network file sys. The OS is a directory in media, it could be called anything you want, but OS would be the default. sda2 might not be correct for you; have to look at you partition table. 

Actually, I don't see any reason why you would bother umount/ing the Windows partition, but you can if you want.

---

### Post by audiomick on 2013-01-24
> **seeker.k3 said:**
> ... Mounting just means [COLOR="Red"]removing[/COLOR] access to that partition. 

Wait on!

Mounting means acquiring access. If the partition is mounted you have access. Removing access would be un-mounting.

---

