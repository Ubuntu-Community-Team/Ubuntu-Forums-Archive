---
title: "Can't upgrade u10.04 even with free space 21GB"
date: 2014-09-21
forum: New to Ubuntu
---

### Post by nu2u904 on 2014-09-21
History on this Compaq running win xp initially shrank xp by 8GB successfully installed u8.04; successfully upgraded to u10.04.Now have less 0.3GB available. attempted to upgrade to u12.04, downloaded some packages then quit no room on root /. I then shrank xp by 21GB and assigned ext3 file system. Tried again to upgrade same problem.

How can I get the installer to skip u10.04 and make use of the 21GB free space? If I can resolve this I could as easily install u14.04 my ultimate target. 
alternatively how can I expand root / to occupy the free space and subsequently replace 10.04?
l

---

### Post by Bashing-om on 2014-09-21
nu2u904; Hi !

As a suggestion take a look at /boot. That is generally the 'device' that gets filled up over time with old kernels;
```

df -h
df -i
cd /
sudo du -sx * | sort -n
cd

```
If that is the case one can remove the old kernels with the package management's tools to regain the space.

Be advised there is the probability of release upgrade failure to 12.04 as the system has undergone some huge changes since 10.04. Won't hurt to try.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Michael_McKenney on 2014-09-21
I have that problem with /boot filling up. I used Synaptic to clear out the old Linux-images.

---

### Post by yancek on 2014-09-21
> I then shrank xp by 21GB and assigned ext3 file system.

Assigned ext3 filesystem to what?  I would think you would need to resize the Ubuntu partition to include the free space on the same partition on which you currently have the system.  Did you do that?

> How can I get the installer to skip u10.04 and make use of the 21GB free space?

You can download the iso file of Ubuntu and burn it as an image to a DVD or put it on a flash drive with the appropriate software (unetbootin, pendrivelinux, etc.) and then boot from it and do a new install.

>  how can I expand root / to occupy the free space and subsequently replace 10.04?

The simplest method.  Obviously, if you have any personal data on the partition, you would need to move it elsewhere, another drive preferably.  You can resize the partition from GParted which is on the Ubuntu installation medium or you can use it from a bootable CD you create.  It won't work run from the partition on which it installed for your purposes.

---

### Post by nu2u904 on 2014-09-22
Thank you. With Synaptic open what is the step by step procedure to remove old kernals and linux images?

---

### Post by slickymaster on 2014-09-22
> **nu2u904 said:**
> Thank you. With Synaptic open what is the step by step procedure to remove old kernals and linux images?

Here's the answer: [How do I remove or hide old kernel versions to clean up the boot menu]("http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu")

---

### Post by nu2u904 on 2014-09-22
Thank you yaneck.  How do I resize my root partition to include the 21GB of free space? Do I need to remove the .ext3 file system? I see that resizing the partition would in effect destroy u10.04.

I have a u12.04 live cd which won't boot. I also have a u13.10 live cd which once booted after long delays; now boots only as far a pale green screen with live mouse pointer but won't respond. With only 0.3GB disk space in root / I can't  download the iso cd. I have a mounted external drive. How can I tell Brazero to change the download location to this drive?

---

### Post by Michael_McKenney on 2014-09-22
I hit the search button and put in Linux-images and did a search for the oldest ones.  I deleted every Linux-image up to the current ones.  It was simple.  check the box right click and choose remove.  It did an awesome job cleaning up my box.  Use uname-a from terminal to determine your version.  Keep at least 2 backup.  I kept all from the latest version for now.

---

### Post by yancek on 2014-09-22
>   How do I resize my root partition to include the 21GB of free space?

You haven't posted enough information to tell.  First, do you now have Ubuntu 10.04 installed?  Are you able to boot it?  If not, do you have anthing else (Linux) which you can boot?  If you can boot any Linux, open a terminal and run this command to get drive/partition info:  sudo fdisk -l(Lower Case Letter L in the command) and post it here.

 > Do I need to remove the .ext3 file system?    

Not necessarily, that's one of the reasons we need the above info.

> I see that resizing the partition would in effect destroy u10.04.


No, not necessarily but again not enough info.
If you can boot the installed Ubuntu run this command:  df -h
Also, while in the terminal type:  parted  You will get some output and it will show (parted) in parenthesis, just type:  print free
That should be enough info to get you started.

---

### Post by grahammechanical on 2014-09-22
Please may I ask you to clarify a couple of things?

You have Ubuntu 10.04 on a partition that is too small to allow an upgrade to Ubuntu 12.04. You are unable to download and burn a Ubuntu ISO image because the 10.04 partition is too small. You have a have a Ubuntu 12.04 live CD but it will not boot. Is this correct?

Then you are in an impossible situation. These are two choices are far as I can see.

1) get that 12.04 CD loading, then 

a) at the live desktop use Gparted to delete that Ext3 partition that you created. The one that is 21GB in size and then expand the 10.04 partition to take up the unallocated space that we get when we delete a partition.

b) use the Something Else option to install 12.04 into that 21 GB partition.

2) As well as removing old kernels start deleting/removing applications in Ubuntu 10.04. If you have applications that are not part of a Ubuntu default install remove them. Ubuntu 12.04 and 14.04 need between 5 - 6 GB of partition space. Start moving data off of that 10.04 partition. There is more than one way to create space in a partition, than removing kernels.

As for getting the 12.04 live CD working have a look at this wiki page. Look at section 6 - F6 options.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

---

### Post by nu2u904 on 2014-09-22
Thank you yancek. On a parallel thread I wrote: Shrank xp by 8GB' installed u8.08; upraded to  u10.04; runs ok. How do print code data for forum?

---

### Post by nu2u904 on 2014-09-22
Thank you slickymaster for that link. It has given me many options to choose from.

---

### Post by nu2u904 on 2014-09-22
Thank you Michael. For starters on my 'Synaptic Package Manager' there is no 'Search' button. I did a quick search no results. I clicked on Edit then Search and entered 'Linux-images' no response, ecept statement no package is selected. What am I missing?

---

### Post by JKyleOKC on 2014-09-23
Try entering "linux-image" rather than "Linux-images" and you should get some results. The search is case-sensitive and quite literal. Also, if you select "Status" from the buttons in the lower left corner of the screen, and "Installed" from the list of choices above that, you'll get a far less crowded display. Finally, you don't need to use the Search button; the search starts automatically when you begin typing into the "Quick filter" text box.

---

