---
title: "Xubuntu Installation Hangs"
date: 2014-06-29
forum: New to Ubuntu
---

### Post by Curtis_Bryant on 2014-06-29
While trying to install Xubuntu on my old desktop computer, the installer locked up while trying to install. It ran fine from the Live DVD, and I connected to the Internet. 

I'm installing Xubuntu hoping that it will run faster than regular Ubuntu on my old computer. Here are the computer's specs:

[LIST]
[*]Model: 2006 Dell Inspiron 530s 
[*]OS: Windows Vista Home Premium (32 bit) 
[*]Pentium Dual CPU E2200 @2.2GHz 
[*]RAM: 3GB 
[*]Display adapter: Intel G33/G31 Express Chipset Family 
[*]Hard drive: NTFS 500GB, 315GB free 
[/LIST]

Would you have any suggestions for completing the installation or a different Linux distro that might work better?

---

### Post by mörgæs on 2014-06-29
Hi, welcome to the fora.

Are you sure it's indeed locked up? For how long did you wait?

---

### Post by Curtis_Bryant on 2014-06-29
Here's some more information about the installation. I downloaded the Xubuntu 14.4 ISO from xubuntu.org, burned the ISO to a DVD, and booted the computer from the DVD. The installer started, and I got through the first three parts, which included selecting the option to install Xubuntu alongside Windows Vista and the partition sizes. I used the default suggested by the installer. That would have given Xubuntu a little more than 98GB of the hard drive's 500GB. 

During the fourth stage--the actual installation--the computer sounded like it was working hard, with the DVD spinning at high speed, but it appeared to have made no progress after several hours. After ejecting the DVD, the computer's behavior did not change. To stop it, I turned it off. When I turned it on again, Windows Vista started normally.

---

### Post by Curtis_Bryant on 2014-06-29
I waited several hours, and it didn't seem to make any progress. That's why I think it hung.

---

### Post by kansasnoob on 2014-06-29
It could be due to this very, very old bug (notice that there are several duplicates):

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/89357](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/89357)

So I usually prepare my partitions using Gparted before installing but we need to take a deep breath and consider a far worse bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Scary, huh :(

So lets take time to see what's going on. Since you can boot the Xubuntu 14.04 live DVD to a live desktop lets first check the disc for defects:

[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

I don't recall if Xubuntu hides the initial boot options or not but those screenshots should give you an idea what I'm talking about. Just select Check disc for defects and wait several minutes for it to complete.

If it shows no defects found just boot back to the live desktop, open the terminal, and post the output of this command:

```
sudo parted -l
```

It would also be nice to include a screenshot of Gparted. Then we can see where the process froze and decide what to do next ;)

---

### Post by JeQhdMD on 2014-06-30
Besides downloading and creating the iso install dvd, did you do anything to prep your hard drive?   Such as defragging vista (twice), then shrinking the ntfs partition, then creating a new partition and lastly - formatting it to either ext3 or ext4 via a live CD like "Parted Magic" . . . ?   Then, when installing a dual-boot, I've never (ever) had any luck with the "install alongside . . " option.   It's usually suggested to use the "do something else" (or similar wording - can't remember it exactly.

The installer hung (I believe) based on not having a viable "empty or Linux" formatted partition ahead of time.

If you've done or tried the above, and it's still hanging, then we have to try something else.

---

### Post by Curtis_Bryant on 2014-06-30
Thank you very much for this information! No errors were found on the installation disc. 

Below you can see screenshots of the command ```
sudo parted -l
``` and a screenshot of Gparted.

[ATTACH=CONFIG]254354[/ATTACH][ATTACH=CONFIG]254355[/ATTACH]

---

### Post by yancek on 2014-06-30
The images you posted show three windows partitions on the first drive (sda) taking up the whole drive and you only have 1MB of unallocated space.  You can't install Xubuntu on 1MB.  If you want Xubuntu on that drive, you will need to first defrag the vista then resize (shrink) it to create room for Xubuntu.

If you want to install it on the external/second drive sdb, you need to select the 'Something Else' or 'Manual' option. From there, you should be able to create and format a partition on which to install Xubuntu.  This entire drive seems to be one FAT32 partition.  You need to shrink it and create another partition with a Linux format, ext4 would be default.

---

### Post by Curtis_Bryant on 2014-06-30
Thank you for the suggestions! I will defrag Vista and use another installation option to create a partition for Linux and let you all know how it goes.

---

### Post by kansasnoob on 2014-06-30
> **Curtis_Bryant said:**
> Thank you very much for this information! No errors were found on the installation disc. 

Below you can see screenshots of the command ```
sudo parted -l
``` and a screenshot of Gparted.

[ATTACH=CONFIG]254354[/ATTACH][ATTACH=CONFIG]254355[/ATTACH]

Sorry for the long delay but I wanted to grab some up-to-date screenshots. You'll see why later.

OK, first things first ;)

Is there a reason for having the 500GB USB drive connected? That could cause problems during the Xubuntu installation so the first thing I'd do is boot into Win Vista and safely shut down and remove the external drive! If there's a reason for not doing so let us know why before proceeding!

Once you're sure the external drive and its data are OK, and it's disconnected, reboot Vista one more time and then use Vista's own partitioner to create the free space for Xubuntu as shown here (don't create any new partitions, we'll use the Ubuntu installer to do that) :

[http://www.techrepublic.com/blog/windows-and-office/how-do-i-resize-a-vista-partition-without-damaging-data/](http://www.techrepublic.com/blog/windows-and-office/how-do-i-resize-a-vista-partition-without-damaging-data/)

I think that's pretty straight forward but if you have any questions ask them before proceeding. Oh, as previously mentioned, it may be wise to defrag Windows before performing the resize.

Regardless, when the resize is completed, once again reboot Vista to be sure that it still boots normally, if not that's a Windows problem that you'll need to fix before performing the Xubuntu installation.

So once you have the external drive disconnected, created adequate free space for Xubuntu, and made sure Vista still boots OK its time to begin the Xubuntu installation. 

Note: The attached screenshots were taken using Ubuntu GNOME Trusty, and I created some mock-up partitions on a spare 80GB drive, so they're only representative of what you'll see. The actual partition sizes (other than SWAP) are obviously smaller than what you'll actually see since I used a much smaller drive!

When you get to the Installation type screen (third screen unless you have to setup wireless) select Something else and click on Continue, then you'll see something similar to this:

[ATTACH=CONFIG]254357[/ATTACH]

So highlight "free space" and click on the + which will allow you to create the new SWAP partition:

[ATTACH=CONFIG]254358[/ATTACH]

Notice that I selected "size = 3200" which is appropriate for 3GB of RAM, "Type = Logical" because you already have 3 primary partitions, "Location = End of space", and "Use as = swap area". Once that's done click on OK and you'll see the newly created swap: 

[ATTACH=CONFIG]254359[/ATTACH]

So once again highlight the "free space", and click on + again to create the root "/" partition:

[ATTACH=CONFIG]254360[/ATTACH]

Notice there that I used the entire free space still available after creating SWAP (because I'm too lazy to do math), "Type = Logical", Location = Beginning of space", "Use as = Ext4", and "Mount point = /". The / means root. Once you've completed those choices click on OK again:

[ATTACH=CONFIG]254361[/ATTACH]

There you can see that we've now created both the / and swap partitions so if you've done everything right it's time to click on Install now.

I hope I didn't make your brain explode.

---

### Post by Curtis_Bryant on 2014-07-01
Thanks for the detailed instructions, kansasnoob! So far, I've gotten as far as the defrag. It tooks hours and seems to have sped up Vista a lot. I'd run Defrag many times, but maybe it had been interrupted. I made sure to turn off anything that might interrupt it such as the Internet connection, antivirus, and several other things.  I'll continue the Xubuntu installation as soon as I can.

---

### Post by Curtis_Bryant on 2014-07-02
After defragmenting the Vista machine, I tried to shrink the C drive according to the instructions in the TechRepublic article but was told there's no shrink space available:

[ATTACH=CONFIG]254387[/ATTACH]

I've heard of snapshots, but what are pagefiles? Might that be preventing the shrinking?

---

### Post by kansasnoob on 2014-07-02
Yikes!!!!

OK, that's not altogether uncommon, but prior to posting the link I want to stress what it says there:

> **Be careful when following these steps, because they could leave your system unable to boot… [COLOR="#FF0000"]advanced geek level required[/COLOR].**

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Good luck :)

---

### Post by Curtis_Bryant on 2014-07-03
I ran defrag a few more times, and it did free up 20MB of shrinkable space, but that's still not enough. Thank you very much for the HowtoGeek article. I think I'll leave Vista alone and look at using the live disk and maybe installing Xubuntu on my laptop, which has more than 200GB of shrinkable space.

Thanks a lot, everybody!

---

