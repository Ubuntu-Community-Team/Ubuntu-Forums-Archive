---
title: "Trouble installing Ubuntu alongside Windows 7 (Option missing)"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by Pac1234 on 2012-03-09
Hello, fine lads: 

I'm new to this forums and I'm here to seek advice on how to install both operating systems in my laptop. I am currently studying physics and need programs such as fortran, gnuplot, vi... etc. in order to do some research and assignments.

I have an HP Pavilion g4 laptop.
I am using a CD to install Ubuntu 
I want to have a dual boot option 
Windows 7, 64-bit
My concrete problem is this:

When trying to install Ubuntu, the "Install alongside Windows 7" option is missing. I have read in this forum that this is because of the lack of free space on the Hard Disk (Allocations, partitions and fragmentations)

How can I successfully solve this issue? 

I know that I need to somehow create/free space, but I don't know how to do it or what program I need.

Please, can anyone help me?

Thanks in advance.

---

### Post by audiomick on 2012-03-09
It is indeed fairly common that a laptop or netbook that has Win7 on it already has 4 primary partitions on the drive.

I can't say for sure that this is your problem, but let's assume it is.

If you can see there is an option in the installer missing, then you can presumably boot into the live environment. That is the "try without changing" option.

Do that and start Gparted. That is a partitioning program that can tell you what is on your drive. Have a look and see how many partitions there are. On a Win7 install, I gather it is fairly common to have
2 partitions that are directly related to the Win7 install
A recovery partition
A partition containing tools from the manufacturer of the laptop.

I don't remember exactly, but I think I blitzed the recovery partition on this netbook to make room for an extended partition to enable me to make logical partiitions for the Ubuntu install. That is the principle, at any rate. Have a look what is there, maybe use the "create a recovery medium" facility (I didn't), and decide which of the existing partitions you can afford to get rid of.

If there really are already 4 primary partitions on the drive, then you do have to get rid of one of them in order to install anything else on there. Either that or get rid of the Windows install completely.

---

### Post by acimi66 on 2012-03-09
From someone who has just began using Ubuntu, I highly recommend making a backup of your windows BEFORE doing the duel boot. My WIN7 never really ran the same after doing a dual install. Which is fine because I was able to make a complete switch.

Try running from the live CD and take a look at Gparted. I don't know if you can actually make the change without losing data.

let us know if you are to run it on the live CD.

---

### Post by Pac1234 on 2012-03-09
Thank you for providing me with your advise. Anyway, on to business:

Well, through the use of Gpart I found these:

Partition      System Archives       LABEL               SIZE               Used           Free        Options

-/dev/sda1      ntfs                       SYSTEM            199.00MiB    66.59MiB   132.41MiB   boot
-/dev/sda2      ntfs                                                 581.34GiB     79.38GiB   501.96GiB   
-/dev/sda3      ntfs                       RECOVERY       14.54GiB     12.74GiB       1.80GiB
-/dev/sda4      fat32                     HP_TOOLS       103.34MiB    13.79MiB     89.55MiB  lba
-not allocated not allocated                                        1.00MiB     

So apparently I have 5 items (partitions). 

Now, based on your input, I need to get rid of at least 2 and create enough free space for a successful installation, am I right? Also, a backup of ALL items is most recommended, am I correct? 

In any case, I would appreciate if someone could tell me how to do the above things. 

Thanks-

---

### Post by crf on 2012-03-09
Pac1234. [https://help.ubuntu.com/community/HowtoResizeWindowsPartitions]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions").

When I installed Ubuntu (on Vista, but Windows 7 would be the similar), I used windows partition editor to shrink the windows partition to free up space. I think this is easiest, as you are using windows' own tools to resize a windows partition.

If you've made enough free space, the live CD will be able to create a new partition using that space, and install Ubuntu onto it.

---

### Post by audiomick on 2012-03-10
> **Pac1234 said:**
> Thank you for providing me with your advise. Anyway, on to business:

Well, through the use of Gpart I found these:

Partition      System Archives       LABEL               SIZE               Used           Free        Options

-/dev/sda1      ntfs                       SYSTEM            199.00MiB    66.59MiB   132.41MiB   boot
-/dev/sda2      ntfs                                                 581.34GiB     79.38GiB   501.96GiB   
-/dev/sda3      ntfs                       RECOVERY       14.54GiB     12.74GiB       1.80GiB
-/dev/sda4      fat32                     HP_TOOLS       103.34MiB    13.79MiB     89.55MiB  lba
-not allocated not allocated                                        1.00MiB     

Ok, it's Hewlett Packard laptop, I gather. Anyway, I've seen people post pretty much exactly this setup a number of times.

> 
So apparently I have 5 items (partitions). 

Now, based on your input, I need to get rid of at least 2 and create enough free space for a successful installation, am I right? Also, a backup of ALL items is most recommended, am I correct? 
No, four partitions, all primary, and a tiny little bit of free space. The free space is more or less irrelevant. I don't know exactly what the reason for it is, so before I tell you any rubbish, I'll just say that there is nearly always a MB or so of free space in there somewhere, and it is nothing to worry about.

You don't need to get rid of two partitions, you only need to get rid of one. You can have four primary partitions and any given drive, or up to three primary and one extended. The trick is, you can make a heap of logical partitions in the extended one.

That link from crf is good. Look at these two as well
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Also, the advice from crf to use the windows tools to change the windows partitions is also reasonable. A lot of people advise this, although many also say that using Gparted is also safe. My view is, the windows tools are there, they work and you are not trying to remove Windows completely, so why not use the tools they provide?

You should
BACK UP ANYTHING IMPORTANT BEFORE YOU START
Playing around with partitions is always slightly risky. For instance, what if you have a power out right in the middle of the operation? Do the backups.

De-fragment the Windows partition you want to re-size. If you have been using the computer for a long time, you might even want to do this twice. It is not a bad idea to take the oppurtunity to get rid of any rubbish that is in there, old files and stuff, before you do this. Neatness is a virtue... ;)

Do your re-size.

Re-start the computer into Windows once or twice, and let it do any disk check stuff it wants to do. When you are satisfied that Windows is happy, you can go ahead.

Getting back to the partitions you have, and what you could delete:
the first two, sda1 and sda2 are the ones that you need to keep for Win7 to run. As far as I know, you need them both, although I can't recall exactly what the smaller (first) one is for. Suffice to say that you need it.

The recovery partition is a candidate for removal. I am not completely informed about this. My attitude to the Win7 on my netbook was "If the windows gets corrupted, it is gone for good", so I don't need a recovery partition. I believe, without being able to say for sure, that if you use the Windows facility to create a recovery medium, you can safely remove this partition and still be able to recover your windows. Maybe someone else can say something about this point?
Whatever, I am fairly sure of this: If you install Ubuntu, or any other OS, next to the Windows and then later run the Windows recovery program that uses the recovery partition, your second OS will be gone. The Windows recovery function puts the computer back to the state it was delivered in, i.e. without the dual boot and without any partitions you may have created. Sure, if your are absolutely dependant on the Windows install for something, this might be an option. I would consider it on my Laptop, which I need for work. On the netbook, where I haven't even started the Windows in nearly a year, the Ubuntu install has priority, so I would definitely do without Windows before I use the Windows recovery option. Horses for courses.

The fourth partition, HP tools, is also a candidate for removal. The trick is to find out what is in there, and if your really need it. I can't say anything definite about this, other than that I have seen a few posts here claiming that you can do without that partition, i.e. specifically a partition called "HP tools" in threads dealing with pretty much the same questions you have. I think you may be able to look at what is on there with the file manager when you boot into the live environment. See if you can work out what is on there. Try searching the internet a bit. This partition is common. I am sure someone somewhere will have written about what is on there. If you are really lucky, HP may have documented it somewhere on their web site, but I wouldn't count on it. Whatever, very broadly speaking, what is in there is things that HP think are really useful and that you should have on your computer. Whether you agree about this or not is a matter of question. ;)

I hope this helps a bit.

---

### Post by oldfred on 2012-03-10
Not sure I can add much to audiomick's post.

I have seen users both delete recovery and HP tools. It becomes your choice. Some have said they backed up HP tools and restored to a logical partition and they still worked. Many make the recovery DVDs but you may only need if you want to later sell computer with Windows 7 as installed. Otherwise you have to reinstall & reapply all updates. A full backup then is better for recovery of Windows.

You should also make a Windows repairCD or USB.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Some more links if interested.
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by bkratz on 2012-03-10
> **Pac1234 said:**
> Hello, fine lads: 

I'm new to this forums and I'm here to seek advice on how to install both operating systems in my laptop. I am currently studying physics and need programs such as fortran, gnuplot, vi... etc. in order to do some research and assignments.

I have an HP Pavilion g4 laptop.
I am using a CD to install Ubuntu 
I want to have a dual boot option 
Windows 7, 64-bit
My concrete problem is this:

When trying to install Ubuntu, the "Install alongside Windows 7" option is missing. I have read in this forum that this is because of the lack of free space on the Hard Disk (Allocations, partitions and fragmentations)



How can I successfully solve this issue? 

I know that I need to somehow create/free space, but I don't know how to do it or what program I need.

Please, can anyone help me?

Thanks in advance.


I think this would be worth reading

[http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/What-is-inside-the-quot-HP-Tools-quot-partition/td-p/216428](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/What-is-inside-the-quot-HP-Tools-quot-partition/td-p/216428)

---

### Post by Pac1234 on 2012-03-11
OK, so after a LOT of tries and experimentation I finally managed to successfully install Ubuntu (Guess where I'm typing this from!). 

Here's what I had to do (GO trough) in order to get this magnificent OS working:

1- First, I created a backup by following these steps: [http://www.howtogeek.com/howto/4241/how-to-create-a-system-image-in-windows-7/](http://www.howtogeek.com/howto/4241/how-to-create-a-system-image-in-windows-7/)

2- Made a partition by resizeing:

- I followed these steps: [https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

-Now, here comes the tricky part: By following the steps above, I shrank the size of my dev/sda2. (I had 582GB of free space and left it at 300GB)

-I ONLY shrank the size. I NEVER EDITED OR LABELED THE NEWLY SHRUNK VOLUME. All of this by using the very same tools Windows provides. 

-After that I ended up with 5 partitions.

3- By using a CD, I live-booted Ubuntu by following these steps: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

BUT STOPPED AT NO.4^

-At No.4, I still didn't have the "Install Ubuntu alongside Windows 7" option, so I clicked the "Something else" option.

-^ This led me to an editor for partitions. In it, I deleted/removed the "HP_TOOLS" partition (dev/sda/4). I kept the dev/sda1 dev/sda2 (Vital for running Windows) and dev/sda3 (The Recovery Partition). 

- Then, I merged the newly freed space (This happens after deleting the sda/dev4 partition) with the unedited and "useless free space" (The one I got by shrinking my sda/dev2 partition in Windows).[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

-I chose the type "ext4" format and chose to use the combined free GB (Around 250GB if I remember correctly); which I got after adding up the newly freed space and the "unused" partition I made priorly in Windows.

-^ I chose the option of "Forcing it to be a primary partition"

-I clicked the option to continue and a warning told me that it was not a very good option, since I wasn't using all the available free space and that some resources could end up being unused ("To better make use of the physical space allocated in the HD" if I remember the wording correctly)

-^ I ignored this warning and proceeded with installation of Ubuntu.

-After 1:30 hours approx (I updated all the packages and drivers by following the "Download Ubuntu" instructions above posted). 

-Rebooted around 3 times to corroborate that I had the dual boot options and that I could use Windows and Ubuntu without problems and... Success! I made it =D

Important: After shrinking the partition in Windows I rebooted Windows 2 times as the instructions above posted indicated. VERY IMPORTANT.

-If for any reason, once you finish installing Ubuntu, you turn on your computer again and find yourself with a black screen of death do this:

-Before turning off your PC and killing yourself, insert the live Ubuntu CD in your tray and get it ready.

-Restart the PC (With the CD already inside) and press "ESC" for the boot option menu.

-Press F9 for the "Boot Options Menu" and re-install Ubuntu by following the step 3 above.

-After that, everything resolved and I had no problem whatsoever.

I want to thank all of you for providing me with the necessary input and for posting the helpful links that guided me through this ordeal (Over 30 hours trying to get a successful installation and not messing up Windows 7... I suck at this, I know).

If someone finds a problem with HP laptops, this might help. 

Always read the provided links in this post and take the most conservative precautions/route. 

IF ALL ELSE FAILS, DO THIS:[http://www.howtogeek.com/howto/7702/restoring-windows-7-from-an-image-backup/](http://www.howtogeek.com/howto/7702/restoring-windows-7-from-an-image-backup/)

Have a nice day and again, thank you all. This is a truly nice community. I'm going to start to learn how to use Linux for my daily commutes. I can see now the great advantages it offers, aside from science and free-software. THE POSSIBILITIES SEEM ENDLESS WITH LINUX!

---

### Post by audiomick on 2012-03-11
Thanks for the resumee. I often wish people would take the time to do this.

One thing: your install is up and running, so don't change it for now. However, next time, think about making the partition that you forced to be a primary into an extended instead. Then you have the option to add another partition inside that at a later date without having to erase one of your 4 primaries again as you did this time.

---

