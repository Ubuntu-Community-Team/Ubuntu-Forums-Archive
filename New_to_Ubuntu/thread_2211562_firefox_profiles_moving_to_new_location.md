---
title: "firefox profiles moving to new location"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by rbmoler on 2014-03-16
I'm dual booting WinXT and Ubuntu.  I have firefox (and thunderbird) on both and I want to have a shared profiles.

I have a separate disk (E: in windows:  media/data large in Ubuntu.)  I've moved the Firfox profile (and the thunderbird profile) to a location on the E (media/data large) drive (E:\Mozilla\Firefoxprofile\profile\xxxxxxxx.default.  Then opened **profile manager** in a Ubuntu terminal window and created a new profile at that location and deleted the old one.  Firefox opens using that new profile as expected.  I can close and open it a ofter as I want so long as I don't shut down the computer.  When I do that and come back the next day and boot the system into Ubuntu and try to open Firefox it says that I don't have a profile or that it's not accessible.

This doesn't happen with Thunderbird.  Everything works fine in WinXP and Ubuntu for both applications except for this qlitch.  I'm out of my depth here.  I have no idea what I've done wrong because I did Thunderbird the same way with no problem.[IMG]http://ubuntuforums.org/images/icons/icon11.png[/IMG]

---

### Post by Impavidus on 2014-03-16
Is the partition with the firefox profile automatically mounted during boot?

It can be done, there are people on this forum who have set it up the same way as you.

---

### Post by rbmoler on 2014-03-16
The drive is definitely mounted.  I checked by it shutting down Ubuntu and reloading (losing my firefox profile in the process,) so I'm now on my XP computer)  DATA LARGE shows up in the "HOME FOLDER under "devices"  Does media as a prefix have some special meaning that it get attached to the profile location string?

The Thunderbird profile is in the same top folder:  media/DATA LARGE/Mozilla/Thunderbird profile/profile/xxxxxxxx.default

Made a mistake.  The drive is mounted, but **neither** thunderbird nor firefox will find the profile on media/DATA LARGE, the other hard drive.  So I'm really at a loss to get this figured out.  It really makes the most sense to use a common drive to locate such things as profiles and other files such as files written with Libre Office.  

It must be something relatively simple that I'm overlooking,  Sure could use a little help.

---

### Post by rbmoler on 2014-03-17
Arghh!  I need a few hundred hours of total emersion  in Ubuntu/linux to have any idea of what's going on and have even a pidgin-knowledge of it.  The DATA Large wasn't "mounted" (whatever that means).  Obviously creating a profile for Firefox using the profile in the DATA LARGE drive mounted it.  I mounted it by accident when I wanted to look at the information on the drive.

So do I have to "Mount" it every time I load Ubuntu?  Can that be made automatic?

---

### Post by Impavidus on 2014-03-17
We all need a few hundred hours before we're really comfortable with Linux. Maybe more than a few.

You can automatically mount the partition at boot using fstab. See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) and ask any questions. I succeeded at once directly after my first Ubuntu install, although I had used *nix for a bit longer already.

"Mounting" means attaching the file system stored on a partition (or anywhere else) to the existing directory tree to make it accessable.

---

### Post by rbmoler on 2014-03-18
I've spent several hours reading and trying to follow the Fstab explanations.  I've also spent a couple hours more reading another article on the forum intitled Automatically Mount Partitions.  Some of the information seems at variance.  Here's where I am:

The device is listed as /dev/sdb5/  on media/DATA LARGE, type = vfat, uuid = 4133-3f3d

In the fstab discussion uuid's are shown as much longer strings which is a bit confusing.

So I think I should have somenting like this string as the argument for fstab:  /dev/sdb5 media/DATA LARGE vfat user,defaults,dmask=027,fmask=137 0 0

I would use uuid by the fstab author claims that it is string like xxx.yyy.zzz which is nothing like the string that I recorded using **ls -al /dev/disk/by-uuid**/ 

I could just as easily simply mount the DATA LARGE drive when I open Ubuntu, but being a little stuborn about learning new stuff, I'll persevere.

---

### Post by Impavidus on 2014-03-18
The UUIDs may look rather differently depending on the partition type. Most examples assume ext4 partitions.

First make sure the mount point "/media/DATA LARGE" exists. With the partition unmounted (if necessary, right click&#8594;unmount), check for the existence of the directory "/media/DATA LARGE". If it's not there create it: **sudo mkdir "/media/LARGE DATA"**. Any other name will do too, but I think you already instructed firefox and thunderbird to look there. The line to add to /etc/fstab is```

UUID=4133-3f3d    /media/DATA\040LARGE    vfat    rw,noexec,nouser,auto,async   0   0
```The **\040** is there to escape the space character in the name of your mountpoint. There can be some discussion about the right options you want. Maybe someone else has a better idea. Most of them are actually the defaults.

---

### Post by rbmoler on 2014-03-18
Sorry,  I don't know how to check for a directory in Linux.  Couldn't find anything like that.  Maybe there's a sudo command?  Tried  "ls /media/DATA040Large" and "ls /media/DATA Large"
with and without the drive being mounted.  Response was "Cannot access...."

---

### Post by oldfred on 2014-03-18
I would suggest not using spaces in Linux. I quickly learned to use CamelCase, under_score or longnames. It just adds more confusion as you have to escape or quote anything with a space.

I found this to be a good reference. But it only has NTFS as we do not suggest FAT32 anymore. You cannot have any file over 4GB and FAT does not have journal so chkdsk repair will take a long time or not work.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Create mount point, copy & edit example into fstab, check for errors with sudo mount -a
Details in above thread.

In 2009 I converted my shared FAT32 to NTFS. I started using the shared folder for Thunderbird and Firefox back in 2007. While I now do not boot XP, I still have my profiles in my NTFS partition until I totally reorganize. I also copy folders to my laptop when traveling and back to desktop when I return.

UUID=46CD-C9B2 /home/fred/share vfat user,auto,fmask=0111,dmask=0000 0 0

You do not have to make mount point be the same as your label. You can use labels instead of UUIDs, but all that can get confusing. I once mounted my data partition as /mnt/data but labelled it Data which then gave me two different results. Linux is case sensitive where Windows is not.

---

### Post by rbmoler on 2014-03-20
I took **Oldfred**'s advice and converted the shared disk to NTFS.  I also renamed it simply **data** in order to get rid of the space.  I had to use **profile manager** four times to create the profiles for Win XP and Ubuntu, but that's easy to do.

I'm still perplexed about using fstab.  I've read at least 3 expositions of how to get my** data** HD to mount automatically on startup and they all differ from each other and from the advice that I've received from each of you.

One important question has to do with whether or not I already have a mount point.  When I start Ubuntu and look at the home folder my **data** drive is shown and it mounts when I click on it.  If there is no mount point how does it do that?  

If I check for the partition with the command: {  ** ls /media/data ** } it returns the complete list of folders and files on the disk, which according to the instructions on the document  "AutomaticallyMountPatitions"**{[https://help.ubuntu.com/community](https://help.ubuntu.com/community)**/Auto..... } means that the location { ** /media/data** } is already in use and I'll have to make a directory with a different name.  This is very confusing.

Perhaps this bit of information will have some bearing on the issue.  That drive was present and active when I originally loaded Ubuntu onto an empty 320 GB partition on my 1 TB primary HD.  That drive has been visible to Ubuntu from the absolute beginning.

A small light bulb just turned on.  If I query the **data** drive before I mount it from the desktop it returns "no such directory...."  which seems to mean that the mount location is open.  When I make the same query after mounting the drive from the desktop, the list of folders and files is shown, meaning that the location already exists.  So does the location exist or not?  If it exists I assume I should use it in fstab.  If I ran that command  with **media/data **as the argument with the drive already mounted would that cause a problem?

I'm reluctant to do anything for fear I'll perform a royal screw up that I won't be able to undo.  In the meantime I'll just mount that drive at startup.

---

### Post by Impavidus on 2014-03-21
Indeed better to use no spaces in the mountpoint.

If you mount the partition by clicking it in the file manager, a mount point can be created on the fly and removed again when you unmount the partition, manually or during shutdown. If you mount it using fstab, the mountpoint has to exist beforehand. So, if you don't mount the partition from the GUI, the mountpoint doesn't exist on your system.

Create the mountpoint as an empty directory, then edit fstab (backup the old version of fstab) and run **sudo mount -a** to mount the partition. The line you need in fstab is something like```
UUID=xxxxxx    /media/data    ntfs    <options>    0    0
```

---

### Post by rbmoler on 2014-03-22
I finally managed to get my head around this.  I took Oldfred's advice and followed the instructions given by Morbious.  It worked!  I just rebooted and LO! my shared HD is now shown as mounted.  

In the process I learned a great deal about what you can do in the terminal in terms of editing and saving expression and their argument strings.

Thanks to all for helping this 80+ year old novice.

---

