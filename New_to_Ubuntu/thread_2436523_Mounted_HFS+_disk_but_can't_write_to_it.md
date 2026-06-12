---
title: "Mounted HFS+ disk but can't write to it"
date: 2020-02-07
forum: New to Ubuntu
---

### Post by itaki on 2020-02-07
I am moving my master raid from my Mac to my new Ubuntu box. I installed HFSprogs and mounted the drive with

```
sudo mount -t hfsplus -o force,rw /dev/sdb2 /media/me/mountpoint 
```
and it mounts fine, but I can't write to it unless I use sudo.

What I mean is that a file manager can't copy to or create any files unless I open the manager with 
```
 sudo nautilus
``` 
And of course I can write to it in terminal by using sudo.
But both of these, especially the first one, seems like bad practice.

The other option is I can think of is
```
sudo chmod 755 -R /mountpoint
```
But there are literally millions of files on this raid and that could take days. And for the record also seems like bad practice.

Anyone familiar with this or have recommendations?

---

### Post by yancek on 2020-02-07
> But both of these, especially the first one, seems like bad practice.
 

Disagree with that.  Linux is designed and always has been as a multi-user system so that the default is to give a normal user write privileges only to the /home/user directory.  If you have partitions on an external drive, you either need root or you need to change ownership to your user for whatever directories/files you want to write to.

---

### Post by itaki on 2020-02-08
Thanks for your help!
Sorry for my ignorance, but I'm new to Linux.
How do I change the entire drive to be owned by me?

---

### Post by coffeecat on 2020-02-08
> **itaki said:**
> How do I change the entire drive to be owned by me?

You could use chown, but **please don't**. I think that would be a very bad idea.

Let's step back a bit.

You say, "I am moving my master raid from my Mac to my new Ubuntu box." If you are moving from MacOS to Ubuntu, you really need to migrate all your data to a native Linux filesystem. I admit I'm out of date, but I don't believe much has happened recently for hfs+ support in Linux, and that it's not reliable. It's significant that you have had to use the force option to get read-write access. I can't find the reference now, but I do remember reading that using the force option when mounting hfs+ risks data corruption. 

I know this would involve a lot of time, and perhaps expense, but "millions of files" sound as though they are more valuable than the time and expense. Do you have backups beyond your master raid?

One other point:

[quote=itaki]```
sudo nautilus
```[/quote]

Please don't. Using sudo with graphical apps can corrupt your environment by allowing root to take ownership of critical files that you must own.

And yet another point. 

[quote=itaki]And of course I can write to it in terminal by using sudo.[/quote]

In MacOS, if your files and folders are owned by the first created user, they will have a UID of 501 (if I remember correctly). In Ubuntu it will be 1000. Which is why using elevated permission in the terminal works. I think - but depending on the cp options you used, I'm not 100% certain - you may find that files you have written to the RAID from Ubuntu with "sudo cp" will retain their 1000 UID, but all the files written from MacOS will be UID=501. Which, if that is the case, is a bit of a mess you will have to tidy up after you've migrated your data to a Linux filesystem.

---

### Post by yancek on 2020-02-08
Using chown would I agree be a very bad idea for an entire drive.  Might be alright on specific directories although I'm not sure how much that would help in your case.    So if you are going to have your RAID setup on Linux, best to use a native Linux filesystem as suggested  as I expect you will have nothing but problems trying to use Apple filesystem from LInux.  There is little incentive for Linux developers to write software to deal with Apple filesystems since it has such a small share of the market, similar to Linux.

---

### Post by itaki on 2020-02-09
Thank you for your replies. You both are probably right in that the best thing to do is transfer everything off the raid, reformat in a linux specific format and copy everything back. Though that is a way bigger and different problem then just using HSFProgs. Which format would you recommend for a 28 TB storage device?

I'm still going to be faced with a similar issue however. In my work, video post production, I get handed a lot of HFS+ drives as Macs are industry standard on set devices. I calculated that moving to Ubuntu would be a mild risk just for data handling. However, in the planning phase it seemed the benefit of incorporating Nvidia GPUs outweighed the risk. However, if working with HFS+ drives is going to always be an issue, maybe I should rethink some choices.

---

### Post by TheFu on 2020-02-09
HFS+ will always be a 3rd-class file system. Expect that.  If you use it only as import media, perhaps it will be fine.

NTFS, FAT32, exFAT are 2nd-class file systems.  Every once in a while, I have to reformat my NTFS disk due to corruption from the video device that mandates I use NTFS and doesn't support any Linux native file system.

For 28TB of storage, I'd suggest using ZFS with multiple volumes based on the size of your backup disk capabilities.  Backup disks shouldn't cross storage devices.  I've standardized on 4TB backup disks, so none of my primary storage volumes is larger than that.

RAID is not a backup.  I have 32TB of storage, but 16TB is primary and the other 16TB is backups. Primary storage is SATA/eSATA connected. Backup storage is USB3.  For media, RAID doesn't get used, but I'm not making a living with it.  

If this is your living, I'd suggest you stay on Apple and introduce Linux NFS with ZFS or LVM+ext4 as a network storage device. Some might recommend using LVM+xfs. Then you can slowly migrate over to Linux workstations after you become familiar with Unix permissions.  OSX has Unix permissions too, but I suppose you've never needed to learn them?  There's no such thing as Ubuntu permissions, BTW.

Have you looked at the Ubuntu software that will replace all the Apple/Adobe software already? That is where more transitions cause people to run back to Apple.

---

### Post by oldrocker99 on 2020-02-09
FWIW, I had an external hard drive to which I suddenly had no permissions. I was using it to do a radio show, and using chown fixed it right up, with no further problems.

It **was** EXT4, not HFS+.

---

### Post by itaki on 2020-02-10
Thank you @TheFU, this is all very good information. I think I'm going to back up the raid completely and move it over to Ubuntu as ZFS as you recommended. The current way of backup in this pipeline is to keep all the media on the original disks that fly in from DIT, and then backup just the project files, renders, graphics and all the other stuff. That way the project could be rebuilt if needed. For more mission critical projects like features, there's a more thorough backup system, but for spots and social engagements we rarely ever revisit old projects.

As for software, we are making a transition from an Adobe pipeline to Davinci. The Resolve pipeline with Fusion, Color, and sound all built in and GPU support 10X faster than Premiere and AE is just a no brainer. Also, for more VFX heavy projects, Nuke runs natively as well. As does Houdini. The only thing I think I'm really going to miss is C4D and possibly AE just because I'm so familiar with it. But we'll see how it goes with Fusion. Really hoping in 6 months I'm not running back to my old mac to just move some text around.

---

### Post by kevdog on 2020-02-13
I love ZFS however just a few things --- you probably need enough RAM to support it -- it's pretty RAM hungry.

---

