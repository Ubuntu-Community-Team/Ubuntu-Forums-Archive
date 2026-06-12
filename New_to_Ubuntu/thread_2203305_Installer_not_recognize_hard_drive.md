---
title: "Installer not recognize hard drive"
date: 2014-02-02
forum: New to Ubuntu
---

### Post by drummerboy2 on 2014-02-02
Hello, 


I am a very new Ubuntu User, and now i want to install Ubuntu 13.10 on several PCs i have.  But when i was trying to install in any Dell Inspiron 6000, in the "Installation Type", not show the HD. 
I tried to format the Hard Disk in many ways with Gparted, but nothing happen. 

I tried to install Lubuntu and Bodhi Linux, and the same thing is happen. 

Anybody know what are happening?. Could be something about the version?. 

Any help, comment or suggest are welcome. 

Thanks 
:cool:

---

### Post by bc.haynes on 2014-02-02
If you are new to Ubuntu, and you don't know how to use gparted, ***be careful***, a lot of what it does is irreversible. 
Have you used Ubuntu before trying to install it on all those computers? Perhaps you should use it a while (until you know how to install and work with files & directories) before committing all the work necessary to manage the computers.I would also suggest waiting until April to install Ubuntu 14.04 LTS (Long Term Support). 13.10 is only supported fot 9 months. 14.04 is supported for 5 years (I believe).

[COLOR=#000000]You can Google[/COLOR][COLOR=#ff0000] "gparted tutorial"[/COLOR][COLOR=#000000] and find many helpful pages.  [/COLOR]

---

### Post by whitesmith on 2014-02-02
Start by using the "Try" option on a live CD (or USB drive) to see if Ubuntu recognizes your system. If it does, follow b.c.haynes' suggestion to wait for 14.04 LTS, which will be supported for 4 years. Regards.

---

### Post by drummerboy2 on 2014-02-02
Thanks for answers!. 

You know, if i "try" the Ubuntu in the machine, all seems ok, you know, the system can "see" the HD, but when the installer are running, in the "Installation Type" not appears anything, nothing. 
Looks like a bug in the installer.

---

### Post by bc.haynes on 2014-02-02
What are the options in "Installation Type"?

---

### Post by drummerboy2 on 2014-02-02
Show this (in the pic). This is the screen of the Dell Inspiron 6000 when is running the Ubuntu installer. 

Nothing!.

---

### Post by mastablasta on 2014-02-03
> **drummerboy2 said:**
> Show this (in the pic). This is the screen of the Dell Inspiron 6000 when is running the Ubuntu installer. 

Nothing!.


what happens if you click new partition table? why did you go to manual partitioning? system should offer you to install ubuntu by doing it's own partition scheme.

do you want to dualboot? does the hard disk have ***MS Windows ***installed?

can you run live OS (select try it on start) then run gparted, seelct the disk drive and post the picture of the drive as it is shown there.

or just open terminal while in try it mode and run 

```
sudo fdisk -l


```(that's a small L in the end)

---

### Post by drummerboy2 on 2014-02-03
@Mastablasta, 

Nothing happen, the "new partition table" are unavailable for open or do anything. In the [COLOR=#000000][FONT=arial]beginning i wanted use dual boot, but now i just want install the Ubuntu only, the harddisk are empty now. 

You know if i load the Ubuntu in "Try Ubuntu" mode,  in that way the system "can see" the hard disk, thats the reason i think if
is any Installer Bug. 
I will try your advice using the Terminal comand. 

Thanks! 

[/FONT][/COLOR]

---

### Post by mastablasta on 2014-02-03
you can run installer in "try ubutnu" mode. there should be install icon available to launch it. you can also preformat the disk there (using gparted), but it's not necessary.

try new partition table if you can create it. 

if you have MBR partition table on disk then you can't have more than 4 primary partitions. and if you have them then you can't install ubuntu in dualboot mode or it won't show up the disk. however you can overwrite the disk by selecting to install ubtuntu (use the whole drive) in the menu that appears before your posted screenshot.

---

### Post by fantab on 2014-02-03
> **mastablasta said:**
> ...or just open terminal while in try it mode and run 

```
sudo fdisk -l


```

.. also post the output of:
```
sudo parted -l
```

Are you trying to install Ubuntu along side Windows? Windows7 or 8? 
Give more details about your compter hardware involed...

---

### Post by drummerboy2 on 2014-02-03
Hi, 

This is the output results, using fdisk -l and parted -l in terminal console: 

What do you think about?

---

### Post by fantab on 2014-02-03
Your output to 'sudo parted -l' shows that you don't have space to install Ubuntu.
All your partitions are NTFS. Are you planning on installing Windows? Linux/Ubuntu will NOT install to NTFS. The partition you want to install Linux/Ubuntu then the partition MUST be formatted with Linux filesystem, like Ext4.

Your HDD is only 40Gb. I were you and planning on installing only Linux then I would create:
```
18Gb Primary Ext4 Ubuntu / (Ubuntu's system files)
20Gb Primary Ext4 Ubuntu /home (Your personal DATA)
2Gb Primary LinuxSWAP
```

Or simply:
38Gb Primary Ext4 Ubuntu /
2Gb Primary LinuxSWAP

---

### Post by drummerboy2 on 2014-02-04
@Fantab, 

i did the partitions (in pics), but in the installer still show nothing for install Ubuntu.

Any clue about what is happening?

---

### Post by sudodus on 2014-02-04
Me too, I have no idea what is happening :confused:

I checked the specs of Dell Inspiron 6000 at an internet site, and I think Lubuntu or Bodhi are better alternatives than standard Ubuntu. Xubuntu 12.04 LTS, LXLE and Bento might also be good alternatives (all based on Ubuntu).

If you intend to install to the whole drive, you can also try the standard option at the partitioning page according to my attached screenshots (of Lubuntu 13.10). '***Erase ... and reinstall'***

Let us know what happens in this case!

---

### Post by mastablasta on 2014-02-04
well this is strange...

try this: delete partitions and leave the disk unformated. run install and then choose "use entire disk". partitioning will be done for you.

FYI it did soemthing similar to me on old compaq. it had only two partitions under XP - system and restore i couldn't set up dual boot as it didnt' recognise emtpy disk space, but using whole disk for install worked like a charm.

---

### Post by fantab on 2014-02-04
Check in your BIOS for SATA Mode setting. If the PC earlier had XP then chances are you have IDE or something similar... change it to AHCI. Also check other 'boot settings' and see if anything not normal, or just reset the BIOS defaults...

Also open utility called 'Disks' from Live Ubuntu and run SMART Tests on your HDD... check if its all good with your HDD...

Install and run '[fixparts]("http://www.rodsbooks.com/fixparts/")' on your HDD. If there are any errors with partition table then it can fix those.

Try another distro or another flavor of Ubuntu like Xubuntu or Lubuntu.

---

### Post by drummerboy2 on 2014-02-05
Thanks for all the answers!. 

Well i tried leaving unformat the HD, and reset to default the BIOS settings, and test the HD with few apps, showing the disk is Ok, but nothing happen. 
I will try with others versions like LXLE and Xubuntu, which I did not try yet.

---

### Post by mastablasta on 2014-02-05
so one of the first install pages doens't give you the option to install ubuntu - use the whole disk?

---

### Post by fdrake on 2014-02-05
have you tried with a different installation disk? the hd looks fine.

---

### Post by drummerboy2 on 2014-02-06
I just tried from the same CD Live. Now, with this CD i installed on several PCs.

---

### Post by sudodus on 2014-02-06
Do you say that you have solved your problem now? In that case, please describe what you did to solve the problem, and please click on **Thread Tools** at the top of this page, and mark this thread as SOLVED :-)

---

### Post by drummerboy2 on 2014-02-06
> **sudodus said:**
> Do you say that you have solved your problem now? In that case, please describe what you did to solve the problem, and please click on **Thread Tools** at the top of this page, and mark this thread as SOLVED :-)

Oops!.. I think not explain well. Unfortunately I have not managed to resolve the installation issue. :confused:.

But i will update soon. 

Thanks!

---

### Post by sudodus on 2014-02-07
> **drummerboy2 said:**
> Oops!.. I think not explain well. Unfortunately I have not managed to resolve the installation issue. :confused:.

But i will update soon. 

Thanks!

Yes, please explain the current situation! We are here trying to help :-)

---

### Post by fdrake on 2014-02-07
@drummerboy2 
did you try to change disk or ubuntu version (kubuntu/xubuntu/mint)

if that fails check the bios options as suggesteed earlier..

---

### Post by drummerboy2 on 2014-02-10
Hello guys, 




Well, i tried to install Ubuntu, Kubuntu, Lubuntu, Bodhi Linux and LXLE, but not work. You know, the installer stop in the same step. 
Even, running the Live Xubuntu Session, load the Gparted, and recognize the HD, but in the installer cant see the partitions HD. 
I was thinking, if you can recommend any other Linux Version, maybe have a different Installer, than those versions.

---

### Post by sudodus on 2014-02-11
If the installers cannot see the hard disk drive, I think it is a general problem, and it is not likely that another linux distro will see it. You need to solve that problem first, and then you can probably install any of Ubuntu, Kubuntu, Lubuntu, Bodhi Linux and LXLE, so you can select the one you like the best.

Back to basics. When you have booted the computer from a linux install disk, try the following command and post the output of it

```
sudo parted -l
```

even if you have done it before, we need to know the result ***now***, before giving further advice.

**Edit**: For example, if you have a failing disk or some other failing hardware, things can change rapidly, so we need to know the present situation.

---

### Post by drummerboy2 on 2014-02-11
Thanks Sudodus for your answer!. 

You know, if i type parted -l , shows the same, as the pic. Even change the partitions, the output message is similar. 

The thing is why for example, Gparted can see the HD and manage the partitions, and the Installer not. You know, if the problem is hardware issues, i think, the Gparted should have trouble managing the hard disk or partition.

---

### Post by sudodus on 2014-02-11
OK, parted sees the 40 GB drive and its two partitions.

Since you had tough luck with the ordinary installers, it might be time to try the One Button Installer. It relies on some basic programs, that come with all Ubuntu versions and flavours, for example parted. Maybe you should also check that fdisk recognizes the hard disk drive:

```
sudo fdisk -lu
```

If successful, I suggest that you try to install your favourite version and flavour of linux according to the following link [One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971")

---

### Post by drummerboy2 on 2014-02-13
Hello, 


Well, I could finally installed the Ubuntu, using ubuntu-12.04.4-alternate-i386.iso. This one came with Text Installer, and with this version everything work fine!. 


Here an happy and efficient Ubuntu Dell Inspiron 6000 notebook! 


Thanks to everyone for the comments, suggests, and help! 


Regards.

---

### Post by mastablasta on 2014-02-13
strange indeed. oh well, as longs as it's working fine now :-)

---

### Post by sudodus on 2014-02-13
Congratulations :KS

---

### Post by catalin6 on 2015-02-08
Hello guys,

I'm new, trying to install Ubuntu 14.04 on a Toshiba laptop. I have the same problem discussed on this thread. In the "Installation Type" screen, I have no option to choose from. For more details please check this picture: [http://ubuntuforums.org/attachment.php?attachmentid=250044&d=1391401107](http://ubuntuforums.org/attachment.php?attachmentid=250044&d=1391401107) 

Something came in my attention when I tried to install Windows 7 on the same laptop: a similar problem occurs! Windows installer does not "see" any hard drive to install the operating system on. And the solution I have for this is to load the "Intel RAID Driver" during the Windows 7 installation => it will allow the installation process to detect my drives and I had successfully installed Windows 7.

Now, what I'm trying to say is that the root of the problem MIGHT be the same when I try to install Ubuntu 14.04.
What do you think?
Is there any way to load similar drivers as "Intel RAID Driver" during (or before) Ubuntu installation?

Sorry if this end up being a silly question. I am not familiar with Ubuntu. 

Thanks in advance for your feedback!

---

