---
title: "Toshiba NB100"
date: 2013-10-13
forum: New to Ubuntu
---

### Post by Ged_Kehoe on 2013-10-13
Hi all

I am a complete newbie to Ubuntu and I am having great difficulty in trying to install Ubuntu 10.14.

I have a Toshiba NB100 netbook that was pre-installed with XP Pro. I have completely formatted the hard drive and downloaded and burnt the Ubuntu 10.14 image to disk.

Once I boot from CD it starts to go through the installation process but then gets to a point where I have to choose a drive to install. There is no drive showing at all but the netbook has 120Gb hard drive. 

What am I doing wrong? I hope somebody can point me in the right direction.

Cheers

Ged

---

### Post by leclerc65 on 2013-10-13
You meant 10.04 ? 
It's no more supported. I suggest that you download 12.04.3.
Use option : Erase and use the entire disc, it's simpler for you.
You can also download Parted Magic, use program Partition Editor to format the disc as Ext4 for Ubuntu.

---

### Post by mörgæs on 2013-10-13
Is this our guy?
[http://www.toshiba.co.uk/discontinued-products/toshiba-nb100-12a/](http://www.toshiba.co.uk/discontinued-products/toshiba-nb100-12a/)

If so I would recommend X/Lubuntu 13.10. Ubuntu is a heavy load for an Atom processor.

---

### Post by Ged_Kehoe on 2013-10-13
> **mörgæs said:**
> Is this our guy?
[http://www.toshiba.co.uk/discontinued-products/toshiba-nb100-12a/](http://www.toshiba.co.uk/discontinued-products/toshiba-nb100-12a/)

If so I would recommend X/Lubuntu 13.10. Ubuntu is a heavy load for an Atom processor.

Yep, this the fella. i will try it your way. Thanks for the advice to both of you.

cheers

Ged

---

### Post by Bashing-om on 2013-10-13
Ged_Kehoe; Hi ! Welcome to the forum .

We are here to help, but be advised, there is no 10.14 version of ubuntu. And all 10 version series are no longer supported as they have reached End Of Life. Those support repositories are closed.

As you are installing onto older hardware, may I suggest that you install a lighter version - ubuntu has become resource intensive and takes some hosses for a good experience. I personally like Lubuntu.
See the link at the top of the post "ubuntu community" for several options.
Download the .iso image and verify the integrity of that .iso with md5sum;
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Boot the installer - bios screen clears, hold the shift key ->language screen , escape key to accept default -> boot options screen -> check disk !

Next, boot the installer into the "try ubuntu" mode, make sure all hardware and devices function as expected.
While in "try ubuntu" boot to the desk top. and locate the utility "GParted" .. as you are having difficulties installing, activate "GParted" and LOOK at that disk. At this point it is possible - unlikely - that you will have to format that disk - I like ext4 - . Setting up a hard disk is advanced and should not be necessary. In the install stage, if you want only 'buntu installed -> choose "erase entire disk and install ubuntu" and the install wizard will take care of everything.. all you have to do is answer a few basic questions for locale and username and desired password. With a fast internet connection, install should be done in 15 minutes.

If you have difficulties booting "try ubuntu" we need to address those issues prior to installing to hard disk. 

[INDENT][INDENT]just my little bit
[/INDENT][/INDENT]

---

### Post by Ged_Kehoe on 2013-10-14
> **Bashing-om said:**
> Ged_Kehoe; Hi ! Welcome to the forum .

We are here to help, but be advised, there is no 10.14 version of ubuntu. And all 10 version series are no longer supported as they have reached End Of Life. Those support repositories are closed.

As you are installing onto older hardware, may I suggest that you install a lighter version - ubuntu has become resource intensive and takes some hosses for a good experience. I personally like Lubuntu.
See the link at the top of the post "ubuntu community" for several options.
Download the .iso image and verify the integrity of that .iso with md5sum;
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Boot the installer - bios screen clears, hold the shift key ->language screen , escape key to accept default -> boot options screen -> check disk !

Next, boot the installer into the "try ubuntu" mode, make sure all hardware and devices function as expected.
While in "try ubuntu" boot to the desk top. and locate the utility "GParted" .. as you are having difficulties installing, activate "GParted" and LOOK at that disk. At this point it is possible - unlikely - that you will have to format that disk - I like ext4 - . Setting up a hard disk is advanced and should not be necessary. In the install stage, if you want only 'buntu installed -> choose "erase entire disk and install ubuntu" and the install wizard will take care of everything.. all you have to do is answer a few basic questions for locale and username and desired password. With a fast internet connection, install should be done in 15 minutes.

If you have difficulties booting "try ubuntu" we need to address those issues prior to installing to hard disk. 
[INDENT][INDENT]just my little bit
[/INDENT]
[/INDENT]


Thank you for this. 

I have another problem as well. Everytime I try to install it says 'Disabling IRQ #20' and hangs for ages. Really stuck with this one. This is with Lubuntu.

---

### Post by mörgæs on 2013-10-14
Did you try boot options like noapic?

---

### Post by Ged_Kehoe on 2013-10-14
> **mörgæs said:**
> Did you try boot options like noapic?

Sorry. I have no idea what that is but I will google it. Cheers.

---

### Post by Bashing-om on 2013-10-14
Ged_Kehoe; Hey;

How far are you getting in booting the installMedium to "try ubuntu" mode ?
What version and distro are you presently trying to install ?
If problem persist, describe in detail the steps you are taking and what/where the boot process is halting, At that point, what do you see ? 

[INDENT][INDENT]an earnest desire
[/INDENT][/INDENT]

---

### Post by Ged_Kehoe on 2013-10-14
> **Bashing-om said:**
> Ged_Kehoe; Hey;

How far are you getting in booting the installMedium to "try ubuntu" mode ?
What version and distro are you presently trying to install ?
If problem persist, describe in detail the steps you are taking and what/where the boot process is halting, At that point, what do you see ? 
[INDENT][INDENT]an earnest desire
[/INDENT]
[/INDENT]


Hi. Thank you for this. It is now working perfectly. I updated my BIOS and tried to install and it worked great. Picked up the wireless no problem.

Once again thank you very much. Now to change my laptop from Vista.

Ged

---

### Post by Bashing-om on 2013-10-14
Ged_Kehoe; Outstanding !

Welcome to our world. I look forward to reading you often.

Please mark this thread as solved - 1st post -> thread tools @ top right of post.

[INDENT][INDENT]above all, enjoy
[/INDENT][/INDENT]

---

