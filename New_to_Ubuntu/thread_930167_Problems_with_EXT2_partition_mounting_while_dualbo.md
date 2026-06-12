---
title: "Problems with EXT2 partition mounting while dualbooting w/ XP"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by mushroomcloudwarrior on 2008-09-25
I've got Ubuntu 8.04 hardy installed on a Dell Vostro 1500,

8 gigs = Ubuntu install
2 gigs = swap
80 gigs = EXT2 partition drive (I use this to share the drive with windows using an ext2 reader. I didn't do the initial partitioning, so don't ask me why i used ext2)
20 gigs = windows install

**The Problem**is that when i boot into ubuntu, it takes about 30 seconds for it to mount it. I know this because the wallpaper's on the EXT2, and it loads only after a while. Amarok seems to 'forget' that my music's kept on here, and i need to run 'rescan the collection' every time i want to listen to music. 

Secondly, when i boot into windows..the reader fails to recognise the disc i.e. when i try to open it, it asks me 'this disc is not formatted, do you want to format it now', now i obviously don't want to format all of my data. Booting into Ubuntu and unmounting the drive seems to do the trick. I've run Kubuntu 7.10 on the same laptop (a year ago) and this system used to work flawlessly, unless there was some problem when ubuntu was shutting down. 

I searched on the forum, but couldn't find anything explaining a solution. 

I also had problems installing nvidia on ubuntu that i couldn't find answers to, should i just start a new thread about that as well?

Thanks guys

---

### Post by neurostu on 2008-09-25
I'm not sure why the EXT2 partition doesn't mount quickly in Ubuntu. As far as winXP goes... Windows does not come with Drivers for the EXT2 and EXT3 filesystems.  Go here: [http://www.fs-driver.org/](http://www.fs-driver.org/) to download drivers so you can open the EXT2 drive in windows.

---

### Post by iansane on 2008-09-25
Lot of things I can't remember but I know it doesn't sound right.

I remember there was some kind of problem with ext2 that could cause it to easily crash and loose everything.

I remember someone with amarok issue but that was removable drive where it mounted different folder everytime.

If it was me and I had a place to back up the files, I would reformat the drive to fat32 or ntfs (readable by windows and ubuntu with no need for other drivers).

As for the nvidia problem I had fun for weeks with that when the kernel kept getting updated every couple of days. Installed nvidia several times with the driver from nvidia. It was over rated so I use nvidia-glx-new now. What is the nvidia prob or are you posting a different post about it?

---

### Post by egalvan on 2008-09-25
> **iansane said:**
> Lot of things I can't remember but I know it doesn't sound right.

I remember there was some kind of problem with** ext2 **that could cause it to easily crash and loose everything.

If it was me and I had a place to back up the files, I would reformat the drive to fat32 or ntfs (readable by windows and ubuntu with no need for other drivers).



Is that ext2 the Linux file system, or the extensible file driver for windows?

ext2 for Linux is solid. it does not easily crash and burn.
It's the recommended file system for boot partitions, grub likes it.
ext2 adds journaling.

I would choose either over FAT32,
FAT32 does not gracefully handle large drives, or large number of directories, or files larger than 4gb.

NTFS has good support under Ubuntu 8.04

ErnestG

---

### Post by iansane on 2008-09-25
egalvan,

As I said I don't quite remember. ext2 linux file system. There was a post about it but I don't know for sure and can't find it. It had something to do with the lack of journaling and unclean shutdown causing data loss. Maybe it was more to do with the kernel at the time. 

I've used fat32 on big drives ignoring the limitations (really before I understood that it had size limitations) and never had a problem.

I guess really with the great support for ntfs, that would be the best one if mushroomcloud decides to format it.

---

### Post by egalvan on 2008-09-25
> **iansane said:**
> egalvan,

As I said I don't quite remember. ext2 linux file system. There was a post about it but I don't know for sure and can't find it. **It had something to do with the lack of journaling and unclean shutdown causing data loss. **Maybe it was more to do with the kernel at the time. 

I've used fat32 on big drives ignoring the limitations (really before I understood that it had size limitations) and never had a problem.

with the great support for ntfs, would be the best one if mushroomcloud decides to format it.

Now there I agree with you, ext2 does NOT like "dirty" shut-downs...
journaling takes care of this, to some extent.
And journaling is really the only difference between ext2 & ext3.

In fact, an ext3 system can be MOUNTED as an ext2, with full read/write. just no journaling (obviously).
Older Linux kernels did this, and this is how the ext2fs driver for XP works.

And NTFS is a good system....
I guess it just chaps my hide to use it. :)

---

### Post by mushroomcloudwarrior on 2008-09-26
Thanks a bunch for the reply guys,

> I'm not sure why the EXT2 partition doesn't mount quickly in Ubuntu. As far as winXP goes... Windows does not come with Drivers for the EXT2 and EXT3 filesystems. Go here: [http://www.fs-driver.org/](http://www.fs-driver.org/) to download drivers so you can open the EXT2 drive in windows.

Neurostu, Thanks, i've already got the exact same driver to read ext2 in windows.

> Is that ext2 the Linux file system, or the extensible file driver for windows?

As i said, i didn't make the initial partitions, but the person who did was well experienced with linux, so i'm going to say it's the linux file system, and as mentioned in the post..i've run it without any issues on kubuntu.

> NTFS has good support under Ubuntu 8.04

I remember not being able to write files to the ntfs partition from linux, or having problems with it in the past. Is the problem more or less sorted now?

> Now there I agree with you, ext2 does NOT like "dirty" shut-downs...
journaling takes care of this, to some extent.
And journaling is really the only difference between ext2 & ext3.

These are proper clean shutdowns! i obviously don't unmount the disc manually. 

My question is, while this has worked in the past, why is it giving me trouble now? 

**Note**: I haven't actually made any effort to mount this partition. Ubuntu detected it by itself and mounts it by itself. I'm guessing i don't have to actively set it up for it to work?

---

### Post by mushroomcloudwarrior on 2008-09-26
> **iansane said:**
> 
As for the nvidia problem I had fun for weeks with that when the kernel kept getting updated every couple of days. Installed nvidia several times with the driver from nvidia. It was over rated so I use nvidia-glx-new now. What is the nvidia prob or are you posting a different post about it?

I'm new to lunux and Ubuntu as a whole, so i've probably done something wrong somewhere. Although, here's what i've experienced:

Installed ubuntu effortlessly, on the first startup, ubuntu asked me if i wanted to install the restricted drivers, then it asked me if i wanted to install the proprietary nvidia drivers. This required a restart, which gave me a screen with nothing but grey lines in the center. This i had to go into recovery mode and 'fix the GUI' (or some command like that) to fix the problem.

I have also tried installing it from the terminal with:

```
sudo apt-get install glx-new
```
(this was after apt-get upgrade/update and build essential

It hasn't worked, i don't exactly remember why but i'll post the output when i get home from work in a few hours. 

Thanks iansane

---

### Post by mushroomcloudwarrior on 2008-09-26
Can i also post here about my frustration for not being able to use the alt+space shortcut for the quick launcher. I've got Launchy setup on my windows too, so i'm really used to using it, and i think it improves productivity/saves time tenfold. When i used Kubuntu, Kopete did an awesome job. However, haven't found anything similar on 8.04, except alt+f3 which does a mediocre job at best. Is there an externam app that i an install to solve this? 

I didn't want to make a new thread about this, however please let me know if i'd be better off with it on a new one. 

**p.s.**In case you're wondering why i've switched from so many things that works to a beta that has problems, basic things like headphone jack and wireless were a problem in that case, which made my laptop unusable. I'm happy living with smaller, less critical issues.

---

### Post by mushroomcloudwarrior on 2008-09-30
Erm,

*Desperately Cries for Help*

:(

---

### Post by iansane on 2008-09-30
Sorry, I got into my own problems with networking and kinda forgot about this assuming the nvidia driver wasn't as important as the ext2 problem and I don't know what is causing the ext2 problem. I was just suggesting reformatting. Someone more knowledgeable will need to help with that.

As far as Nvidia problem, I'm not sure what to do if nvidia-glx-new isn't working. I was talking about the nvidia driver from nvidia.com as far as if you need help with it. It's a pain to install and takes a few steps and manual things to do in terminal. Better off if someone can help figure out problem with the restricted driver on your system cause the other has to be re-installed every time there's a major kernel update.

Oh, and yes problems with ntfs are sorted out. ntfs support is great.

---

### Post by mushroomcloudwarrior on 2008-09-30
> **iansane said:**
> Sorry, I got into my own problems with networking and kinda forgot about this assuming the nvidia driver wasn't as important as the ext2 problem and I don't know what is causing the ext2 problem. I was just suggesting reformatting. Someone more knowledgeable will need to help with that.

As far as Nvidia problem, I'm not sure what to do if nvidia-glx-new isn't working. I was talking about the nvidia driver from nvidia.com as far as if you need help with it. It's a pain to install and takes a few steps and manual things to do in terminal. Better off if someone can help figure out problem with the restricted driver on your system cause the other has to be re-installed every time there's a major kernel update.

Oh, and yes problems with ntfs are sorted out. ntfs support is great.

Thanks for the reply,

It's just that i've waited abotu a year for ubuntu to work, and right now..small things like the ext2 are keeping me from booting into it when i just want it all to just work. I've read others with the same laptop having problems with nvidia, so i've left that for now. 

I'm just going to keep looking, and if anybody knows why this is..please do post on this thread.

---

### Post by iansane on 2008-09-30
I feel your pain. It's all the little things and they seem to get complicated trying to figure out.

The Amarok music issue.

I'm wondering if it has something to do with how the partition gets mounted. I know if something like a usb drive/thumbdrive or anything else that gets mounted as a regular drive is plugged in or removed at different times it will change whether the partition is mounted as /dev/sda1 or /dev/sda2. Even with music folder mounted to the partition in fstab if the /dev/hd? changes it won't mount.

If your using /media/disk or /media/disk-1 or something like that instead of a set mount point like the one below, it could be changing at boot time.

```

/dev/sda6 /vm ext3 defaults 0 0

```

That's in my "/etc/fstab" file and it always mounts the vm folder to that drive because that's where I keep my vm's (virtual machines).

You may already know all this but just in case, do you have your music folder mounted at boot time like that?

---

### Post by mushroomcloudwarrior on 2008-09-30
> **iansane said:**
> I feel your pain. It's all the little things and they seem to get complicated trying to figure out.

The Amarok music issue.

I'm wondering if it has something to do with how the partition gets mounted. I know if something like a usb drive/thumbdrive or anything else that gets mounted as a regular drive is plugged in or removed at different times it will change whether the partition is mounted as /dev/sda1 or /dev/sda2. Even with music folder mounted to the partition in fstab if the /dev/hd? changes it won't mount.

If your using /media/disk or /media/disk-1 or something like that instead of a set mount point like the one below, it could be changing at boot time.

```

/dev/sda6 /vm ext3 defaults 0 0

```

That's in my "/etc/fstab" file and it always mounts the vm folder to that drive because that's where I keep my vm's (virtual machines).

You may already know all this but just in case, do you have your music folder mounted at boot time like that?

Actually, i don't know this already. I'm just going to boot into Ubuntu and check. Although, my 80 gig does seem to mount every time, just a little late..

---

### Post by iansane on 2008-09-30
ok well let me know and I can tell you how to make your music folder mount to the partition with music and then you can tell amarock to use that folder specifically instead of scanning the whole system.

---

### Post by mushroomcloudwarrior on 2008-10-02
> **iansane said:**
> ok well let me know and I can tell you how to make your music folder mount to the partition with music and then you can tell amarock to use that folder specifically instead of scanning the whole system.

Here's my fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=52246785-44fb-44e6-8869-80771587d8dc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=671acba3-c93f-4b68-90ed-02307c495ab4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I've already set Amarok to look in one specific folder for the music (/media/local disk/music)

If it helps, the partition is called 'Local Disk' every time i boot ubuntu. Although, i'm guessing you're referring to the mount point of the partition.

Also, does my fstab file look OK?

---

### Post by iansane on 2008-10-02
Hey, just got in and turned on the computer.


If you type in terminal: 

```

sudo fdisk-l

```

It should show you a list of your drives/partitions.

Like mine here:

```

ian@lotus-control:~$ sudo fdisk -l
[sudo] password for ian: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c0967

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9738    78220453+  83  Linux
/dev/sda2            9739       19464    78124095   83  Linux
/dev/sda3           19465       38913   156224092+   5  Extended
/dev/sda5           19465       19707     1951866   82  Linux swap / Solaris
/dev/sda6           19708       31865    97659103+  83  Linux
/dev/sda7           31866       38913    56613028+  83  Linux
ian@lotus-control:~$ 

```

If the drives you mentioned are the only ones, the one with "*" under boot is your ubuntu, then there's the "swap"partition, ntfs,windows,or uknown for your windows partition. I can't remember that part and I don't have windows right now but you should be able to tell which one it is. then there will be one that is the drive with the music on it.

I don't see an fstab entry for the ext2 drive so it is probably mounting differently every time. To make it mount automatically to the same folder every time. make or choose the folder you want to use in ubuntu. I'm guessing /home/yourname/music or what ever folder you want.
Then put this in a new line in your fstab.

```

/dev/sda? /path/to/your/folder ext2 defaults 0 0

```

replace the "?" in sda? with the right number which you will get with the first command that lists the partitions and drives.

This way every time you boot, /home/yourname/music or what ever will automatically be mounted to the music in the ext2 partition.

If you tell amarock to build the collection from that folder, it should stay the same everytime.

---

### Post by iansane on 2008-10-02
Oh, and there's something like fdisk -l that shows the file system (ie. ext2, ext3, ntfs,etc.) but I'm looking for it. If you have trouble figureing out which one it is you can always install gparted and use it to see them in a gui with file system shown.

---

### Post by mushroomcloudwarrior on 2008-10-03
> **iansane said:**
> Oh, and there's something like fdisk -l that shows the file system (ie. ext2, ext3, ntfs,etc.) but I'm looking for it. If you have trouble figureing out which one it is you can always install gparted and use it to see them in a gui with file system shown.

Hey,

I couldn't decide which partition i was looking for using 'fdisk -l' so i installed gparted,and found that it was sda5 that i was looking for, and that the drive was ext3 (and not ext2 as i'd mentioned before). Anyway, i changed the /etc/fstab file according to your instructions and it loads up now. I then booted into windows without unmounting the drive and could access the ext3 partition as well! 

Such a delight! 

Thanks a lot for your help iasane, really appreciate it.

However, everytime Ubuntu boots up now, i get the 'local disk' folder on the desktop, is that normal?

---

### Post by iansane on 2008-10-03
Not sure where the local disk folder is coming from. Is that something from amarok? How did you set up that or was it already set when you got the computer?

It's not anything in fstab so I don't know.


You'll have to ask around about that. If it's not amarok then the person you got it from might have set something up.

Also, don't think it had anything to do with the problem from windows but who knows? Not me :-)

Wish I had more knowlege. Glad I could help with fstab though.

---

### Post by mushroomcloudwarrior on 2008-10-03
> **iansane said:**
> Not sure where the local disk folder is coming from. Is that something from amarok? How did you set up that or was it already set when you got the computer?

It's not anything in fstab so I don't know.


You'll have to ask around about that. If it's not amarok then the person you got it from might have set something up.

Also, don't think it had anything to do with the problem from windows but who knows? Not me :-)

Wish I had more knowlege. Glad I could help with fstab though.

Rebooted into Ubuntu again, i still have the Local Disk icon on my desktop, trying to unmount is gives me an error saying only root can unmount it, i'm guessing this is a result of the changes in the fstab file. 

I've got it working like i wanted to though, thanks again for the help!

I've downloaded Gnome-launchbox recently, it doesn't really appear in the application menu, it's strange because even Gparted doesn't appear in the menus. When i do manage to start the launchbox using the terminal window, i can't set shortcuts on it or anything, know anything about this error?

---

### Post by iansane on 2008-10-03
don't know about gnome-launchbox but gparted is under system>administration>partition editor

---

### Post by mushroomcloudwarrior on 2008-10-03
I've found 'Gnome-do' that does what i need to.

Just for someone browsing this thread wanting to get an application similar to launchy (windows), quicksilver (mac) or katapult (KDE). 

```

sudo apt-get install gnome-do
```

You'll probably want to add it to your startup after having installed it. 

```
Add it to your System > Preferences > Sessions: gnome-do --quiet (for autostart at login)
```

You can call it using [win] + [space] after this.

Found here: [http://ubuntu-tutorials.com/2008/03/05/how-to-install-gnome-do/](http://ubuntu-tutorials.com/2008/03/05/how-to-install-gnome-do/)

---

