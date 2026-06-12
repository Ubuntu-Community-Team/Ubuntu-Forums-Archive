---
title: "Windows 7 dual boot / remove partition"
date: 2013-06-18
forum: New to Ubuntu
---

### Post by AdamDynamic on 2013-06-18
Hey,

I've spent the evening trying to fix this and got nowhere with it, I'm hoping someone here can help me?

I tried to install Ubuntu 13.10 as a dual boot on my Lenovo Thinkpad with Windows 7 64 bit installed. The installation didn't work (the machine booted to Windows automatically with no boot menu) so I tried to remove the partition that the Ubuntu install had created so that I could start again.

I've managed to remove the drive so that I now have a 340Gb 'unallocated' space on my harddrive, all I want to do is extend my Windows partition into this space but nothing I try seems to allow me to do it. I've tried the Windows Disk Manager, I also tried making a live CD with GParted installed, the result is the same with both: I can shrink the Windows partition but I can't extend it into the unallocated space, nor can I shrink the unallocated space.

Can anyone point me in the right direction on how I can fix this? I'm starting to become concerned that I've lost 340Gb of my harddrive? Any help would be appreciated, if more information would be helpful, please ask - I've included a screenshot of my GParted attempt here: [http://www.flickr.com/photos/adamdynamic/9078261413/](http://www.flickr.com/photos/adamdynamic/9078261413/)


Thanks,

Adam

---

### Post by Frogs Hair on 2013-06-18
I have used a similar tutorial to the one at the link in the past on the Win 7 side of the hard-drive .    [http://www.bleepingcomputer.com/tutorials/shrink-and-extend-ntfs-volumes-in-windows/#extend](http://www.bleepingcomputer.com/tutorials/shrink-and-extend-ntfs-volumes-in-windows/#extend)

---

### Post by ahallubuntu on 2013-06-18
~

---

### Post by MidnightGrey on 2013-06-19
To add to ahallubuntu's post:

if you wish to reinstall ubuntu, I would recommend extending the windows partition first (leaving 40-20 Gb unallocated for linux). While you can install linux first and then extend Windows, if you do not install linux in exactly the right conditions this could make extending windows problematic later (if you dont put linux on the tail-end of your unallocated block for example).

As ahallubuntu said: you dont really need 340Gb for Ubuntu, keep in mind;
Ubuntu can access and use the Windows partition for storage.
Windows cannot see or access the Ubuntu partition at all.

Additionally: Swap-partitions are no longer required at all, especially in newer computers with high RAM capacity, check out this [handy page for more information on Swap](https://help.ubuntu.com/community/SwapFaq).
A swap-file can be created after installation which will serve and has the benefit of being more flexible than swap-partitions (easier to resize).

---

### Post by AdamDynamic on 2013-06-19
> **Frogs Hair said:**
> I have used a similar tutorial to the one at the link in the past on the Win 7 side of the hard-drive .    [http://www.bleepingcomputer.com/tutorials/shrink-and-extend-ntfs-volumes-in-windows/#extend](http://www.bleepingcomputer.com/tutorials/shrink-and-extend-ntfs-volumes-in-windows/#extend)

Hi,

Thanks for all of the responses. I tried the tutorial above, when I open my Windows Disk Manager the partition appears in my 'Disk 0' as 'Free Space' (bright green header, dark green border) and right-clicking on the Windows partition doesn't allow me to extend the volume, only shrink it. I've seen (and tried) other similar tutorials on the web that say to right-click on the green partition and 'delete partition' I get the error message  'There is not enough space available on the disk(s) to complete this operation'.

(I've uploaded a photo of what I mean here: [http://www.flickr.com/photos/adamdynamic/9081239133/](http://www.flickr.com/photos/adamdynamic/9081239133/))

In terms of the 'end goal' at this point, I was going to install Ubuntu via Wubi as the partition approach is already proving to be much more work than I thought it would be.

> [COLOR=#000000]Ubuntu also created one logical partition inside the extended - a swap partition (/dev/sda5). To get the free space back, you need to: 1. Delete /dev/sda5. 2. Delete /dev/sda3.[/COLOR]

What's the best way to do this? I have a bootable pendrive with Ubuntu on it (that I used for the original install), can I acheive this through that?

Thanks again for the help!

Adam

---

### Post by MidnightGrey on 2013-06-19
> **AdamDynamic said:**
> What's the best way to do this? I have a bootable pendrive with Ubuntu  on it (that I used for the original install), can I acheive this through  that?
Do it from GParted, right click on sda5 > DELETE. then right click on sda3 > DELETE.

You cannot extend your Windows 7 partition until you've deleted the extended partition (sda3)

---

### Post by Impavidus on 2013-06-19
That 3.89GB healthy primary partition that the windows partition editor mentions isn't primary but logical and windows has no idea whether it's healthy or not because it doesn't know about swap partitions. Furthermore, windows doesn't mention the extended partition that contains it, making everything very confusing. Therefore using gparted from a live disk is easier.

Before you can delete your /dev/sda5 you may have to right-click on it and select swap off.

You may not really need a swap partition if you have plenty of ram, but if you have plenty of disk space it doesn't hurt either. We're talking about less than 1% of your disk space.

Wubi is being phased out, as it doesn't work very well on new win8 systems. It was designed to allow people who want to test Ubuntu to easely uninstall it using a windows uninstaller and to prevent them from having to modify partitions. As you are modifying partitions now anyway...

*If* you decide you want to run Ubuntu from a separate partition, I'd say, make your windows partition (/dev/sda2) a bit larger than it's now, leave your extended partition (/dev/sda3) where it is but shrink it a bit, leave your swap partition (/dev/sda5) and add a linux partition (ext4, about 25-60GB including /home) and a shared data partition (formatted ntfs, so both windows and linux can read it). I never tried it, but people have reported boot problems when Ubuntu writes to the partition from where windows vista or 7 boots. You can do it in ten minutes. As you're not shrinking or moving any partitions containing data the risk is minimal, but it's best to have backups anyway. Use windows tools for modifying any existing windows partitions.

---

