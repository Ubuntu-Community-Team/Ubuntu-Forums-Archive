---
title: "Ubuntu unusable due to too small a partition"
date: 2021-01-11
forum: New to Ubuntu
---

### Post by arthurconmy on 2021-01-11
Hello all,

I am new to ubuntu and recently set up ubuntu from a USB stick to dual boot from my windows 10 laptop. However, I think I chose too small a partition size for ubuntu, since I could only install a text editor and chrome before getting 'free more space from filesystem root' and having lots of problems here.

I have tried to extend the partition by using GParted but I was not successful since sda5 was mounted (and I think it is not possible to extend a partition why using that system?). Here's what I can see on GParted:

[https://cdn.discordapp.com/attachments/505450335272304642/797976396562694195/unknown.png](https://cdn.discordapp.com/attachments/505450335272304642/797976396562694195/unknown.png)

Can I extend the partition from windows? Here's what I see from the windows disk manager:

[https://i.gyazo.com/1cdf973ed6911921aec072260b2560a7.png](https://i.gyazo.com/1cdf973ed6911921aec072260b2560a7.png)
I would like to continue using ubuntu, but currently this setup is painful to use. If extending the partition isn't the best solution, any other solutions would really be appreciated.

---

### Post by Impavidus on 2021-01-11
You cannot change a partition when it's mounted and you cannot unmount a partition when you run the system installed on it. So the procedure is to boot Windows and use that to shrink the Windows partition, then boot an Ubuntu live disk and use that to expand the Ubuntu partition. However, your Windows partition is quite full already, so this may be a problem.

BTW, that brownish wallpaper on the background looks like the default wallpaper of a very old Ubuntu release. May I ask which version of Ubuntu you installed? I hope you just installed that old wallpaper because you liked it.

---

### Post by grahammechanical on 2021-01-11
There are a few important things to remember when resizing; creating and deleting partitions.

1) Use Windows tools to resize Windows partitions. And you will need to resize the Windows partition sda2 to create unallocated space to expand the  Linux/Ubuntu partitions.
2) Use Linux tools to resize; create and delete Linux partitions.
3) Run GParted from a Live Session and not from an installed Ubuntu.

The steps to take are these

a) Shrink sda2
b) Move sda3 across the unallocated space
c) Expand sda4 into the unallocated space
d) Expand sda5 into the unallocated space within sda4.

GParted will let us queue up actions but I like to set up an action and then apply it one at a time. I feel better when I do that. I know that things are working well. But that is just me. 11GB is indeed too small for Ubuntu. Even 15GB will be tight. Usable but tight. I think between 20 - 25GB.

Regards

P.S. Regarding the wallpaper it is indeed a background from a much earlier release of Ubuntu but it is part of the wallpaper set of Ubuntu 20.10.  The default wallpaper from Hardy Heron (08.04) given a new lease of life in Groovy Gorilla (20.10)

---

### Post by oldfred on 2021-01-11
You cannot change mounted partitions.
So you have to use live installer and its gparted or download & create gparted live flash drive. (I like to be able to boot both.)

But you have another issue.
You show an extended partition which means you have the now 40 year old MBR (msdos) partitioning. 
Windows only boots in BIOS mode from MBR.
But you show an ESP which is used for UEFI booting and UEFI wants gpt. Ubuntu lets you install in UEFI mode to MBR drives, but really should not.
Windows has to have boot flag on its boot partition, probably your sda1, but UEFI wants boot flag on ESP. Only one boot flag per drive. Or a conflict.
You can move boot flag back to sda1 and reinstall grub, installing the BIOS boot version of grub to convert install to BIOS/MBR.

Since system is UEFI, much better to have Windows in UEFI boot mode. Microsoft has required vendors to install in UEFI/gpt mode since 2012, but user could install in BIOS/MBR.
With BIOS, you will always need Windows repair/recovery flash drive as well as Ubuntu live installer.
While grub will boot Windows is in same boot mode, both BIOS or both UEFI, it cannot boot Windows is different boot mode.
And grub only boots working Windows, or Windows that is not hibernated. Fast start up in Windows turns on hibernation flag, so then grub cannot boot it.
And then you have to use your Windows repair disk to put a Windows boot loader into MBR to boot Windows (or maybe Boot-Repair, if it can see the hibernated install). 
After fixing Windows you can then restore grub using Ubuntu live installer.

With UEFI, you just need to select Windows in UEFI boot mode as both Windows & Ubuntu should be directly bootable from UEFI. Or no hassle with boot loaders.

---

### Post by arthurconmy on 2021-01-11
Hello, I am on the way through going through the steps to the post above, clearing as much of the 99GB that I've used on the windows machine as possible.

However, I do not understand almost any of this post. What consequences does this have? While the experience hasn't been pleasant, I have managed to load into ubuntu and windows from start menu for the past month.

---

### Post by oldfred on 2021-01-11
It looks like boot flag is on sda1, but ESP is still working for UEFI boot.
So from UEFI you are booting Windows in BIOS boot mode & from UEFI you are booting Ubuntu in UEFI boot mode.
I thought that did not even work. Not really recommended, but if it works then that is ok.

---

### Post by rsteinmetz70112 on 2021-01-11
You have some technical issues with the way the drive is set up, but even more important than that from my perspective you don't have that much space on the HD to work with. Have you considered a new bigger drive?

---

### Post by yancek on 2021-01-11
Best solution is to get another drive as your windows partition is using 80GB of a 99GB partition.  Most of that is likely personal data which could simply move to another internal/external drive.

With the setup you have, you will not be able to increase the size of the Ubuntu partition because it is on a logical partition within an Extended partition and you have the EFI partition between it and your large windows partition.  That's a small drive for a current laptop, especially with windows 10.

---

### Post by arthurconmy on 2021-01-11
Hi, I've now freed up 27GB from sda2 and it is unallocated space. How can I complete your step b)? I think that the key shown in the image means I can't do this while booted into ubuntu, and I can't currently do it from within windows.

---

### Post by yancek on 2021-01-12
>  How can I complete your step b)

You need to be more precise with your questions as there have been 4 members who responded to your post.  Is the statement above referring to the line below in post #3?

>  b) Move sda3 across the unallocated space

Your system appears to be unusual as you have a Legacy install.  We know that as sda4 shows as an Extended partition which means an msdos drive rather than GPT which has no Extended partition.  I'm also curious about sda3 which shows as an EFI partition yet shows only 1.03MB used.  On my laptop with windows and Ubuntu, that partition uses 30MB so it probably isn't being used.

With the msdos type Legacy system you are using, you are only allowed to have 4 primary partitions.  You already have 4 primary partitions so you would have to delete one.  You would then have to unmount and resize the logical (sda5) and Extended (sda4) partitions.  A big problem is that you can't move or extend what is now sda5 directly to use the unallocated space you created by shrinking windows (on sda2) because the EFI partition is between them.   You could copy the Ubuntu system files entirely from sda5 to the new partition you create from the unallocated space or you could create a separate /home partition to use on the newly created partition.  These options have potential to create a lot of problems for an inexperienced user.

Another possibity is to check the EFI partition on sda3 to see if there is actually anything there.  If it truly has only 1.03MB being used then it is empty and you can delete it so I would mount that partition and take a look at it and post that information here.   The commands to use to get this information are as following which you can do from the installed Ubuntu.  Type each command into the terminal and hit the Enter key after each.

>  sudo mkdir /mnt/sda3
sudo mount /dev/sda3 /mnt/sda3

After doing that you should be able to navigate there and see what you have.  Using the terminal and running the following should show a folder named EFI.  Running the second command should show at least folders named Boot, Microsoft and ubuntu.  If you don't see any of those folders, it means you are not using EFI and you can safely delete sda3.  

```
 ls /mnt/sda3
ls /mnt/sda3/EFI
```

A windows OS cannot be installed in EFI mode on a legacy (msdos) system so another way to determine if windows is using EFI is with the fdisk command from Ubuntu.  The output you will see has a line as shown below, Disklabel type.  Mine below is gpt, if it is legacy, it will show msdos which means your windows is not EFI.  That's possible but is not generally done, and certainly not on a preinstalled windows.

>  Disklabel type: gpt

In any case, you need a new drive.  Your Ubuntu partition is too full and won't work and your windows partition is about 80% full and will stop functioning soon if you put more software or data on it.  
MInimum recommended size for a / (root filesystem) partition with a current Ubuntu is about 20GB.  

I think it would be a much simpler and likely more successful process to reinstall Ubuntu after shrinking the windows partition and possibly deleting the EFI partition if you determine it is not being used.  Getting a second external drive for backups of both systems would also be  a good idea.

Dual booting windows 10 and Ubuntu is explained at the site from the link below and is also the official Ubuntu documentation.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by arthurconmy on 2021-01-12
> **yancek said:**
> In any case, you need a new drive.

Thank you for this. I think I will try to follow the steps to expand the ubuntu partition, but am I right in thinking buying a fresh, larger internal hard drive and then setting up ubuntu on that will be the easiest approach?

---

### Post by arthurconmy on 2021-01-12
Hey @grahammechanical, just finished doing this and ubuntu is working more stably. Thanks!

I would still like to know, is buying and installing a new hard drive still a feasible option in future? Windows is still hogging a lot of this partition...

---

### Post by yancek on 2021-01-12
>  I would still like to know, is buying and installing a new hard drive still a feasible option in future?

Yes, several options.  You can get a new drive and use it as a storage medium attaching it to the computer and creating partitions  for windows with a wndows filesystem such as ntfs and another partitioon with a Linux filesystem such as ext4.  Or you can just use ntfs as Linux/Ubuntu will be able to read and write to it.  A default windows system will not be unable to read or write to a LInux filesystem so using an ntfs partition may be the simplest.

You can easily install Ubuntu to an external drive and then format the current partitions of your old Ubuntu install to ntfs to use with windows.  Windows installer will not allow installation on an external drive but that's no a problem in your case.  Before you begin, I would suggest you read through the link I posted in my last post on dual booting windows with Ubuntu.  Since you have a legacy install of windows, you should enable Legacy/CSM boot in the BIOS firmware of your computer and install Ubuntu in Legacy mode.  That way you will be able to boot Ubuntu and windows from the GRub menu in Ubuntu.  If you install Ubuntu in EFI mode, you will have to access the BIOS on boot and select windows there.

If you have questions after reading the Ubuntu documentation, post them here and someone should be able to point you in the right direction.

If you can, before you install Ubuntu, disable or disconnect the windows drive, much simpler if you can do that.

---

### Post by rsteinmetz70112 on 2021-01-13
> **arthurconmy said:**
> Hey @grahammechanical, just finished doing this and ubuntu is working more stably. Thanks!

I would still like to know, is buying and installing a new hard drive still a feasible option in future? Windows is still hogging a lot of this partition...

Yes you can purchase and install a new larger internal hard drive. I would first clone your existing drive to the new drive. Since you are using a laptop you may need to get an USB enclosure to do that although the last laptop I bought had space for both an internal SATA SSD and an M2 SSD. I'm only using one right now since it came with a 2TB drive. I'm not sure if both can be active at the same time. If so you could simply add whichever one is not present that depends on your hardware.

---

### Post by arthurconmy on 2021-04-07
> **yancek said:**
> Yes, several options.  You can get a new drive and use it as a storage medium attaching it to the computer and creating partitions  for windows with a wndows filesystem such as ntfs and another partitioon with a Linux filesystem such as ext4.  Or you can just use ntfs as Linux/Ubuntu will be able to read and write to it.  A default windows system will not be unable to read or write to a LInux filesystem so using an ntfs partition may be the simplest.

You can easily install Ubuntu to an external drive and then format the current partitions of your old Ubuntu install to ntfs to use with windows.  Windows installer will not allow installation on an external drive but that's no a problem in your case.  Before you begin, I would suggest you read through the link I posted in my last post on dual booting windows with Ubuntu.  Since you have a legacy install of windows, you should enable Legacy/CSM boot in the BIOS firmware of your computer and install Ubuntu in Legacy mode.  That way you will be able to boot Ubuntu and windows from the GRub menu in Ubuntu.  If you install Ubuntu in EFI mode, you will have to access the BIOS on boot and select windows there.

If you have questions after reading the Ubuntu documentation, post them here and someone should be able to point you in the right direction.

If you can, before you install Ubuntu, disable or disconnect the windows drive, much simpler if you can do that.

> **rsteinmetz70112 said:**
> Yes you can purchase and install a new larger internal hard drive. I would first clone your existing drive to the new drive. Since you are using a laptop you may need to get an USB enclosure to do that although the last laptop I bought had space for both an internal SATA SSD and an M2 SSD. I'm only using one right now since it came with a 2TB drive. I'm not sure if both can be active at the same time. If so you could simply add whichever one is not present that depends on your hardware.

I have now used 94GB of 98GB of my drive and am forced to use web apps which has been a miserable experience as of late, and want to upgrade.

Is buying a new hard drive (for the HP Elitebook 840) the i) easiest and ii) most affordable way to go about this?

[I am able to make a new thread if necro-posting is frowned upon here]

---

### Post by deadflowr on 2021-04-07
> [I am able to make a new thread if necro-posting is frowned upon here]
It's your thread and it's only been a few months.
As long as any new information pertains to the same topic as before you can keep this thread going.

We have a 1 year time limit of inactivity before the forum automatically closes a thread.
Of course there are reasons why the staff may close a thread before that as listed in the forums rules here:
[https://ubuntuforums.org/misc.php?do=showrules]("https://ubuntuforums.org/misc.php?do=showrules")

---

### Post by Tadaen_Sylvermane on 2021-04-07
I know for awhile laptop hard drives were an easy swap. I'm not sure about newer models though. The thinner they get the less room for a traditional 2.5 drive. As such I would fear that they may be following apple in the idea of built in drive space. This effectively means you need to get the drive space when you buy it. Not upgradeable. I'm only theorizing of course but it's an inevitable thing as these things get thinner as I mentioned above. Usb 3.0 / thunderbolt can make this moot but then you have to drag around an external.

---

### Post by arthurconmy on 2021-04-08
> **Tadaen_Sylvermane said:**
> I know for awhile laptop hard drives were an easy swap. I'm not sure about newer models though. The thinner they get the less room for a traditional 2.5 drive. As such I would fear that they may be following apple in the idea of built in drive space. This effectively means you need to get the drive space when you buy it. Not upgradeable. I'm only theorizing of course but it's an inevitable thing as these things get thinner as I mentioned above. Usb 3.0 / thunderbolt can make this moot but then you have to drag around an external.

Hey thanks so much for the reply. Yeah I'm short on time at the moment and clueless about hardware so carrying round the bulk seems a decent option. I have just searched and my machine does have USB 3.0 ports ([https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/how-do-i-find-out-if-my-usb-port-is-2-0-or-3-0/td-p/1360211;](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/how-do-i-find-out-if-my-usb-port-is-2-0-or-3-0/td-p/1360211;) mine do have the SS), so I'm right in thinking I could just use an external hard drive right?

---

### Post by arthurconmy on 2021-04-09
> **Tadaen_Sylvermane said:**
> I know for awhile laptop hard drives were an easy swap. I'm not sure about newer models though. The thinner they get the less room for a traditional 2.5 drive. As such I would fear that they may be following apple in the idea of built in drive space. This effectively means you need to get the drive space when you buy it. Not upgradeable. I'm only theorizing of course but it's an inevitable thing as these things get thinner as I mentioned above. Usb 3.0 / thunderbolt can make this moot but then you have to drag around an external.

Hey apologies for the double ping but could you check the message above? Really don't want to waste money!

---

### Post by CelticWarrior on 2021-04-09
You can use an external USB drive with USB2.0 or USB3.0, the difference is the former will be much slower.

---

### Post by kurt18947 on 2021-04-09
> **Tadaen_Sylvermane said:**
> I know for awhile laptop hard drives were an easy swap. I'm not sure about newer models though. The thinner they get the less room for a traditional 2.5 drive. As such I would fear that they may be following apple in the idea of built in drive space. This effectively means you need to get the drive space when you buy it. Not upgradeable. I'm only theorizing of course but it's an inevitable thing as these things get thinner as I mentioned above. Usb 3.0 / thunderbolt can make this moot but then you have to drag around an external.

I would be surprised and disappointed by a soldered hard drive in the PC world. What I expect will become common is M2 SATA or more likely NvME. An M2 drive is approximately the size of two sticks of chewing gum and are commonly available in 1 TB capacities. Of course the PC's motherboard must have the appropriate connector and BIOS support.

Edit: Holy Cow! I was browsing Amazon and Inland (of all manufacturers) is advertising a 4 TB M2 2280. Inland drives are typically value propositions. I have a couple Inland SATA drives, they're middling performers but seem reliable.

---

