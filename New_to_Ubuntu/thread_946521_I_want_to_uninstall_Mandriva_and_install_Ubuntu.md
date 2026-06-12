---
title: "I want to uninstall Mandriva and install Ubuntu"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by hapkidoman on 2008-10-13
I am brand new to linux after always using windows and am trying out different distros.  I've just installed mandriva, but do not like it and I really want to install Ubuntu (after hearing discussions about it).  How do I go about doing that?  I have Mandriva partitioned on my hard drive along side Windows Vista.  I still want to keep Vista without damaging it.  

Can I just install Ubuntu over mandriva?  What's the best way to do this without screwing up Vista?

Thanks so much in advance.

---

### Post by Idefix82 on 2008-10-13
Yes, you can just delete the partitions that Mandriva is occupying during the installation procedure (choose manual installation) and repartition the space for Ubuntu. This procedure shouldn't interfere with your Windows installation at all.

---

### Post by Elfy on 2008-10-13
I guess it made a / drive and a swap one- can't remeber of the top of my head.

When you get to the partition part of the install - pick manual. You don't need to delete anything, choose the partitionon which mandriva is installed - Edit partition - you get a new window.

In the Use As box - pick ext3, althought it might be ext2 journalled - format
In the Mountpoint box - pick /
exit that window - the partition should now be amrked for formatting and with / as mountpoint

Move on to next part of the installation and continue

---

### Post by hapkidoman on 2008-10-13
So, I just install Ubuntu and during the installation process put ubuntu over the mandriva partitions?  Will this erase everything of mandriva?

---

### Post by Elfy on 2008-10-13
As long as you point it at the correct partition yes it will reformat and then install in the partition.

---

### Post by bodhi.zazen on 2008-10-13
> **hapkidoman said:**
> So, I just install Ubuntu and during the installation process put ubuntu over the mandriva partitions?  Will this erase everything of mandriva?

yes, exactly ...

You can keep the swap partition if you like, or reformat it ... does not matter.

---

### Post by hapkidoman on 2008-10-13
Well, I'm in the process of installing Ubuntu, but have run into a problem.

During the partitioning section of the installation, I've selected manual.

I'm suppose to select the partition which mandriva is on; however I don't know which one it is.  Here are my options:

/dev/sda

  /dev/sda1  ntfs
  /dev/sda2  ntfs
  /dev/sda5  ext 3
  /dev/sda6  swap
  /dev/sda7  ext 3

I don't know which ones to select in order to mess with the "use as box" and the mountpoint

---

### Post by hapkidoman on 2008-10-13
How can I figure out which partition mandriva is on so I don't accidentally select Windows Vista?

---

### Post by hapkidoman on 2008-10-13
Thanks for everyone who has helped me so far.  I've figured out that the ntfs is for Windows Vista and that the ext 3 partitions are for the mandriva.  However, do I choose both ext 3's and edit them as forestpixie suggested?  Do I do that with the swap partition too?

Any advice would be greatly appreciated.

---

### Post by hapkidoman on 2008-10-13
Hi everyone,

I'm in the process of installing ubuntu over mandriva.  I also have windows vista and would like to keep it on my computer.  During the installation process of ubuntu, I select manual (when asked to partition).  I deleted the following:

/dev/sda5 ext 3
/dev/sda6 swap
/dev/sda7 ext 3

I kept the following:  /dev/sda1 ntfs and /dev/sda2 ntfs  because they are for windows vista.

Now, I have a lot of free space and don't know what to do with it.  When I edit the free space do I select ext 3 or what?  Do I select -/ for the mountpoint option or /home, /boot, or any of the other options?  I need some space for a swap partition, but I'm not quite sure what I'm doing.

Any help would be great.

Thanks in advance.

---

### Post by Elfy on 2008-10-13
When you installed mandriva did you set it up with a seperate home partition - anyway from the livecd opena terminal from accessories and run ```
sudo fdisk -l
```

It would appear that is the case, butanyway you could do the same with ubuntu. Post the output of that command and we can go from there.

Swap will be recognised and dealt with wiothout your input.

---

### Post by overdrank on 2008-10-13
> **hapkidoman said:**
> Hi everyone,

I'm in the process of installing ubuntu over mandriva.  I also have windows vista and would like to keep it on my computer.  During the installation process of ubuntu, I select manual (when asked to partition).  I deleted the following:

/dev/sda5 ext 3
/dev/sda6 swap
/dev/sda7 ext 3

I kept the following:  /dev/sda1 ntfs and /dev/sda2 ntfs  because they are for windows vista.

Now, I have a lot of free space and don't know what to do with it.  When I edit the free space do I select ext 3 or what?  Do I select -/ for the mountpoint option or /home, /boot, or any of the other options?  I need some space for a swap partition, but I'm not quite sure what I'm doing.

Any help would be great.

Thanks in advance.

Please do not create multiple threads on the same issue. Threads merged :)

---

### Post by hapkidoman on 2008-10-13
> **forestpixie said:**
> When you installed mandriva did you set it up with a seperate home partition - anyway from the livecd opena terminal from accessories and run ```
sudo fdisk -l
```

It would appear that is the case, butanyway you could do the same with ubuntu. Post the output of that command and we can go from there.

Swap will be recognised and dealt with wiothout your input.

Here are the results of doing that.....

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2527a2c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1411    11333826    7  HPFS/NTFS
/dev/sda2   *        1412       24592   186201382+   7  HPFS/NTFS
/dev/sda3           24593       38404   110944890   83  Linux
/dev/sda4           38405       38913     4088542+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

notice that I did end up putting a swap partition up.  When I go into /dev/sda3 in order to edit it, I select ext 3 and put / as my mountpoint.  However, whenever I continue the process it says that sda3 failed.  I'm worried now....

---

### Post by hapkidoman on 2008-10-13
> **overdrank said:**
> Please do not create multiple threads on the same issue. Threads merged :)

Sorry, no one had replied in a while and I was starting to get worried that I wouldn't get my problem resolved.

---

### Post by Elfy on 2008-10-13
> **hapkidoman said:**
> Sorry, no one had replied in a while and I was starting to get worried that I wouldn't get my problem resolved.

People reply eventually when they have time ;)

sda3 failed to do what - exact message please.

How did you create the partitions? With the partitioner during the install or the partition editor in the sys >admin menu?

---

### Post by bodhi.zazen on 2008-10-13
See this thread :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

If you are not sure what is where you will need to mount the partition and review the contents.

---

### Post by hapkidoman on 2008-10-13
Well, initially, I made the partitions while installing Mandriva.  Before that I had only Vista on my computer (my computer is 3 days old).  So, I had the partition that the install process in Mandriva set up.  I deleted:

/dev/sda5 et 3
/dev/sda6 swap
/dev/sda7 ext 3

Okay........now I just did the same thing as before.  I went into /dev/sda3 and selected  ext journaling file system and selected / as the mount point in order to see the same error message so that you would no what it said and it is in the process of installing the OS.  Currently it is at 50% completion and is copying files.  It did not do this last time, so I do not know what the difference is...

Is what I did correct?

---

### Post by Elfy on 2008-10-13
If it's installing I would say so :)

Next time try to be a little less impatient - although a lesson in partitioning was probably worth it.

---

### Post by hapkidoman on 2008-10-13
Now I have a new error that starts when it is 54% of the way to completion:

The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

I checked the cd and ubuntu said that there was 1 faulty file......

---

### Post by hapkidoman on 2008-10-13
Also, I tried to get back into vista.  So, I shut down the computer and turned it back on (there was no cd in the drive) the boot screen said:

grub loading please wait....
Error 22

now, I can't get back into windows vista and am definitely starting to become worried.

---

### Post by Elfy on 2008-10-13
There is a cd [integrity]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck") check on the livecd boot menu - did you do it?

Check the md5sum of the download - [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Did you burn the cd at a slow speed, I have also had problems using cdrw rather than cdr's

---

### Post by bodhi.zazen on 2008-10-13
You will need to either install some version of Linux or restore your windows MBR to boot windows (or use a boot disk or boot CD). You can do it manually from grub (if you know the lingo).

You may need to either burn a new copy of Ubuntu or try the alternate installer.

---

### Post by Elfy on 2008-10-13
> grub loading please wait....
Error 22can't remember if mandriva uses grub - if that is the case then it is trying to boot mandriva - but the partition no longer exists.

Check the cd and go from there - if it is no good you're going to have to reburn it and if it's the md5sum it will need to be downloaded again - if though you used the torrent to download it then the file should be ok.

---

### Post by hapkidoman on 2008-10-13
> **forestpixie said:**
> There is a cd [integrity]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck") check on the livecd boot menu - did you do it?

Check the md5sum of the download - [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Did you burn the cd at a slow speed, I have also had problems using cdrw rather than cdr's

Yes, I used the integrity check on the livecd.  It said that I had one file that was bad.

---

### Post by hapkidoman on 2008-10-13
> **bodhi.zazen said:**
> You will need to either install some version of Linux or restore your windows MBR to boot windows (or use a boot disk or boot CD). You can do it manually from grub (if you know the lingo).

You may need to either burn a new copy of Ubuntu or try the alternate installer.

How do I restore my windows MBR to boot windows?  I know nothing about grub.

---

### Post by bodhi.zazen on 2008-10-13
You do it from your Vista Recovery CD or partition:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If you do not have one, just re-install Mandriva for the moment.

---

### Post by hapkidoman on 2008-10-13
> **bodhi.zazen said:**
> You do it from your Vista Recovery CD or partition:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If you do not have one, just re-install Mandriva for the moment.

I've re-installed Mandriva successfully and can now get into windows vista.  Also, I am no longer having a complete heart attack.  Which is good.  However, once I burn a new Ubuntu livecd and make sure that the integrity is good.....how do I go about replacing mandriva with ubuntu.  I'm still confused as to what to do once I get to the partition section of the install.

---

### Post by Davsdu on 2008-10-13
double post

---

### Post by gandaran on 2008-10-13
> **hapkidoman said:**
> I've re-installed Mandriva successfully and can now get into windows vista.  Also, I am no longer having a complete heart attack.  Which is good.  However, once I burn a new Ubuntu livecd and make sure that the integrity is good.....how do I go about replacing mandriva with ubuntu.  I'm still confused as to what to do once I get to the partition section of the install.

you either use the existing mandriva ext3 partitions, just select and tick them for formatting or delete them and make your own ext3 partitions
one ext3 (for) / (root) (5 GB  should be enough)
one swap  (maybe 1GB)
one ext3 (for) home (whatever is left of disk space)

---

### Post by Davsdu on 2008-10-13
First off, make a backup of whatever documents/files you might already have on your Vista partition that you want to keep (just in case). Next, when installing Ubuntu, delete every partition that is not occupied by Vista when you´re asked about partitioning. After that, Ubuntu will automatically detect the empty space and suggest a working partition set-up for you. It should be fairly straight forward after that. :)

Also, be sure to install Ubuntu 8.4 and not 8.10 which is still in beta. Otherwise, it MIGHT give you a few problems during installation or later. Lastly, no need for any heart attack, take a cup of coffee, take a deep breath, relax, and enjoy life. :D

---

### Post by Keen101 on 2008-10-13
> **hapkidoman said:**
> Hi everyone,

I'm in the process of installing ubuntu over mandriva.  I also have windows vista and would like to keep it on my computer.  During the installation process of ubuntu, I select manual (when asked to partition).  I deleted the following:

/dev/sda5 ext 3
/dev/sda6 swap
/dev/sda7 ext 3

I kept the following:  /dev/sda1 ntfs and /dev/sda2 ntfs  because they are for windows vista.

Now, I have a lot of free space and don't know what to do with it.  When I edit the free space do I select ext 3 or what?  Do I select -/ for the mountpoint option or /home, /boot, or any of the other options?  I need some space for a swap partition, but I'm not quite sure what I'm doing.

Any help would be great.

Thanks in advance.


Ok, I see that you have re-installed mandriva. That's ok.
I have quoted you. once you have the new cd [B]You should do the same thing. remove the

 /dev/sda5 ext 3
/dev/sda6 swap
/dev/sda7 ext 3[/B]

then go back to ubuntu's "**Guided partitioning**" option, and select "**use largest continuous free space**"

Ubuntu shoud do the rest. Oh, and don't panic. We are here to help. Someone mentioned having a separate /home partition, but that is mostly for more advanced users. Since this is your first install of ubuntu don't worry about it.

---

### Post by hapkidoman on 2008-10-13
I just wanted to say thank you to everyone who replied and helped me along the way.  I am currently in the process of burning my new ubuntu livecd at a lower speed.  I will attempt to install it one more time.  

If I choose to use the mandriva partitions, and I select them for formatting is the only thing that I do is check the box that says formatting?

---

### Post by Davsdu on 2008-10-13
Your last post is a little vague, to me at least, I´m afraid. Do you mean, you´ll like to overwrite your Mandriva installation or do you want to install Ubuntu next to Vista **and Mandriva**? If it´s the latter then Ubuntu will ask you whether you´d like to reduce either the Vista or Mandriva partition while installing. If you simply want to get rid off Mandriva, then just follow the steps provided by Keen101. That should do the trick. ;)

---

### Post by Elfy on 2008-10-13
No you need to give them mountpoints as I said earlier. It would be useful now to know the result of ```
sudo fdisk -l
```

Given that information we could possibly get you through the install with both a root and home partition.

Certainly I think it would be worth it for you - you do, it appears like to get your hands dirty with the system - quick way to learn :D

If you have a seperate home then any configs you have for e-mails etc will be transferrable to reinstalled system files.

At the end the decision is yours to make.

Finally did you check the md5sum for the file before you burnt it to make sure that the download was good?

---

### Post by gandaran on 2008-10-13
> If I choose to use the mandriva partitions, and I select them for formatting is the only thing that I do is check the box that says formatting?
select the manual installation process first
then you have to select the mount point, one ext3 for / (root) another ext3 for home, leave the swap just as it is, then tick the / and home for formating and just click next, its easy!

---

### Post by hapkidoman on 2008-10-13
I just wanted to say that thanks to everyone's help I am now the proud user of ubuntu and visa.  However, when I did then installation I only did a / (root) partition, I did not do a /home partition.  Is this okay?  Will I be able to change that later, once I become a more experienced user?

---

### Post by Elfy on 2008-10-13
Yes you can if you so wish, I don't bother myself and keep all my data on seperate drives and partitions - all I have of any consequence in /home are configs for my apps - when I reinstall I backup the ones I wish to keep and put them back.

I found it useful when I started last year, but fairly quickly changed - following a reinstall in which I overwrote it all ;)

Good luck and glad you have finally got there.

---

### Post by Idefix82 on 2008-10-14
Congratulations on installing Ubuntu!
Don't worry about the partitions now. In a couple of weeks' time you will notice that you are hardly ever booting into Vista anyway and it is just eating up space :) We have all been there before. Then you will probably want to do another clean install of Ubuntu and give it a lot of space so that will be your chance to set up all the partitions you want. By that time you will also have heard of other possible partitions like /boot, /var, /usr and so on. But as I said, don't worry about it for now.

---

