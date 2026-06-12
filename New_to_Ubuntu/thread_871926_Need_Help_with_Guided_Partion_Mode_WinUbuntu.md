---
title: "Need Help with Guided Partion Mode Win/Ubuntu"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by ms_meme on 2008-07-27
Hello,

Very new here. I have used the live cd and am preparing to install (weeks away). I am sure the guided mode will be the best for me. I have read a lot about it and studied the pictures so I have an idea what will be happening. 

My problem or question is how to decide how to move the slider for the first Windows partion. I have read to do a % of this or that. But I don't know what this or that is.  I will continue to use Windows so need to leave room for something.

I do not understand ram and rom and memory stuff.  

I hope someone can ask me questions so I can provide them answers that will help them advise me on what to do.
[[IMG]http://img356.imageshack.us/img356/5523/partitionmj7.th.png[/IMG]]("http://img356.imageshack.us/my.php?image=partitionmj7.png")
Here is a  picture of my partition I took in ubuntu.
Thanks in advance for very simple answers for a simple member

---

### Post by Shazaam on 2008-07-27
1. Defrag Windows in safe mode (will take a while).
2. Boot the Ubuntu or gparted livecd.
3. Move the right slider to the left (resize) to about 50-60 gig for Windows so it is first on the drive.
4. Reboot and let windows do a disk check (may happen twice).

The rest depends on your future plans. If you think you will install multiple distros make an Extended partition in the new unpartitioned space. Then you can install other linux os's as logical drives in the extended partition without worrying about the 4 primary partition limit. This is my disk layout.....
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00047d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38626   310263313+   5  Extended
/dev/sda5               1         781     6273319+  82  Linux swap / Solaris
/dev/sda6             782        3350    20635461   83  Linux (Puppy)
/dev/sda7            3351        8471    41134401   83  Linux (Mepis)
/dev/sda8            8472       18784    82839141   83  Linux (Gutsy)
/dev/sda9   *       18785       28705    79690401   83  Linux (Hardy)
/dev/sda10          28706       38289    76983448+  83  Linux (open)

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000096f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS (XP)

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc709c709

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9145    73457181   83  Linux (opensuse)

```
Most linux distros live happily on a 20 gig or less partition size.

---

### Post by ms_meme on 2008-07-27
> **Shazaam said:**
> 
1. Defrag Windows in safe mode (will take a while).
2. Boot the Ubuntu or gparted livecd.
3. Move the right slider to the left (resize) to about 50-60 gig for Windows so it is first on the drive.
4. Reboot and let windows do a disk check (may happen twice).

The rest depends on your future plans.

Thank you Shazaam.

[LIST=1]
[*]I will defrag and do other preparations.
[*]I will boot the Ubuntu cd
[*]I will move the slider over to between the 50-60 gig marker. In the picture I posted is the slider for Windows near 16 gig? And that I have about 95 gig left. And I should put it over to around 50?  Just making sure.
[/LIST]
This next step is where I am confused.  Do I reboot immediately? or do I continue through the rest of the installing?  Do I then go into Windows myself through START to start the disk check?  or will this come up automatically?

Will this guided mode give those partitions for Sharing with Windows and a Home partition?
I don't understand what I am asking.  I have just seen the picture and read that there were four partitions.   (I think)

Do pardon me for asking what may seem self-evident questions.  I know I have one chance to do this and if something goes wrong I want to be able to blame it on the machine. :)

Oh, your code looks...well your code looks.... well it looks nice. :lolflag: I hope to someday look at a code and understand it. 

As for my future plans.........I am sure I will not be adding any other Linux distros in the near future.
For the past so many hours I have just been struggling to post a post.  Every time I previewed, it told me I didn't have enough and to add one more item. :( I have typed this post umpteen times.

---

### Post by Shazaam on 2008-07-27
You can "Resize" the Windows partition during install. The picture you have on your first post doesn't show the sliders. It is showing the total size of the Win partition. You need to click on "Resize/Move" to show the sliders. A simple diagram to show which slider to move....

```
|            <-----| (move the right one to the left)
```

Ok, no added distros besides Ubuntu. Then just install Ubuntu to the unpartitioned space with the partition setup you want.
To be safe you "should" reboot after any Windows partition change so Win won't freak out. But you will be ok during the install. When you are done installing and Ubuntu reboots you will see a grub bootloader screen. Hit your "esc" key immediately and choose Windows first (up and down keyboard arrows to select) so it can do an automatic disk check. Then reboot to Ubuntu.

For a better explaination of what to do this is a good site to look at....
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

