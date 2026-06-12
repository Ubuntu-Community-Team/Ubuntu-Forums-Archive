---
title: "Dual Boot on Two Drives"
date: 2006-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by gn2 on 2006-10-11
**EDIT:**This thread is now largely irrelevant, as 7.04 has an "Advanced" button at the Grub installation stage, which when pressed gives the option to enter a different location for Grub to be written to.

_________________________________________________________________________________________________________________________________________________________________




Generally in Ubuntu **EDIT: up to6.10?** the usual way to install a dual-boot system involves overwriting the Master Boot Record of the Windows hard drive.

On one hard drive this is pretty much unavoidable.

However,

If you are dual-booting with TWO hard drives it is not necessary to write Grub over the MBR if you can access a "Boot Device Selection Menu" by pressing F8
(or whatever key depending on BIOS)

You can thus keep both installations entirely separate.

To do it this way:

Disconnect the Windows drive and install Ubuntu and Grub on the second drive. Reconnect first drive after installing Ubuntu.

Windows on master, Ubuntu & Grub on slave if using two IDE drives.

(This method will also work on SATA drives, or a mix of SATA & IDE)

Press F8 (or whatever key depending on BIOS version) at boot time to bring up the Boot Device Selection Menu.

Choose OS by selecting which drive to boot from.

Select desired default OS by re-arranging boot order in BIOS.

Only need to press F8 to select non-default OS.

Re-boots are as quick as using traditional Grub-in-MBR option. 

Always disconnect other OS's drive if re-installing.

This process will also work for adding Windows to an Ubuntu system

Access to files on either drive can be configured later on, once you've got a safe installation organised.


**Edit: The following information will allow dual-booting on two drives with all BIOS versions, with a little editing of Grub. Thanks are due to Anaconda and Bulldog**


Yep all good and so, but..

it would be even better if the hd with ubuntu is the master and windows hd is the slave.

Everything would work just like in your example (no grub in windows drives mbr), but you wouldn't have to do anything in the bios, and in all bios:s it propably even isn't possible to select the booting drive..

But if you have ubuntu in master, then when you boot you would go to grub, and you can select which os is booted. The only thing you would have to do is edit /boot/grub/menu.lst and add windows to your grub..

title Windows NT/2000/XP (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

remapping hd:s when booting to windows from slave drive is nesessary, because windows wants to think it is in the master drive..

and if you remove either hd from your machine, the other one would work normally like in your example...
__________________
____________
anaconda 

gn2: The end result is the same, Grub is kept off the Windows MBR.

Bulldog has also made posts advocating this method.

Definitely a very good thing.


GUI Grub Editor Info: [http://www.ubuntuforums.org/showthread.php?t=228104](http://www.ubuntuforums.org/showthread.php?t=228104).

---

### Post by gn2 on 2006-10-11
Duplicate post from merged threads.

---

### Post by Mojosdad on 2006-10-12
I did pretty much a similar thing, but as my BIOS had some strange issues about ignoring the HD boot order after the boot menu had been used I just changed the GRUB menu.list to also include Windows in the boot selection.

This way I can boot into either Ubuntu or Windows, and Grub/MBR problems only bring down one OS.

---

### Post by gn2 on 2006-10-12
> **Mojosdad said:**
> I did pretty much a similar thing, but as my BIOS had some strange issues about ignoring the HD boot order after the boot menu had been used I just changed the GRUB menu.list to also include Windows in the boot selection.

This way I can boot into either Ubuntu or Windows, and Grub/MBR problems only bring down one OS.

I reckon that so long as you keep Grub on the Ubuntu drive your Windows should be safe enough.

---

### Post by weird_c00kie on 2006-10-13
thanks for the link to this gn2, but i don't think it would help me, given my situation right now.
i need the two OSs to be able to communicate, so i can back my windows stuff up on the linux drive, format the windows one and then restore the data again. having them ignore each other wouldn't help me too much. i get what you're saying though, which is a relief heheh

i'm more interested to hear how Mojosdad edited his grub menu.list to include windows heheh

---

### Post by d3v1ant_0n3 on 2006-10-13
I just had a read of your (weird_c00kie) other thread, and this one also..I'm having isssues with our desktop, and the kids hate having to select windows from grub (they're lazy).

This suggestion does seem like a workable one for 2 HDD's...The 2 OS's won't actually ignore each other, and once you have the whole mounting NTFS/Making Ext3 visible in Windows issues sorted, they should be able to communicate.

The only difference this should make is that, instead of having to select your OS through grub, you have to select it through the Boot Menu popup from bios.

Going to give this a try later and see how it goes methinks.

---

### Post by weird_c00kie on 2006-10-13
i'd personally find it more of a hassle having to go into the bios everytime than i would having to pick it at the grub screen, but maybe that's just me heheh

---

### Post by Khaotik on 2006-10-13
> i'd personally find it more of a hassle having to go into the bios everytime than i would having to pick it at the grub screen, but maybe that's just me heheh

Na, I totally agree with you.

Also considering not all BIOS' are the same or even have this F8 boot menu you are speaking of, Its alot easier just to install GRUB to the MBR of hd0. If there are any problems pop in a repair disk. 2 Minute fix. :D

---

### Post by gn2 on 2006-10-13
> **Khaotik said:**
>  If there are any problems pop in a repair disk. 2 Minute fix. :D

Only quick fix if all goes well......

And that doesn't always happen sadly.

---

### Post by sirius10 on 2006-10-13
Hey, I have the same problem. 2 hardiscks - 2 operating systems. First is Ubuntu, 2nd is WinXP. I waited for Grub to show the menu in which I would choose the OS but it only tells me to press ESC to enter the menu. I did so and WinXP it's not even listed! I'm a fresh Ubuntu/Linux user, I didn't even knew till today that there should have been a menu... I booted different OS by changing info in BIOS!:(  Please, is there anyone there who could help me? Maybe enlight me a little bit? And, something else: I read somewhere else that is not a good idea to install Windows after Ubuntu (but I just found out that too...) Is it true? Help, help, help!

---

### Post by confused57 on 2006-10-13
> **sirius10 said:**
> Hey, I have the same problem. 2 hardiscks - 2 operating systems. First is Ubuntu, 2nd is WinXP. I waited for Grub to show the menu in which I would choose the OS but it only tells me to press ESC to enter the menu. I did so and WinXP it's not even listed! I'm a fresh Ubuntu/Linux user, I didn't even knew till today that there should have been a menu... I booted different OS by changing info in BIOS!:(  Please, is there anyone there who could help me? Maybe enlight me a little bit? And, something else: I read somewhere else that is not a good idea to install Windows after Ubuntu (but I just found out that too...) Is it true? Help, help, help!
Maybe this thread can help:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
Ignore the section on disconnecting drives, etc...you already have Ubuntu & Windows installed, you might just want to try adding the Windows entry manually to your /boot/grub/menu.lst.

You might want to open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L"
 
then
```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list, not menu.first

Post the output of the above 2 commands, if you can't get Windows to boot from the link I gave you.

---

### Post by gn2 on 2006-10-13
> **confused57 said:**
> 
Ignore the section on disconnecting drives, etc...

But that's what this thread is all about,  the option to circumvent Grub issues which are a complete pain in the a**e

---

### Post by Cubbybearks on 2006-10-13
I was able to create a boot disk for WindowsXP on a floppy and edit the boot.ini settings to include Ubuntu that way when I want to boot from Ubuntu I insert the disk to and when I dont I leave the disk out of the drive works for me since I share a computer with someone else and we each have our own hard drives

---

### Post by confused57 on 2006-10-13
> **gn2 said:**
> But that's what this thread is all about,  the option to circumvent Grub issues which are a complete pain in the a**e
Yes, I agree grub can be difficult to configure, but I wanted to offer another choice for the poster that I replied to(he mentioned he'd already booted using bios).  In fact, I've placed a link to this thread in the "howto" that I supplied in my other reply, for anyone who might want to use bios to boot Ubuntu & Windows on different hard drives.

Using bios to boot Ubuntu or Windows is a viable option and is preferred by many people dualbooting with 2 hd's.

---

### Post by gn2 on 2006-10-13
> **confused57 said:**
> 
Using bios to boot Ubuntu or Windows is a viable option and is preferred by many people dualbooting with 2 hd's.

I say it should be the recommended option.

The popular conception these days is that Ubuntu "Just works"

So it's a pity the hazards of dual-booting and Grub aren't better explained at the outset to the unsuspecting new user, who comes full of hope and expectation. 

And often ends up severely hacked off.

I would suggest that single hard drive dual booting should carry much more warnings and explanation of all the potential hazards in the official documentation. Without this Ubuntu is being reckless with prospective users' valuable data.

I found out about it the hard way, and I wouldn't wish it on others......

---

### Post by Coelocanth on 2006-10-13
Gn2, if I may ask: what happened to you when you installed your dual boot? I've seen a number of your posts referencing a bad experioence with it. I ask because I (as the noob I am) installed Ubuntu as a dual boot with XP on the same SATA drive and had GRUB install on the mbr, but I've had no troubles whatsoever. Makes me nervous now, as I'm thinking of installing another SATA drive and loading Edgy on it once it's released, so now I'm wondering how I should go about doing so.

Feel free to toss me a PM if you think this is too off topic for this thread. Cheers.

---

### Post by sirius10 on 2006-10-14
Thank you so much! Your link really helped me!
I did that step by step and now Grub shows me the menu and I have the possibility to boot whatever OS I desire. Automatically, it boots the XP if I don't choose otherwise. Even though I work much more with Ubuntu than with XP  it's great that I don't need to enter Bios and loose time this way.
Is there any possibility to include that helpful thread in the WIKI or something? I'm sure that there are a lot of people that would find this very helpful, as I did. 
Thanks again for your help!:D

---

### Post by Mojosdad on 2006-10-14
I agree dual-booting hazards (especially GRUB failures) should be made clearer.

My original install of 5.10 to a second HD coincided with its failure, leaving me with GRUB looking for a second disk that didn't exist and no Windows MBR on the primary. Luckily I know about FixMBR, I'd never alter hd0 MBR again. My philosphy now is one OS on one HD which is bootable on its own.

Second time round I intalled 6.06 to the secondary HD (after discconnecting master) and put GRUB on the slave MBR. Connected the master back up and got the BIOS to boot from the slave disk first. Changed the grub list to add Windows partition.

Like I said I only altered the grub menu because my BIOS ignores the preset boot order if the F8 menu has been used (ever!)

---

### Post by magicsmoke on 2006-10-14
I did a dual boot with 2 HDD's as well.  I have 3 HDDs, (1 sata with win xp, 1 ide as storage, and another sata i put ubuntu on).  I disconnected the first 2 drives mentioned to do the Ubuntu install but when i reconnected them afterwards, Ubuntu fails to load.  I changed boot order in my bios and Ubuntu will start the loading process, but fails shortly after.  I can change the boot order for my win xp hdd and win xp will load just fine.  My guess is that Ubuntu is trying to load the filesystem from my ide drive since thats disk 0 (not sure why its the first disk).

Any suggestions?  I think I have to chnage what hd Ubuntu thinks the filesystem is on, but thats a big guess since i'm still new linux.

---

### Post by oxymoron on 2006-10-15
This boot from bios option is exactly what i have been after!

I just need something clarified b4 i try it. My second drive is my data storage & i will still need to partition this drive for windows use. 

By using the 1st section of the drive for windows & the second section of the drive for xubuntu, will it still boot into xubuntu from the boot menu F8?

Given that in reality the second drive will be partitioned & not used in its entirety for Xubuntu.

Many thanks for any help on this :)

Oxy, a recent SuSe convert :)

---

### Post by gn2 on 2006-10-16
> **oxymoron said:**
> This boot from bios option is exactly what i have been after!

I just need something clarified b4 i try it. My second drive is my data storage & i will still need to partition this drive for windows use. 

By using the 1st section of the drive for windows & the second section of the drive for xubuntu, will it still boot into xubuntu from the boot menu F8?

Given that in reality the second drive will be partitioned & not used in its entirety for Xubuntu.

Many thanks for any help on this :)

Oxy, a recent SuSe convert :)

One OS and it's own bootloader on each hard drive for this solution.

It's a workaround for eliminating the hazards of two OS's on one hard drive

---

### Post by bulldog on 2006-10-16
Well I'm very stubborn on this :D 

You must have the possebillity to set the bootdevice in your BIOS to do it my way.

I have a IDE master and a Sata which can be master as well slave.

I set the IDE as first bootdevice in BIOS and install windows on it.

Then select the Sata as bootdevice in BIOS and install Ubuntu on it.
[don't unplug your IDE hdd]

GRUB will be installed on the Sata drive and detects windows and add it to the menu.lst.
Also fstab will be up to date!

Only thing to do is to map your hdd's in menu.lst because windows likes to be on the first boot device.
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader	+1
```

What I have achieved this way,I can boot windows and Ubuntu from GRUB,but if GRUB is corrupted for what reason,I can change the boot device in BIOS or by pressing F11 to change it to the IDE hdd and boot windows with its own bootloader.

This is the most comfortable way to use dual boot with two hdd's.

By the way,reinstalling GRUB with the live cd is very easy to do and cost no more as 10 minutes.

I'm much more concerned about gparted where you could erase the wrong partition and lose a lot of data by a mouse click.

---

### Post by anaconda on 2006-10-16
Yep all good and so, but..

it would be even better if the hd with ubuntu is the master and windows hd is the slave.

Everything would work just like in your example (no grub in windows drives mbr), but you wouldn't have to do anything in the bios, and in all bios:s it propably even isn't possible to select the booting drive.. 

But if you have ubuntu in master, then when you boot you would go to grub, and you can select which os is booted. The only thing you would have to do is edit /boot/grub/menu.lst and add windows to your grub..

title		Windows NT/2000/XP (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader	+1

remapping hd:s when booting to windows from slave drive is nesessary, because windows wants to think it is in the master drive..

and if you remove either hd from your machine, the other one would work normally lik in your example...

---

### Post by xpod on 2006-10-16
lol....i wondered when you were going to get round to that.

I just took a master hd with windows out of another pc,swapped its jumpers over to slave and was going to keep things tidy like you say....

Somehow though edgy ended up on the thing and i forgot all about f8;)

---

### Post by gn2 on 2006-10-16
> **anaconda said:**
> Yep all good and so, but..

it would be even better if the hd with ubuntu is the master and windows hd is the slave.

Everything would work just like in your example (no grub in windows drives mbr), but you wouldn't have to do anything in the bios, and in all bios:s it propably even isn't possible to select the booting drive.. 

But if you have ubuntu in master, then when you boot you would go to grub, and you can select which os is booted. The only thing you would have to do is edit /boot/grub/menu.lst and add windows to your grub..

title		Windows NT/2000/XP (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader	+1

remapping hd:s when booting to windows from slave drive is nesessary, because windows wants to think it is in the master drive..

and if you remove either hd from your machine, the other one would work normally lik in your example...


For those who can access a "Boot device selection menu" (and that's the majority of PC's) doing it the way I suggest completely avoids having to muck about with Grub.

But I agree that for those who don't have this facility your method is preferable to having Grub over the MBR on the Windows drive.

I have posted elsewhere on this, and think there should be more warnings for new users about the potential problems associated with the standard single drive dual-boot set-up.

---

### Post by bulldog on 2006-10-16
> **anaconda said:**
> Yep all good and so, but..

it would be even better if the hd with ubuntu is the master and windows hd is the slave.

Everything would work just like in your example (no grub in windows drives mbr), but you wouldn't have to do anything in the bios, and in all bios:s it propably even isn't possible to select the booting drive.. 

But if you have ubuntu in master, then when you boot you would go to grub, and you can select which os is booted. The only thing you would have to do is edit /boot/grub/menu.lst and add windows to your grub..

title		Windows NT/2000/XP (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader	+1

remapping hd:s when booting to windows from slave drive is nesessary, because windows wants to think it is in the master drive..

and if you remove either hd from your machine, the other one would work normally lik in your example...

You've got the picture.:D 

gn2 is a little chicken about GRUB :D 

But what anaconda says is my way too.

The way gn2 want's us to do things,require setting up fstab manually.
And there are folks around who wont like this a bit :D 

Cheers.

---

### Post by gn2 on 2006-10-16
> **bulldog said:**
> 
gn2 is a little chicken about GRUB :D 

The way gn2 want's us to do things,require setting up fstab manually.
And there are folks around who wont like this a bit :D 



Not at all chicken, just don't like unnecessary tweaking. I'm lazy.

Must confess I do my F8 dual-booting with a Distro which will configure access to other drives by means of a simple GUI. PCLinuxOS.

Use Ubuntu single booted on an old laptop though...

---

### Post by bulldog on 2006-10-16
Well you and I have a different view on how to install on two hdd's.

Both are good and trusty.

In my opinion is my way a little more comfortable,but you will disagree I suppose.:D :D 

You promote your way and I mine lol.

---

### Post by gn2 on 2006-10-17
> **bulldog said:**
> Well you and I have a different view on how to install on two hdd's.

Both are good and trusty.

In my opinion is my way a little more comfortable,but you will disagree I suppose.:D :D 

You promote your way and I mine lol.

I would concede that yours will work on any PC, but mine is dependent on the type of BIOS.

Glad we agree the main thing, which is to avoid overwriting the MBR on the windows drive.

---

### Post by gn2 on 2006-10-19
Aha! it works with RAID too!

[http://www.ubuntuforums.org/showthread.php?t=279947](http://www.ubuntuforums.org/showthread.php?t=279947)

---

### Post by Acollective on 2006-10-19
This thread should be stickied. I had the Grub on windows MBR problem and gave up on ubuntu for a while cause I just didn't have time to figure it out. 

   Of course now I feel foolish for not figuring it out myself 
:)

A. Collective
--ADJ. 	collective - forming a whole or aggregate--

---

### Post by gn2 on 2006-10-19
> **Acollective said:**
> This thread should be stickied. I had the Grub on windows MBR problem and gave up on ubuntu for a while cause I just didn't have time to figure it out. 

   Of course now I feel foolish for not figuring it out myself 
:)

A. Collective
--ADJ. 	collective - forming a whole or aggregate--

Same topic, different thread on Support Forum, more posts, you're not alone.

[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)
.

---

### Post by Bigbluecat on 2006-10-19
Alright - I'll chuck my 2p in.

I dual boot on two HDD and have grub in the MBR. Had my share of problems getting it running but I learned a lot about grub and booting in getting the system working right. 

That is in part why I started using Linux. I wanted to learn from it. 

Have no problems now fixing MBR, manually booting Kernels and re-writing menu.lst.

Can't do that if it works too well first time.:-k

Still - next time if I have to re-do things I may use Bulldog's method.

---

### Post by gn2 on 2006-10-19
> **Bigbluecat said:**
> 
Have no problems now fixing MBR


And if you are lucky that will continue, if not.....?

Fixmbr will not always work. Fact.

So don't let that MBR end up a grubby mess.

---

### Post by Torquemada28 on 2006-10-20
I have Windows installed on a SATA drive and Ubuntu installed on the primary master IDE. I installed a new SATA drive and booting windows from grub has caused problems ever since. I want to make sure that grub is still linking to the drive/partition with windows on it but, being the noob that I am, I'm not familiar with the designations used in menu.lst. 

This is the output of fdisk:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2709    21760011    7  HPFS/NTFS
/dev/sda2            2710       38913   290808630    5  Extended
/dev/sda5            2710       21958   154617561    7  HPFS/NTFS
/dev/sda6           21959       38913   136191006    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1275    10241406    7  HPFS/NTFS

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2685    21567231   83  Linux
/dev/hda2            2686        4865    17510850    f  W95 Ext'd (LBA)
/dev/hda5            2686        4664    15896286   83  Linux
/dev/hda6            4665        4865     1614501   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       12749   102406311    7  HPFS/NTFS
/dev/hdb2           12750       24321    92952090    f  W95 Ext'd (LBA)
/dev/hdb5           12750       24321    92952058+   7  HPFS/NTFS

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        1335    10723356    7  HPFS/NTFS
/dev/hdd2            1336       14593   106494885    f  W95 Ext'd (LBA)
/dev/hdd5            1336        5159    30716248+   7  HPFS/NTFS
/dev/hdd6            5160       14593    75778573+   7  HPFS/NTFS

```

As you can see, I have a whole lot of drives.8) 
The partition with windows is /dev/sda1 and the Ubuntu drive is /dev/hda1.

Here's the output of menu.lst concerning the windows drive:

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP
root            (hd3,0)
savedefault
makeactive
map             (hd0) (hd3)
map             (hd3) (hd0)
chainloader     +1

```

I know it says "on /dev/sda1" but what does "(hd3,0)" mean?
What does this refer to? I thought it would mean the first partition of the third harddrive but I'm not sure how SATA drives fit into the numbering scheme.
Is menu.lst referring to the correct place or does it require some editing?

---

### Post by gn2 on 2006-10-20
> **Torquemada28 said:**
> I have Windows installed on a SATA drive and Ubuntu installed on the primary master IDE. I installed a new SATA drive and booting windows from grub has caused problems ever since. 

So don't boot it from Grub?

Sorry I can't help, my area of interest is in avoiding having to muck about with editing Grub, which is a major P.I.T.A.

Maybe Bulldog would oblige, he enjoys that kind of thing?
.

---

### Post by bulldog on 2006-10-20
I'm not sure how it will figure out in your configuration,but it isn't that hard to find out.

You have three disks,2 IDE and 1 Sata.
Sata has no more master or slave like an IDE drive.

You van try to make (hd3.0) into (hd1.0) to see if windows will boot.

You have only a few options to try out and it shouldn't be that hard to figure out how the mapping should be.

But as I can see your Ubuntu is bootdevice 1 which in GRUB language = 0

Your windows is sda1 no master slave configuration and should be bootdevice 2 in GRUB language = 1

But if this doesn't workout make it 0 and 2.

but you should use (hd0.0) instead of (hd0) the second 0 stands for the partition which is used.

Should not be to difficult to do,just a little experimenting.

Make a copy of your menu.lst before you go messing with it.```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```so if things go bad you can copy it back.

---

### Post by bullinchinashop on 2006-10-20
This is one of the few things about Ubuntu that really ticks me off. Zenwalk Slackware SUSE & Vector let you decide where the boot loader is installed. You can also choose to not install a boot loader or to install it to a floppy (of course I yanked out my floppy ages ago...might be time to go buy another :) )
Automatically installing a bootloader is nice for absolute beginners but Ubuntu really should give you the option to control how where and if a boot loader is installed.

---

### Post by Herman on 2006-10-20
> This is one of the few things about Ubuntu that really ticks me off. Zenwalk Slackware SUSE & Vector let you decide where the boot loader is installed. You can also choose to not install a boot loader or to install it to a floppy (of course I yanked out my floppy ages ago...might be time to go buy another :smile: )
Automatically installing a bootloader is nice for absolute beginners but Ubuntu really should give you the option to control how where and if a boot loader is installed. Hello bullinchinashop, bulldog, gn2 and others,
The 'Alternate' Installations CD has always catered for that, and is the original Ubuntu installer, the only type of installation available for  the earlier releases of Ubuntu. 
Many people didn't like having so many options, they found it 'confusing', they wanted the install to be simpler, therefore the 'Desktop' Live/Install CD was developed for those people.

The Ubuntu 'Alternate CD .iso is available for each release, downloadable from the same site where you downloaded your 'Desktop CD .iso from. It is quite easy to use, refer to my signature links for some illustrated examples of it's use. It's actually quite straighforward, most people can follow it.

This page [***(Click Here)***]("http://users.bigpond.net.au/hermanzone/p6.htm#Installing_a_Boot_Loader_for_Ubuntu") shows how you can choose between Grub or Lilo, or continue without a bootloader at all if you like. Grub can be installed almost anywhere, including to the MBR of any hard disk the user cares to specify. (See figure 10). Lilo can be installed anywhere too. (See figure 13).

If you install with the 'Alternate' CD, (with all your disks plugged in), the installer will have a chance detect your other installed operating systems, and add those to the Grub menu automatically for you. It might automatically mount your other partitions for you in /etc/fstab as well. 
It will be less confusing for you in the long run too, as instead of having every disk set up and configured as 'hda', like an all Windows system, (all thinking they are 'drive C', ignorant of the other disks and partitions in the computer), operating systems on each disk will be set up with thier correct hard drive designation.

If you want to see in advance how to later remove Grub from the MBR, I listed quite a few ways on this page, if one doesn't work, you can choose another. [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
There is nothing sacred about the MBR, it is made of the same materail as the rest of the hard disk, and can be written to and overwritten as many times as you like. It won't wear out. Grub is easily removed if you no longer need it or decide it isn't working well in your particular installation.

You can use GAG Boot Manager from a floppy disk, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")
to boot your computer with, or install GAG to MBR, if you wish.

However, it is useful to be aware of the idea of running the installer with the disks unplugged and using the F8 key to boot up with if your particular PC configuration is confusing for the installer and Grub, such as when IDE and SCSI disk are mixed, or when people have a modified computer, with drives plugged in in unique ways. The F8 key idea is a great idea for those installations, and I would like to thank gn2 for thinking of it, realizing it's usefulness, and promoting it, it's a great workaround for some of those tricky situations, so gn2 has done us all a great service by making us all aware of that possibility's usefulness. gn2 really does deserve a pat on the back. =D>

Regards, Herman :-D

---

### Post by liveforfunnow on 2006-10-20
quick question from a bonda-fine noob:

i have 2 sata drives, one already has a winblows xp installation. do i need to disconnect it from the MB to install ubuntu to the other drive? or can i just select it from the GUI installer?

---

### Post by kondor on 2006-10-20
I'm glad I found this post. I currently have a machine with 3 SATA drives running sda: WinXp; WinXPMedia Edit.//sdb:SUSE10.0; Ubuntu 6.10RC and Kubuntu 6.10RC. I had Ubuntu CE on sdb also yesterday.

I was booting them all from the Grub entry on the MBR, with the default Kubuntu6.10RC. I had intended partitioning sdc for several Linux installs, as FedoraC6 is due out next week and I wanted to try it. I'm going to change the installs on sdb shortly, as I want to add Xubuntu to the mix. 

I didn't realize that there was a problem with booting with GRUB installed into the MBR. What happens to GRUB that causes problems if it is located in the MBR? I need to know before a problem comes up. The installer always recognizes the other installed OS(s) and always tells me that there shouldn't be any problems if it puts GRUB into the MBR of sda.

GRUB updates the config when a kernel is updated which is handy, I think.

Thanks.

---

### Post by Herman on 2006-10-21
> quick question from a bonda-fine noob:
i have 2 sata drives, one already has a winblows xp installation. do i need to disconnect it from the MB to install ubuntu to the other drive? or can i just select it from the GUI installer? Hello liveforfunnow, 
The currently popular Ubuntu 'Desktop' Live/Install .iso , or CD, is the one that has the 'GUI' partitioner, which is very good. It installs Grub to MBR of the first hard disk. 
Here's a good how-to about that, [Install Desktop CD Ubuntu]("http://www.psychocats.net/ubuntu/installing")

The Ubuntu 'Alternate' .iso (CD) is menu based (or text based if you like). That one allows you to perform special installations of Ubuntu. You can have a choice of Grub or Lilo bootloaders, and choose to install one of them to any hard disk, floppy disk, or to a partition's first sector.
Here's an illustrated how-to for that one, [Install Alternate CD Ubuntu]("http://users.bigpond.net.au/hermanzone")

You don't really need to unplug any hard disks or open your computer case to install Ubuntu, but you can do so if you want to. 
Most people would not be comfortable with opening up their computer cases themselves and messing around in there without the proper tools and training, you can ruin your computer in just a few seconds. I don't mean just the software and data either. But if you are comfortable with that and you know what you are doing, then by all means, do whatever you think will be easiest and best for you and your machine. Sometimes that really is the best thing to do, but mainly only if you have a machine that is a little different in some way, and Grub doesn't install and work well for some reason.

Regard, Herman :D

---

### Post by Herman on 2006-10-21
> I didn't realize that there was a problem with booting with GRUB installed into the MBR. What happens to GRUB that causes problems if it is located in the MBR? I need to know before a problem comes up. The installer always recognizes the other installed OS(s) and always tells me that there shouldn't be any problems if it puts GRUB into the MBR of sda.

GRUB updates the config when a kernel is updated which is handy, I think.Hello, kondor
Nothing bad happens, it's just that there are a few machines that grub has trouble automatically configuring itself in, and if the user doesn't know how to configure Grub, and is too shy to ask for help, they become distressed and sometimes angry.
Grub can easily be configured most of the time if the user gets help, or does a little reading and learns how to use Grub. 

Regards, Herman :D

---

### Post by gn2 on 2006-10-21
> **bullinchinashop said:**
> This is one of the few things about Ubuntu that really ticks me off. Zenwalk Slackware SUSE & Vector let you decide where the boot loader is installed. You can also choose to not install a boot loader or to install it to a floppy (of course I yanked out my floppy ages ago...might be time to go buy another :) )
Automatically installing a bootloader is nice for absolute beginners but Ubuntu really should give you the option to control how where and if a boot loader is installed.

And warn of the implications if you subsequently want to remove Ubuntu and Grub.

fixnbr will not always work, and getting the space used by Ubuntu back isn't always easy. gparted sure isn't Partition Magic, and most PC owners don't have a Windows disc, just recovery software.

---

### Post by bullinchinashop on 2006-10-21
> **gn2 said:**
> And warn of the implications if you subsequently want to remove Ubuntu and Grub.

fixnbr will not always work, and getting the space used by Ubuntu back isn't always easy. gparted sure isn't Partition Magic, and most PC owners don't have a Windows disc, just recovery software.

The biggest problem I've had outting Grub/LILO on the MBR is when I  install a different distro. I had aLinux installed and installed Zenwalk over it. I deleted & recreated the aLinux partition but when I tried to boot into ZenwalkI still got the aLinux boot manager (Can't remember which it was,sorry). If I chose aLinux on the boot loader I would get about 10 seconds of aLinux's splash screen and then then a lot of noise in the picture and then Zenwalk would finally load. 
I wish there was some way to write the boot loader to a bootable cd-r (I got rid of my floppy ages ago & I'd have to get rid of a hard drive to put in another one). Most disto's give you the option to write LILO/Grub to a floppy but do they realize that there are more & more computers being shipped w/out floppies? I'm pretty sure my sister's Dell came w/out a floppy drive...

---

### Post by gn2 on 2006-10-21
> **Herman said:**
> Hello bullinchinashop, bulldog, gn2 and others,
The 'Alternate' Installations CD has always catered for that, and is the original Ubuntu installer, the only type of installation available for  the earlier releases of Ubuntu. 
Many people didn't like having so many options, they found it 'confusing', they wanted the install to be simpler, therefore the 'Desktop' Live/Install CD was developed for those people.

The Ubuntu 'Alternate CD .iso is available for each release, downloadable from the same site where you downloaded your 'Desktop CD .iso from. It is quite easy to use, refer to my signature links for some illustrated examples of it's use. It's actually quite straighforward, most people can follow it.

This page [***(Click Here)***]("http://users.bigpond.net.au/hermanzone/p6.htm#Installing_a_Boot_Loader_for_Ubuntu") shows how you can choose between Grub or Lilo, or continue without a bootloader at all if you like. Grub can be installed almost anywhere, including to the MBR of any hard disk the user cares to specify. (See figure 10). Lilo can be installed anywhere too. (See figure 13).

If you install with the 'Alternate' CD, (with all your disks plugged in), the installer will have a chance detect your other installed operating systems, and add those to the Grub menu automatically for you. It might automatically mount you other partitions for you in /etc/fstab as well. 
It will be less confusing for you in the long run too, as instead of having every disk set up and configured as 'drive C', like an all Windows system, (or all thinking they are 'hda', ignorant of the other disks and partitions in the computer), operating systems on each disk will be set up with thier correct hard drive number.

If you want to see in advance how to later remove Grub from the MBR, I listed quite a few ways on this page, if one doesn't work, you can choose another. [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
There is nothing sacred about the MBR, it is made of the same materail as the rest of the hard disk, and can be written to and overwritten as many times as you like. It won't wear out. Grub is easily removed if you no longer need it or decide it isn't working well in your particular installation.

You can use GAG Boot Manager from a floppy disk, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")
to boot your computer with, or install GAG to MBR, if you wish.

However, it is useful to be aware of the idea of running the installer with the disks unplugged and using the F8 key to boot up with if your particular PC configuration is confusing for the installer and Grub, such as when IDE and SCSI disk are mixed, or when people have a modified computer, with drives plugged in in unique ways. The F8 key idea is a great idea for those installations, and I would like to thank gn2 for thinking of it, realizing it's usefulness, and promoting it, it's a great workaround for some of those tricky situations, so gn2 has done us all a great service by making us all aware of that possibility's usefulness. gn2 really does deserve a pat on the back. =D>

Regards, Herman :-D


I would argue that Ubuntu should have explicit warnings and give prospective dual-booters full information about loading Grub in their Windows MBR.

Should the new or first-time user decide to remove Ubuntu and Grub, he/she can end up without a working PC.

Should fixmbr fail, as indeed it can, they can end up having to re-install Windows, which is a major P.I.T.A. and potentially disastrous in terms of data loss.

I got caught out this way, fortunately I am a fastidious backer-upper, so it was just a nuisance. Others may not be so lucky.

As for Grub, a quick scan of the forums will easily reveal the true story of it's reliability...

(As I know you are well aware of Herman)

So again I urge the Ubuntu staff to look at things from  the perspective of someone coming to Ubuntu full of hope ad expectation, but with little or no knowledge of the implications of over-writing their Windows MBR with Grub.

It's easy once you know how, but the innocent newccomer doesn't know what he doesn't know. It's up to the install software to tell/warn him fully. With detailed explanations.

---

### Post by bullinchinashop on 2006-10-21
> **gn2 said:**
> I would argue that Ubuntu should have explicit warnings and give prospective dual-booters full information about loading Grub in their Windows MBR.

Should the new or first-time user decide to remove Ubuntu and Grub, he/she can end up without a working PC.

Should fixmbr fail, as indeed it can, they can end up having to re-install Windows, which is a major P.I.T.A. and potentially disastrous in terms of data loss.

I got caught out this way, fortunately I am a fastidious backer-upper, so it was just a nuisance. Others may not be so lucky.

As for Grub, a quick scan of the forums will easily reveal the true story of it's reliability...

(As I know you are well aware of Herman)

So again I urge the Ubuntu staff to look at things from  the perspective of someone coming to Ubuntu full of hope ad expectation, but with little or no knowledge of the implications of over-writing their Windows MBR with Grub.

It's easy once you know how, but the innocent newccomer doesn't know what he doesn't know. It's up to the install software to tell/warn him fully. With detailed explanations.

I haven't stored anything important on my Windows drive for years. Everything that I save goes on a seperate drive that is used for that purpose only.I very strongly recommend getting an extra drive (even if it's just a USB 2.0 external) to save anything important on. saving anything important on the drive that houses you OS is just asking for trouble.

---

### Post by gn2 on 2006-10-21
> **bullinchinashop said:**
> I haven't stored anything important on my Windows drive for years. Everything that I save goes on a seperate drive that is used for that purpose only.I very strongly recommend getting an extra drive (even if it's just a USB 2.0 external) to save anything important on. saving anything important on the drive that houses you OS is just asking for trouble.

I wholeheartedly agree. But not everyone is as savvy as us......

---

### Post by Acollective on 2006-10-21
truly lucky ... fixMBR did not "Fix" the MBR when I had my little disaster. However I just finished setting using bulldogs method and all is well. :)

---

### Post by Herman on 2006-10-21
> when I tried to boot into ZenwalkI still got the aLinux boot manager Well of course you would, Zenwalk is a Linux distro, naturally it has a Linux bootloader. I have Zenwalk here here too, but it isn't installed at the moment, I have tried it out though. :rolleyes:

>  I wish there was some way to write the boot loader to a bootable cd-r (I got rid of my floppy ages ago & I'd have to get rid of a hard drive to put in another one). Most disto's give you the option to write LILO/Grub to a floppy but do they realize that there are more & more computers being shipped w/out floppies? I'm pretty sure my sister's Dell came w/out a floppy drive... 
Hello bullinchinashop
 I wrote a how-to about how to make your own personal Grub CD , would you like to try that one?  :D
                                      How to make a Grub CD-RW....................................................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD")

> I haven't stored anything important on my Windows drive for years. Everything that I save goes on a seperate drive that is used for that purpose only.I very strongly recommend getting an extra drive (even if it's just a USB 2.0 external) to save anything important on. saving anything important on the drive that houses you OS is just asking for trouble. I agree with you on that one, I use a seperate USB drive too. 8)

Have fun and all the best, Regards, Herman :D

---

### Post by bulldog on 2006-10-21
There are to many people who have windows **and** they're data on the same large C:\ drive.

It should be done by the manufacturers that there should be a separate data partition.

Now when things go bad they think most often to have no other option then to reformat and reinstall windows.

Mostly lose their data with windows and having no idea it's not necessary to do it that way.

Never have done so,always made several partitions on my drive and restoring important data on a USB drive as well.

But you can write a book about it but most people find out the bad way.

---

### Post by Herman on 2006-10-21
> I would argue that Ubuntu should have explicit warnings and give prospective dual-booters full information about loading Grub in their Windows MBR. I don't think Linux users generally like too many warning signs. Most people should know when they are doing something they aren't sure of, and try to find out more about it somehow first.  It's just common sense. ;)
A hard disk's MBR does not belong to Windows, it is not part of any operating system's partition. Windows has a boot sector of its own though. Some people have yet to learn the difference. ](*,)
>  Should the new or first-time user decide to remove Ubuntu and Grub, he/she can end up without a working PC.
 Yes, but only for a few minutes. It's easy to replace the IPL code in the MBR with code for another bootloader, or else boot with a bootloader on a CD or a floppy disk so you can access the information and/or software from the internet if necessary to help you do that, or get help if you need it.
>  Should fixmbr fail, as indeed it can, they can end up having to re-install Windows, which is a major P.I.T.A. and potentially disastrous in terms of data loss. Well, for one thing, you can rescue all your data with Linux, that's one of the things Linux is famous for. I can teach you how to do that if you like.  Secondly, you wouldn't need to re-install Windows at all, only the 446 byte 'IPL' for the bootlaoder. There are several other ways of  reinstalling the IPL for the Windows bootloader in the MBR besides fixmbr, if that doesn't work. Several are listed in my [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm"). In my website on installing Ubuntu, the 'Uninstall Page is the first page listed in the [home page's index]("http://users.bigpond.net.au/hermanzone/"), so people will hopefully read how to do that first, before they begin thier installations. So they should be aware of what they are doing.  However, my site is not an official site, I'm just an ordinary user of the software like yourself, hoping to be helpful. Not everyone might know of and read my website. There are links for it in many places though, if anyone is looking for help, and many Ubuntu forum members will refer you to it if you ask.   :D
>  I got caught out this way, fortunately I am a fastidious backer-upper, so it was just a nuisance. Others may not be so lucky.
 Surely nowadays everyone is aware that they should back up their data at all times, and particularly before making major changes to thier partitions and drives.  Come on now...  Please!   :rolleyes:
>  As for Grub, a quick scan of the forums will easily reveal the true story of it's reliability...
(As I know you are well aware of Herman) Yes, no-one has ever attempted to hide the fact that there is some hardware that Ubuntu has problems installing Grub correctly in. The posts for help are all here in Ubuntu Web Forums in full public view, for all to see. So  people can easily see there is a small risk that things might need a little manual intervention occasionally, and usualy, they can also see how someone else solved the same problem already. That's what these forums are here for. I am sure that Windows-only computers have problems too, Windows tech support employs quite a large number of staff to try to deal with them all, and they are not always successful in solving every problem either. 
Tell me something. How many people would you estimate to be installing Ubuntu succesfully every day, compared with the number of people who type in for help with a grub problem? And of those, how many would you estimate cannot be easily solved. Now, I admit, there are a few that I don't know how to easily solve, but I think hundeds of people would be installing each day. just look at the forum statistics. At the time of typing this,                  Members: 181,794,                     Active Members: 135,820. Ubuntu first came out with 'Warty 4.10', which means it was released in October 2004, (about two years ago). So if we divide 180000 members by (2*365) days, that indicates that an average of around 250 people have joined Ubuntu Web Forums per day. Now, that's not a very good indicator of the number of people installing Ubuntu per day, but it's the best I can do for now. This is only an average, and the number of installs will have began with only a few when 'Warty' first came out, and is increasing exponentially, as more and more people find out how good Ubuntu is, and tell their freinds. So anyway, even though this is a rough way of guessing, I think that a lot of people are probably installing Ubuntu every day, and not very many have any problems at all. :D
And the ones who do, usually get help and are easily able to solve their problem, once they have the right help.

Did you ever ask for help with your Grub problem? I have searched and I cannot find any post by you asking for help. :confused:
> and getting the space used by Ubuntu back isn't always easy. gparted sure isn't Partition Magic, and most PC owners don't have a Windows disc, just recovery software.       It works perfectly well for most people. I think you have a tendency to exaggerate quite a lot, and rather often. 
I recommend [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php"), as the version of GParted on the Dapper Live CD is way out of date now.  A lot of improvements have been made in GParted in the last six months, and anyway, it works better on it's own LiveCD. GParted is excellent disk partitioning software, I use it all the time.
My Acer computers all came with 'Recovery disks', which I agree, do not offer any options, they just erase Ubuntu and re-install Windows to factory shipped settings. Most people have Windows 'Install' CDs, which I am led to believe are more functional.
I already explained how to restore the MBR with a Windows 98SE boot disk, if you have the 'Recovery' CD, like I do. Besides, there are lots of other ways as well, all on the [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm"). If one method won't work there are plenty of others to try. :D

That's all for now, you should read my website if you want to learn more, [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
Regards, Herman :D

---

### Post by Libertine on 2006-10-21
How do I disable GRUB?

---

### Post by ghostofcain on 2006-10-21
Wish, i'd spotted this thread before my recent HD hiccup, currently have Xp on one IDE drive, for the wife/Kids/Games and Ubunutu on a second. Installed Ubuntu after windows and Grub to Ubuntu HD, then set XP as master and Ubuntu as slave via jumpers, and then swapped them about in BIOS ie slave - master, master- slave. So in normal operation boots from Ubuntu with Grub offering Windows, if ubunutu disk fails will boot direct to windows. Convuluted solution I admit but less fiddling for wife and kids should HD fail, again

---

### Post by gn2 on 2006-10-21
> **Acollective said:**
> truly lucky ... fixMBR did not "Fix" the MBR when I had my little disaster. However I just finished setting using bulldogs method and all is well. :)

Just keep that MBR nice and clean, say no to a Grubby mess!

---

### Post by kondor on 2006-10-22
> **bulldog said:**
> There are to many people who have windows **and** they're data on the same large C:\ drive.

It should be done by the manufacturers that there should be a separate data partition.

Now when things go bad they think most often to have no other option then to reformat and reinstall windows.

Mostly lose their data with windows and having no idea it's not necessary to do it that way.

Never have done so,always made several partitions on my drive and restoring important data on a USB drive as well.

But you can write a book about it but most people find out the bad way.

I have used BerryLinux LiveCD to fix WinXX when a BIOS update hiccuped. I like BerryLinux Live. Also, data is seldom "lost". Inability to access data is not the equivalent "lost". That's how many people learn: broken systems and desperation. Also, it takes many overwrites to truly get rid of data on a HD. If the data" is put in a separate partition, no access means no access.

A LiveCD of a Linux flavor can read WinXX files. PC manufacturers are not responsible for educating purchasers concerning the supposed inadequacies of the WinXX file system. Most manufacturers include a photo sheet showing folk how to press the "on" button. Most folk that use PCs do not care what makes them "work". Certainly that is the business model. Time is money.

PCs are not loaded with WinXX simply because it is a monopoly OS. It is because WinXX is designed "user friendly". To require the Ubuntu developers to hold everyone's hand during their Ubuntu "experience" is a bit excessive. Why should they waste their time making Ubuntu Windows proof? And, what will you do when your USB/eSATA/Firewire external drive quits? Certainly external HD life is no greater than those in the box. Ubuntu does warn those who use the distro: NO WARRANTY, express or implied.

Ubuntu currently is a superb Linux distro, amazing given the timeframe from start to now. It is stable, even the new final RC, and comes in so many flavors that it boggles the mind. And, kudos to the Debian team that provided(s) the groundwork. IMHO, Ubuntu does not need seatbelts and airbags or emissions controls. If someone desires to install Ubuntu and doesn't know about bootloaders, they can search this forum or the Wiki and find enough information to melt their brain. Also, in many areas where Ubuntu was designed to be distributed, there is no problem concerning dual boots, and triple boots and installing a new distro each day. Much of that world cannot afford toys.

I personally do not think the Ubuntu Team should concern themselves with those who are installing Linux as a toy, sticking a toe in the Linux "pool" whilst remaining essentially submerged in the Windows pool, especially those who complain about WinXX, yet keep it on their machines.

Course, that's just me. Ubuntu is not Slack or SUSE either. In fact, I would recommend everyone interested in Linux play with Slack until they have learned something. As for SUSE, 10.1 was a bomb of greater magnitude than the recent PRNK "pop". So much for "corporate" distros.


Ubuntu is fine! 

 registered linux user 266482

---

### Post by gn2 on 2006-10-22
> **kondor said:**
> 

 And, what will you do when your USB/eSATA/Firewire external drive quits? Certainly external HD life is no greater than those in the box.

Ubuntu currently is a superb Linux distro, 

 If someone desires to install Ubuntu and doesn't know about bootloaders, they can search this forum or the Wiki and find enough information to melt their brain. 



Firstly, I would point out that an external drive if used as a backup spends 99% of it's time switched off. So will last significantly longer than anything fitted inside a PC case.

Ubuntu is an average Distro, others are more user friendly, have many more useful features and are more advanced.

As for knowledge of bootloaders, most people coming to Ubuntu won't even know the term, let alone know to read up on the implications of wiping out their Windows native bootloader.
You don't know what you don't know.....

Of course you are entitled to your opinion.

---

### Post by la3875 on 2006-10-25
I did exactly this about a month ago with the same success except I made Ubuntu disk the master and XP the slave and stayed out of the bios altogether. Works beautifully!!!

---

### Post by badguyanil on 2006-10-29
> **gn2 said:**
> Generally in Ubuntu the usual way to install a dual-boot system involves overwriting the Master Boot Record of the Windows hard drive.

However,
f you are dual-booting with TWO hard drives it is not necessary to write Grub over the MBR if you can access a "Boot Device Selection Menu" by pressing F8
(or whatever key depending on BIOS)
You can thus keep both installations entirely separate.
To do it this way:
Disconnect the Windows drive and install Ubuntu and Grub on the second drive. Reconnect first drive after installing Ubuntu.
Windows on master, Ubuntu & Grub on slave if using two IDE drives.
(This method will also work on SATA drives, or a mix of SATA & IDE)
Press F8 (or whatever key depending on BIOS version) at boot time to bring up the Boot Device Selection Menu.
Choose OS by selecting which drive to boot from.
Select desired default OS by re-arranging boot order in BIOS.
Only need to press F8 to select non-default OS.

Well followed the above given method
1.Disconnect the Windoes Drive.
2.Connect the 2nd drive as master. Install Ubuntu + GRUB.
3.Reconnect Windows as master and ubuntu as slave.

For Windows i have 2 OS installed XP and 98. So when i press F8 duirng booting i get tthe option of only Win OS's. I cant even see the other slave HDD. Although BIOSdoes recognise it during boot! (ofcourse it will). Please help.

---

### Post by gn2 on 2006-10-29
> **badguyanil said:**
> Well followed the above given method
1.Disconnect the Windoes Drive.
2.Connect the 2nd drive as master. Install Ubuntu + GRUB.
3.Reconnect Windows as master and ubuntu as slave.

For Windows i have 2 OS installed XP and 98. So when i press F8 duirng booting i get tthe option of only Win OS's. I cant even see the other slave HDD. Although BIOSdoes recognise it during boot! (ofcourse it will). Please help.

When installing Ubuntu you should perhaps have connected it's hard drive as slave, Windows on the master connector, but the power disconnected.

When you press F8 do you get a list of devices?

If so use the up/down arrows to select the Ubuntu hard drive, when it's highlighted press enter and it will boot.

---

### Post by badguyanil on 2006-10-30
hmm but i have installed win XP and Win 98 on one drive...with ubuntu in the second. Making ubuntu as master! was just wondering if the above will work with 6.10 release too!

---

### Post by gn2 on 2006-10-30
> **badguyanil said:**
> hmm but i have installed win XP and Win 98 on one drive...with ubuntu in the second. Making ubuntu as master! was just wondering if the above will work with 6.10 release too!

Don't understand why you would want to keep W98 now that it's unsupported.
Surely any old programs you have will run in XP using compatibility mode?

---

### Post by badguyanil on 2006-10-30
> **gn2 said:**
> Don't understand why you would want to keep W98 now that it's unsupported.
Surely any old programs you have will run in XP using compatibility mode?

ya very right dont need 98 anymore! but last i installed my OS's way back! XP wasnt there! had just 98! Installed XP seperately later! And now planning to shift to linux. I could have over written 98 alright but wanted to test XP. Much like Ubuntu! Also 98 is mere 500 mb with only OS! so never thought of removing it!

---

### Post by badguyanil on 2006-10-30
Well i did as is given in the thread ie make the following entires in /boot/grub
title Windows
map (hd0,0)(hd1,0)
map (hd1,0)(hd0,0)
rootnoverify (hd1,0)
make active
chainloader +1

and also commented the hiddenmenu option.

Note i have ubuntu 6.10 as Master and Windows (XP + 98 in dual boot) as slave. 

I do get the menu while booting up, but when i select windows i get a "Error : Unrecognised Device String" message. please help coz it is getting tedious to change the setting again and again to switch env's as i have not been able to figure out how to access net from ubuntu! Please reply asap.

---

### Post by gn2 on 2006-10-30
> **badguyanil said:**
> Well i did as is given in the thread ie make the following entires in /boot/grub
title Windows
map (hd0,0)(hd1,0)
map (hd1,0)(hd0,0)
rootnoverify (hd1,0)
make active
chainloader +1

and also commented the hiddenmenu option.

Note i have ubuntu 6.10 as Master and Windows (XP + 98 in dual boot) as slave. 

I do get the menu while booting up, but when i select windows i get a "Error : Unrecognised Device String" message. please help coz it is getting tedious to change the setting again and again to switch env's as i have not been able to figure out how to access net from ubuntu! Please reply asap.


Guess you've gone the Grub edit route...

My personal preference is Windows on master with the MBR intact, and Ubuntu & Grub on Slave. Set Slave before Master in BIOS boot order and Ubuntu is default OS. Of course you need to be able to access device selection menu by pressing F8 (or whatever key depending on BIOS version) to switch OS.

You may need to run fixmbr with Windows drive re-instated as master.

Then re-install Grub to Slave drive.

Remember to disconnect the other drive when performing these actions.

---

### Post by badguyanil on 2006-10-30
> Originally Posted by badguyanil  
Well i did as is given in the thread ie make the following entires in /boot/grub
title Windows
map (hd0,0)(hd1,0)
map (hd1,0)(hd0,0)
rootnoverify (hd1,0)
make active
chainloader +1

and also commented the hiddenmenu option.

Note i have ubuntu 6.10 as Master and Windows (XP + 98 in dual boot) as slave. 

I do get the menu while booting up, but when i select windows i get a "Error : Unrecognised Device String" message. please help coz it is getting tedious to change the setting again and again to switch env's as i have not been able to figure out how to access net from ubuntu! Please reply asap.

> Guess you've gone the Grub edit route...


Hmm but i cant set BIOS boot order! it will read the Primary Master by default follwed by Primary Slave and so on for Secondary....Or can i set it!never needed to check this! will check it! but i prefer the grub edit mode! Trying to migrate out of windows u see! So the more i learn to use linux the better. Any suggestions on Groub edit!

---

### Post by confused57 on 2006-10-30
> **badguyanil said:**
> Hmm but i cant set BIOS boot order! it will read the Primary Master by default follwed by Primary Slave and so on for Secondary....Or can i set it!never needed to check this! will check it! but i prefer the grub edit mode! Trying to migrate out of windows u see! So the more i learn to use linux the better. Any suggestions on Groub edit!
Using bios to dualboot is a viable option for some users, but here's how I have my system set up:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by Handssolow on 2006-11-06
> **Cubbybearks said:**
> I was able to create a boot disk for WindowsXP on a floppy and edit the boot.ini settings to include Ubuntu that way when I want to boot from Ubuntu I insert the disk to and when I dont I leave the disk out of the drive works for me since I share a computer with someone else and we each have our own hard drives

I like the sound of this method particularly as I'm wanted to set my wife's PC for dual boot and this seems like an easy system for her to use. It keeps both HDs clean.
I assume that the second OS's data would be invisible or inaccessable.

Yes, this is a request for information about windows but can I have some more information about how to set this up, which hd is master and what needs to be added to the floppy's windows boot.ini file?

---

### Post by gn2 on 2006-11-07
> **Handssolow said:**
> I like the sound of this method particularly as I'm wanted to set my wife's PC for dual boot and this seems like an easy system for her to use. It keeps both HDs clean.
I assume that the second OS's data would be invisible or inaccessable.

Yes, this is a request for information about windows but can I have some more information about how to set this up, which hd is master and what needs to be added to the floppy's windows boot.ini file?

Read access to each other's drives can be configured later, writing can be more problematic, with NTFS and ext2/3 not getting on very well.

Windows on master Linux on slave if you have a "Boot Device Selection menu"

No tweaking of the boot.ini is required whatsoever.

---

### Post by Handssolow on 2006-11-08
It's working. I've put Ubuntu on a Sata master, Xp on an IDE slave with a boot into Grub to select as described earlier. Initially when I first modified Grub it didn't work, I thought it was the A7V880 mobo with the mix of hds. I re-read the posts and then moved the windows bit to the end in Grub, allowed unhiddden and 10 seconds but I didn't add savedefault to the windows lines.

---

### Post by JW9 on 2006-11-17
Here is what I ran into booting on two disks.  After successfully installing XP and Ubuntu on separate disks, (XP should be first), the ubuntu grub gives you a choice of which OS to open.  This is fine........untill you want to or have to replace ubuntu.  When you take it out the bios can no longer find Windows.  The bios is still controlled by Linux. The only safe way to use them that I have found is to change the boot in the bios.  Surely someone can come up with a safe and easier way to boot either without having to change the bios or use the grub.

---

### Post by MrBeard on 2006-11-18
Hi all,

 First post and already i have come with questions...

 I'm planning on puttin ubuntu 6.06 onto the drive from my old machine and (assuming I can get the bits) poke it into the case of my new machine as a second drive.

 Can I do the annaconda solution with Win M.E.? (Please stop laughing at the back). Eventually I'll get round to putting XP onto the other bit (probably when MS stop support for that too.)

 If not I'll try the whole thing with using the bios which may work best anyway as then Mrs Pete will be able to just switch it on and use it and I won't have to set up a linux user for her...

Thanks,
Pete.

---

### Post by gn2 on 2006-11-18
> **MrBeard said:**
> Hi all,

 First post and already i have come with questions...

 I'm planning on puttin ubuntu 6.06 onto the drive from my old machine and (assuming I can get the bits) poke it into the case of my new machine as a second drive.

 Can I do the annaconda solution with Win M.E.? (Please stop laughing at the back). Eventually I'll get round to putting XP onto the other bit (probably when MS stop support for that too.)

 If not I'll try the whole thing with using the bios which may work best anyway as then Mrs Pete will be able to just switch it on and use it and I won't have to set up a linux user for her...

Thanks,
Pete.

I would recommend Windows 2000 Professional rather than XP Home.

Can be had on eBay cheap and doesn't suffer from product activation.

Better yet, explain to Mrs Pete that you will save a fortune on software by going Linux-only, and you will be able to take her for a nice meal out with the savings? \\:D/ 

Recommend either the Tolbooth or Carron restaurants in Stonehaven.

---

### Post by Village on 2006-11-20
After lots of headaches, I've been able re-install windows having backed up what I needed. 

I have 3 HDD's two are for Windows, although one has not been installed for Windows yet and the other will be for Ubuntu.

I want Windows to be the default. Currently Windows is the Master (I think).

My question is annoyingly strait forward. What's the easiest way of doing this?

Thanks in advance.

---

### Post by gn2 on 2006-11-20
> **Village said:**
> After lots of headaches, I've been able re-install windows having backed up what I needed. 

I have 3 HDD's two are for Windows, although one has not been installed for Windows yet and the other will be for Ubuntu.

I want Windows to be the default. Currently Windows is the Master (I think).

My question is annoyingly strait forward. What's the easiest way of doing this?

Thanks in advance.

Depends if they're all IDE, SATA or a mix.

And whether you can access a "Boot device selection menu" at boot time.

If you've already got Windows loaded, unplug that drive's power and connect the drive you wish Ubuntu installed on to the slave connector, and install Ubuntu and Grub.

After you have got both installed and re-connected you can put the desired default OS's drive first in the BIOS boot list, and switch to the other OS by pressing F8 (or whatever key depending on make/model)and selecting the desired drive from the menu.

If you format drive 3 as FAT32 you can safely read/write to it from either OS.

If you can't access a "Boot device selection menu" you will need to do some Grub editing, as per the Anaconda/Bulldog method outlined in post 1 of this thread.

---

### Post by Village on 2006-11-21
There all IDE. Know of any good How-to's?

Thanks
Village

---

### Post by la3875 on 2006-11-21
See this thread [http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902) and the link to hermanzone. It helped me get up and running on two IDE drives with Windows as the slave. As necessary I can boot into either and this set up has kept the peace with the other users in the family.

Good luck and may the Ubuntu be with you...

---

### Post by gn2 on 2006-11-21
> **Village said:**
> There all IDE. Know of any good How-to's?

Thanks
Village

Read post 1 on page 1 of this thread.

Which I started as a "How To" for dual-booting avoiding overwriting the Windows native bootloader with Grub.

---

### Post by j3cakes on 2006-11-24
This method worked beautifully for me. I was a bit apprehensive putting ubuntu anywhere near my main PC - mostly because there are a number of posts on this forum mentioning having to reformat drives once it's all gone horribly wrong - but it's all good right now.

There are other.. issues.. but they're not relevant to this thread and I'm sure there's a solution here somewhere.

---

### Post by MrBeard on 2006-11-25
> **gn2 said:**
> I would recommend Windows 2000 Professional rather than XP Home.

Can be had on eBay cheap and doesn't suffer from product activation.

Better yet, explain to Mrs Pete that you will save a fortune on software by going Linux-only, and you will be able to take her for a nice meal out with the savings? \\:D/ 

Recommend either the Tolbooth or Carron restaurants in Stonehaven.


I like this plan...

Would've been looking for XP Pro in any case (use it at work don't like the fact that XP Home won't let me do so much, ME is a real pig.)

---

### Post by veganrailpunk on 2006-11-26
Help!

I have set up with Ubuntu 6.10 on the master (with a ext3 storage partition as well) and Windows XP on the slave. They are boh IDE drives with the end connector in the XP/slave and the middle connector in the Ubuntu/master. Both installations were done with the other drive disconnected. I have edited grub like bulldog said but when i choose XP from GRUB it says:

```
Error 21: Selected disk does not exist
```

But it does! I have mounted the Windows drive in Ubuntu & I can boot windows with my Ubuntu drive disconnected.

In GRUB menu.lst I have put:
```
title Windows XP
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1
```

and I also tried:
```
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

which gave the same error.

Is it possible that I just have my drive numbers mixed up? And how would I find what they are. sudo fdisk -l gives:

```
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3264    26218048+  83  Linux
/dev/hda2           24182       24321     1124550    5  Extended
/dev/hda3            3265       24181   168015802+  83  Linux
/dev/hda5           24182       24321     1124518+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        5004    40194598+   7  HPFS/NTFS

```

Can anyone help?

Thanx
Pete
xx

---

### Post by la3875 on 2006-11-27
I'm no expert but do you get the grub countdown when you boot the computer? And what happens when you let the time lapse? Does Windows boot automatically then?:-k

---

### Post by gn2 on 2006-11-27
The far end of the cable is the master connector.

The middle connector is the slave connector.

Jumpers on the drives have to be set to match or both set as cable select.

Things will be easier with Windows on master.

---

### Post by veganrailpunk on 2006-11-27
> **la3875 said:**
> I'm no expert but do you get the grub countdown when you boot the computer? And what happens when you let the time lapse? Does Windows boot automatically then?:-k

If I let the countdown lapse it auto boots Ubuntu.

> **gn2 said:**
> The far end of the cable is the master connector.

The middle connector is the slave connector.

Jumpers on the drives have to be set to match or both set as cable select.

Things will be easier with Windows on master.

OK now this is annoying! Just put the hds to cable select (never understood what that meant til now) with Windows on the master, Ubuntu on the slave. Changed the boot order in BIOS so slave boots first. Turned on the computer. GRUB loads fine. Select Windows... Hooray it loads! Then reboot, try Ubuntu and...

```
BusyBox v.1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
```

humph :( 

typing 'help' gives a long list of command line commands.

any ideas?

thanx :) 
xx

---

### Post by veganrailpunk on 2006-11-27
OK from other threads I think it's failing cos GRUB is pointing to the wrong partition. So in menu.lst I created a new entry for Ubuntu (copied the old one) with:

```
title		Ubuntu, kernel 2.6.17-10-generic (SLAVE)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```

Which is the same as the entry for when it's plugged into the master but with root (hd1,0) instead of (hd0,0).

But, alas, that comes back with:

```
Error 17: Cannot mount selected partion
```

I was sure that was gonna work! What have I done wrong!?!

---

### Post by bulldog on 2006-11-27
> **veganrailpunk said:**
> OK from other threads I think it's failing cos GRUB is pointing to the wrong partition. So in menu.lst I created a new entry for Ubuntu (copied the old one) with:

```
title		Ubuntu, kernel 2.6.17-10-generic (SLAVE)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```

Which is the same as the entry for when it's plugged into the master but with root (hd1,0) instead of (hd0,0).

But, alas, that comes back with:

```
Error 17: Cannot mount selected partion
```

I was sure that was gonna work! What have I done wrong!?!

Think you have to set the root at (hd0,0) instead of (hd1,0)
It's the first disk (hd0) and first partition (hdo,o) pointing to hda1.

Didn't read everything though and have no more time at the moment but will look into it later this evening if this is not gonna work.
Post back if this is not good.

---

### Post by veganrailpunk on 2006-11-27
> **bulldog said:**
> Think you have to set the root at (hd0,0) instead of (hd1,0)
It's the first disk (hd0) and first partition (hdo,o) pointing to hda1.

Didn't read everything though and have no more time at the moment but will look into it later this evening if this is not gonna work.
Post back if this is not good.

Nope doesn't work, I have Ubuntu on the slave so wouldn't that be (hd1,0)? 

I tried having Windows on the slave with your map bits but it wouldn't have it although that entry works when it is plugged in the master (I set slave to boot in bios so I get GRUB)

When Ubuntu is plugged to the master, root (hd0,0) works fine, but as I can't get windows to work on the slave I need Ubuntu on the slave. Is Ubuntu not happy on the slave? Not interchangeable? I am new to this...

Thanx
xx

---

### Post by bulldog on 2006-11-27
Set ubuntu and GRUB as master on your mobo.
Then we take a look at your GRUB to get windows started.

If Ubuntu and GRUB are master hdd you can boot ubuntu but not windows.
This should be not to difficult to correct it.

---

### Post by veganrailpunk on 2006-11-27
> **bulldog said:**
> Set ubuntu and GRUB as master on your mobo.
Then we take a look at your GRUB to get windows started.

If Ubuntu and GRUB are master hdd you can boot ubuntu but not windows.
This should be not to difficult to correct it.

Just put Ubuntu and GRUB back on master and... it worked!! I think I had my BIOS set up wrong and while I was busy playing with it to set Windows as the master I fixed it. Silly me. Thanx for everyone's help!

I definitely think bulldogs GRUB method is the way forward. Quality.

Love to everyone
xx

---

### Post by MrBeard on 2006-11-27
Am I correct in thinking that in the menu.lst reference to hd(0,0) refers to the root partition of the master disk and hd(1,0) the root partition of the slave disk?

Just want to make sure before I start messing about with grub (whic I think I will have to do this heap of junk I'm using doesn't seem to want me to get into the bios to choose where I'm booting from). 

Also can I edit this with a text editor (vi for example)?

---

### Post by veganrailpunk on 2006-11-27
> **MrBeard said:**
> Am I correct in thinking that in the menu.lst reference to hd(0,0) refers to the root partition of the master disk and hd(1,0) the root partition of the slave disk?

Just want to make sure before I start messing about with grub (whic I think I will have to do this heap of junk I'm using doesn't seem to want me to get into the bios to choose where I'm booting from). 

Also can I edit this with a text editor (vi for example)?

yeah hd0,0 is first partition on the master etc

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```

that'll create a backup then you can edit it in gedit

for full instructions see 1st post in this thread [http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

pete
xx

---

### Post by Sailfish on 2006-11-29
I have a system with 3 SATA drives.  Separately on each drive I installed WinXP, Vista, Ubuntu 6.1.  Each OS (except Ubuntu) beautifully when selected in the BIOS.  Ubuntu boots beautifully when the other drives are disconnected. I don't want a boot loader to manage startup.  I don't want Acronis, no Grub and no Lilo.  I do know that I have Grub installed though....  When this system boots you just hit F11 and it lists the drives.  Then toggle and enter.  Grub somehow wants to reach out...  How do I fix/stop this???

---

### Post by gn2 on 2006-11-29
> **Sailfish said:**
> I have a system with 3 SATA drives.  Separately on each drive I installed WinXP, Vista, Ubuntu 6.1.  Each OS (except Ubuntu) beautifully when selected in the BIOS.  Ubuntu boots beautifully when the other drives are disconnected. I don't want a boot loader to manage startup.  I don't want Acronis, no Grub and no Lilo.  I do know that I have Grub installed though....  When this system boots you just hit F11 and it lists the drives.  Then toggle and enter.  Grub somehow wants to reach out...  How do I fix/stop this???

Did you disconnect the other drives before installing Ubuntu?

---

### Post by j3cakes on 2006-11-29
I thought grub was the loader for ubuntu so you couldn't stop it from running. You can disable the grub boot menu by removing any '#' before the 'hidden' keyword in the /boot/grub/menu.lst (as above) but it shouldn't run if you've not selected ubuntu.

My main PC has two SATA drives and this is how I do it too; F12 (on my machine) then pick a drive to boot from.

---

### Post by gn2 on 2006-11-29
> **j3cakes said:**
> I thought grub was the loader for ubuntu so you couldn't stop it from running. 

It is the default loader for Ubuntu. Other options are available.

> **j3cakes said:**
> You can disable the grub boot menu by removing any '#' before the 'hidden' keyword in the /boot/grub/menu.lst (as above) but it shouldn't run if you've not selected ubuntu.

If it does run under these circumstances it indicates that Grub has been installed on the selected drive.


> **j3cakes said:**
> My main PC has two SATA drives and this is how I do it too; F12 (on my machine) then pick a drive to boot from.

This is the best way I know of protecting your Windows installation.
If Grub is on the MBR of the Windows disc, and for whatever reason Grub needs to be updated/edited, Windows may not boot.

Windows has enough problems to contend with without adding Grub to the mix.........:)

---

### Post by Sailfish on 2006-11-29
> **gn2 said:**
> Did you disconnect the other drives before installing Ubuntu?

Thank you for helping gn2!

Yes.  I just did a reinstall with just the Ubuntu Drive attached.  I booted once to be sure that the system would boot to Ubuntu and it did.  Then I reconnected the other two drives and booted... It proceeds to the Ubuntu logo and progress bar before failing and saying - .bin.sh: can't access tty; job control turned off

(initramfs)

This is the live CD that offers the installation option once up. I installed with the "erase entire disk" option and Grub to(hd0).  Partition #1  (0,1,0) (sda) as ext3
Partition #5  (0,1,0) (sda) as swap

---

### Post by bulldog on 2006-11-29
> **Sailfish said:**
> Thank you for helping gn2!

Yes.  I just did a reinstall with just the Ubuntu Drive attached.  I booted once to be sure that the system would boot to Ubuntu and it did.  Then I reconnected the other two drives and booted... It proceeds to the Ubuntu logo and progress bar before failing and saying - .bin.sh: can't access tty; job control turned off

(initramfs)

This is the live CD that offers the installation option once up. I installed with the "erase entire disk" option and Grub to(hd0).  Partition #1  (0,1,0) (sda) as ext3
Partition #5  (0,1,0) (sda) as swap

You use the wrong options for GRUB.
If it's installed on hd0 partition 1 use (hd0,1) not (hd0,1,0) GRUB won't understand this :D

And it beats me why you are disconnecting the other drives.
If you want to use one of them in Ubuntu,you have to mount them or edit fstab.
If you know how your disks are recognized in Ubuntu [sudo fdisk -l] it is easy to set it up with all your drives connected.

But what do I know.......

---

### Post by Sailfish on 2006-11-29
> **Sailfish said:**
> Thank you for helping gn2!

Yes.  I just did a reinstall with just the Ubuntu Drive attached.  I booted once to be sure that the system would boot to Ubuntu and it did.  Then I reconnected the other two drives and booted... It proceeds to the Ubuntu logo and progress bar before failing and saying - .bin.sh: can't access tty; job control turned off

(initramfs)

This is the live CD that offers the installation option once up. I installed with the "erase entire disk" option and Grub to(hd0).  Partition #1  (0,1,0) (sda) as ext3
Partition #5  (0,1,0) (sda) as swap

> **bulldog said:**
> You use the wrong options for GRUB.
If it's installed on hd0 partition 1 use (hd0,1) not (hd0,1,0) GRUB won't understand this :D

And it beats me why you are disconnecting the other drives.
If you want to use one of them in Ubuntu,you have to mount them or edit fstab.
If you know how your disks are recognized in Ubuntu [sudo fdisk -l] it is easy to set it up with all your drives connected.

But what do I know.......

Just to make sure this is all straight...  When installing Ubunto it indicated that it was installing Grub to (hd0).  I don't actually know where it ultimately ended up.  At the end of the install it provided the other information about Partions 1 & 5.  If I do a reinstall and tell it to put Grub on (hd0,1), then that will allow me to boot the OS from the BIOS?

---

### Post by bulldog on 2006-11-30
Installing GRUB on (hd0,1) is not a good idea.
That would be in the first partition of hd0 and I don't think you want that.

You have to understand GRUB counts your disks starting with zero.
So your first disk is (hd0) your second is (hd1) and so on.
The partitions is the number behind the (,) so your fifth partition on your second disk is (hd1,4).

The best thing to do is install GRUB on the disk where Ubuntu is installed and install windows on a separate hard disk.
Now make the Ubuntu disk the master boot device and the windows disk slave.
You will see a GRUB menu and you can choose between windows and Ubuntu.

Only thing is,windows will not boot in this configuration,you have to do a little altering in your menu.lst

You have to map your drives,because windows like to think it's on the first boot device.
So map them as you can see in this example.
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1
```
Now windows will boot from the slave drive.
If you have to reinstall Ubuntu or windows,you won't have to bother about the other OS because they are on separate disks,and if GRUB might fail,you can boot windows by choosing this disk as boot device in your BIOS.

Hope this clears something for you.

Don't do a reinstall because GRUB isn't working or you can't find it.
First try to boot from both disks to see if GRUB is installed on the other disk,you can find an option to do so in your BIOS.
If GRUB is on the windows disk,pop in the windows install cd,and go through till you get three options,1]install windows 2]repair a windows install 3]exit,choose to repair a windows install.
Now you're taken to windows recovery console and after typing your admin password,you can give the command 'fixmbr' and/or 'fixboot'.
Now your windows boot loader should be reinstalled.

Now find out which disk is hd0 and hd1 with sudo fdisk -l.
Now boot into the live Ubuntu cd and when you're at the desktop open a terminal and type the following commands,
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Finally exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.
Remember to make the last step,setup (hd0) for the disk where you want GRUB installed,so if this is (hd1) it would be setup (hd1) instead of (hd0).

If you have more questions about this,let me know,I will try to answer them if I can.

---

### Post by Sailfish on 2006-11-30
Thank you Bulldog for taking the time to help me with this.  I truly appreciate what you are providing.  In the true Borg spirit, I think that I will go with the flow on Grub per your instructions and see if I don't just learn a little bit about what is happening.  It will at the least make my questions more sound.

Possibly my brain is tracking in a completely different universe here and I just don't get it.... Or I am explaining it so poorly that it is going nowhere. I will try again:

I put Windows on a drive. When I start the system I get Windows. Now I put OSx86 on a different drive and add it to the system. If I prioritize Windows in the BIOS, I get Windows. If I prioritize OSX, I get OSX. Now I put Ubuntu on a third drive and add it to the system. If I prioritize Ubuntu in the BIOS and boot, I do not get Ubuntu. ( I get /bin/sh: can't access tty ; job control turned off ) If I unplug everything but Ubuntu, I get Ubuntu. Why is it different? That is the big question.

My Motherboard, upon startup, says, "Press F11 for Boot Options." When I do that, I get a list of my drives. Then I just arrow to the one I want to boot and hit enter. It is completely independent of any operating systems attached to the system.

I would be thrilled to edit menu.lst or fstab to fix this... I just don't know how to do it.

If this needs to be explained to me in another fashion please feel free to educate me. I am very eager to understand

---

### Post by bulldog on 2006-11-30
The question in this is where's GRUB installed and how is it configured.
If you disconnect all the disks exept Ubuntu it will boot,no problem,but if all disks are connected,it won't boot.

This in fact is that GRUB is counting your hdd's and comes with the wrong hdd for Ubuntu so it can't boot.
You have to edit menu.lst so it points to the right hdd for ubuntu and probably your fstab too.

That's why I advice to leave all the disks connected so they are properly assigned in GRUB and menu.lst and fstab as well.

Try sudo fdisk -l to find out how your disk are ordered and alter menu.lst and fstab to correct things.

---

### Post by Sailfish on 2006-11-30
> **bulldog said:**
> The question in this is where's GRUB installed and how is it configured.
If you disconnect all the disks exept Ubuntu it will boot,no problem,but if all disks are connected,it won't boot.

This in fact is that GRUB is counting your hdd's and comes with the wrong hdd for Ubuntu so it can't boot.
You have to edit menu.lst so it points to the right hdd for ubuntu and probably your fstab too.

That's why I advice to leave all the disks connected so they are properly assigned in GRUB and menu.lst and fstab as well.

Try sudo fdisk -l to find out how your disk are ordered and alter menu.lst and fstab to correct things.

AH HA! That doesn't mean I have this where I want it, but I understand better.  I went through some of your direction.

Booted into Live CD
In terminal I typed "sudo fdisk -l"
I got this in Reply:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18703   150231816   83  Linux
/dev/sdb2           18704       19457     6056505    5  Extended
/dev/sdb5           18704       19457     6056473+  82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38914   312571192+  af  Unknown
ubuntu@ubuntu:~$ 

Then I typed "sudo grub" > "/boot/grub/stage1"
I received this in reply:

(hd1,0)

Does this help us at all?

---

### Post by Sailfish on 2006-11-30
SUCCESS!!! Many Thanks to bulldog and gn2.  System booting with 4 drives and 4 OS's through Motherboard F11 (BIOS Prioritization).

Will Post the How To Tutorial as soon as I get done walking the dog!

---

### Post by bulldog on 2006-11-30
Post your menu.lst so we can take a look how it's configured.
I suppose it points to (hd0) cause you had just one drive connected.
In your situation your Ubuntu is on sdb which is in GRUB talk (hd1)

So you should examine your GRUB and have a look at fstab to correct these items so it points to (hd1,0)

Windows is on sda = (hd0)
Ubuntu is on  sdb = (hd1)
OSX is on sdc = (hd2)

With this knowledge we can alter GRUB to start windows and Ubuntu,I have no experience with OSX,can't tell about that one.
We also should make the sdb [Ubuntu disk] the master boot device so you always boot with GRUB and choose your OS.
When GRUB should fail,you can always boot the windows disk by making it boot device,so could you do with OSX.

Your windows and OSX disks are not affected by this way of doing things,and it's easier to boot in my view.

---

### Post by Sailfish on 2006-12-02
For those who wish to multi boot operating systems that are on separate drives with the BIOS. Accomplished by selecting an F key during BIOS post to bring up a drive list or by actually entering the BIOS and prioritizing a drive.

1.   I hooked a 500GB SATA drive to my system (alone) and loaded Windows XP
     onto it.
2.   I repeated the process with Osx86 onto a 360GB SATA drive (alone)
3.   Once again with Linux Ubuntu 6.1 onto a 160GB SATA (alone)
4.   All drives were added to the system each to it's specific plug in.
5.   Testing either from a cold boot or restart, each drive was tested by
     prioritizing it in the BIOS.
6.   All booted normally except for Linux.  It gave the error:
    .bin.sh: can't access tty; job control turned off
    (initramfs)
7.   Why did it do this is the grand question...  Why didn't it just behave
     like the other OS's? And how do we fix it?
8.   Reboot the system with the live Ubuntu CD with the complete array of
     drives installed.
9.   Select:  Applications > Accessories > Terminal
10.  In the Terminal Window type:  sudo fdisk -l
11.  I got this:  (note colored text)

Disk /dev/sd[COLOR="Red"]a[/COLOR]: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sd[COLOR="Red"]a[/COLOR]1 * 1 60800 488375968+ 7 HPFS/NTFS

Disk /dev/sd[COLOR="Red"]b[/COLOR]: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sd[COLOR="Red"]b[/COLOR]1 * 1 18703 150231816 83 Linux
/dev/sd[COLOR="Red"]b[/COLOR]2 18704 19457 6056505 5 Extended
/dev/sd[COLOR="Red"]b[/COLOR]5 18704 19457 6056473+ 82 Linux swap / Solaris

Disk /dev/sd[COLOR="Red"]c[/COLOR]: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sd[COLOR="Red"]c[/COLOR]1 * 1 38914 312571192+ af Unknown
ubuntu@ubuntu:~$ 

12. When same function is performed with only the Linux drive in place it
    comes up as:

Device Boot Start End Blocks Id System
/dev/sd[COLOR="Red"]a[/COLOR]1 * 1 18703 150231816 83 Linux
/dev/sd[COLOR="Red"]a[/COLOR]2 18704 19457 6056505 5 Extended
/dev/sd[COLOR="Red"]a[/COLOR]5 18704 19457 6056473+ 82 Linux swap / Solaris

    This is the problem.   It changed.
13. The menu.lst and the fstab files must be edited to reflect the “b”
    which is what it becomes when the drives are all in the array.
14. If you are like me, 4 days ago I had no idea where you would find those
    files.
15. First you need to log in a root or there is no way you will be able to
    edit them.
16. Places > Home Folder > (hit up arrow twice) > double click “boot”
    folder >  double click “grub” folder and there you will find menu.lst
17. Places > Home Folder > (hit up arrow twice) > double click “etc” folder
    >  and there you will find fstab.

18. My Original menu.lst (single drive):

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sd[COLOR="Red"]a[/COLOR]1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sd[COLOR="Red"]a[/COLOR]1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot
### END DEBIAN AUTOMAGIC KERNELS LIST

19.Edited menu.lst 

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sd[COLOR="Red"]b[/COLOR]1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sd[COLOR="Red"]b[/COLOR]1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

20.My Original fstab (stand alone drive):

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sd[COLOR="Red"]a[/COLOR]1
UUID=acf68984-8e11-4132-b926-ccd4c263201b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sd[COLOR="Red"]a[/COLOR]5
UUID=56da790e-550a-4751-9fff-05baa2b53494 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom2   udf,iso9660 user,noauto     0       0

21.Edited menu.lst 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sd[COLOR="Red"]b[/COLOR]1
UUID=acf68984-8e11-4132-b926-ccd4c263201b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sd[COLOR="Red"]b[/COLOR]5
UUID=56da790e-550a-4751-9fff-05baa2b53494 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom2   udf,iso9660 user,noauto     0       0

22.That's it!  Enjoy.

Many Thanks to gn2 and bulldog for making me think!.  It may not be the easiest way to skin the cat but it works.  No GRUB and No Acronis.  Although now you could set Windows to boot as your default drive, install the Acronis bootloader on Windows and Voila..  There ya go.

---

### Post by bulldog on 2006-12-02
Nice, you have it as you want now,it's not that difficult to understand how GRUB works :D 

If you connect just one hdd it's alway recognized as (hd0).
But if you connect more of them,that could change very easily .

Just find out which drive is which with sudo fdisk -l and change the menu.lst and fstab to correct it to the proper disk and you're off to go.

To find GRUB [menu.lst] with terminal commands,```
gksudo gedit /boot/grub/menu.lst
```
To find fstab with the terminal```
gksudo gedit /etc/fstab
```

But I'm glad to be of some assistence to you.:D

---

### Post by casfindad on 2006-12-04
> **gn2 said:**
> 

Always disconnect other OS's drive if re-installing.

This process will also work for adding Windows to an Ubuntu system



Why does the other OS's drive need to be disconnected? I just added a second SATA disk to my system. I would like to install windows on an NTFS partition on this new disk and split the rest between FAT32 (for file sharing) and ext3 (for system backup). Do I need to unplug my existing SATA drive with Kubuntu before installing Windows on the new disk?

---

### Post by gn2 on 2006-12-04
> **casfindad said:**
> Why does the other OS's drive need to be disconnected? 

The quote was relating to re-installing.

If you re-install Ubuntu using the standard CD, it will put Grub in your Windows drive MBR.

As you are installing Windows on a new SATA drive, you may not have todisconnect, however if you do disconnect the Ubuntu drive you will defiinitely not be able to install Windows to the wrong drive by mistake.

Disconnection is a safety precaution.

If your hardware is up to it, I would suggest running a Virtual PC with VMWare or Parallels instead of dual-booting.

---

### Post by willcox on 2006-12-06
Well my friends, can't find solution/succeed in this important thread, and I do expect that someone can help me:
SATA with 2 partitions, the 1st with Ubuntu 6.10, the 2nd as storage (100 Gb each one)
IDE drive with a FAT32 partition (slave).
If a type:
sudo fdisk -l
output:
/dev/sda1               1          65      522081   83  Linux
/dev/sda2              66         326     2096482+  82  Linux swap / Solaris
/dev/sda3             327       13075   102406342+  83  Linux
/dev/sda4           13076       30401   139171095   83  Linux

My question is:  why Ubuntu 6.10 does not recognize my FAT32 partition?
This partition runs pretty good with XP & Fedora Core 5.
/etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=bfa5b0de-ae59-4c0b-822e-3323ac21129e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=66adee43-571d-43b2-a7eb-88da5660a74e /boot           ext3    defaults        0       2
# /dev/sda4
UUID=dd2145af-6b95-441f-ab8b-37f88a4b980a /opt            ext3    defaults        0       2
# /dev/sda2
UUID=67e984fe-4e5e-4225-969a-e4625bf484a6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/etc/mtab:
/dev/sda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
/dev/sda1 /boot ext3 rw 0 0
/dev/sda4 /opt ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

Thanks in advance!

---

### Post by gn2 on 2006-12-07
> **willcox said:**
> 
My question is:  why Ubuntu 6.10 does not recognize my FAT32 partition?


What's on this Fat32 partition on your IDE slave drive?

---

### Post by bulldog on 2006-12-07
You can mount your FAT32 partition with this info I guess.
Don't know why ubuntu didn't do it for you......

[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

### Post by scc4fun on 2006-12-07
I'm a noob myself, but if the FAT32 drive/partition is IDE then then it should be hda1 (assuming it is the first partition on the first/only IDE drive).

---

### Post by willcox on 2006-12-07
Thx!
  I have, you know, mp3's, videos, oOo/word docs, and a lot of personal info stored since redhat 7.1 to fedora core 5.
 I forgot to tell you that there is a jumper that limits the drive to 32 Gb, (80 Gb) and as I have mentioned above, it runs with no problems on XP and FC5.

Mhh! I just want to be able to see and copy the whole FAT32 partition onto my 2nd Ubuntu's partition.
Anyways, I'm still looking for more info.

---

### Post by gn2 on 2006-12-07
Got an external USB hard drive enclosure?

eBay time perhaps......

---

### Post by willcox on 2006-12-07
Yes!  
  I have a 2 Gb USB mem. 
  The FAT32 partition has only ½ Gb (aprox) of free space, and I'm wondering if I'd better write 6 or 7 DVD's, as a extra back-ups.

---

### Post by MrBeard on 2006-12-08
Thanks veganrailpunk.

I'll give this a shot this afternoon (I hope)...

Cheers,
Pete2.

---

### Post by MrBeard on 2006-12-08
Thanks everyone. I've got this working now...

Windows as default so that Mrs B can just go straight there and I can pick and choose...

:)

---

### Post by gn2 on 2006-12-08
> **willcox said:**
> Yes!  
  I have a 2 Gb USB mem. 
  The FAT32 partition has only ½ Gb (aprox) of free space, and I'm wondering if I'd better write 6 or 7 DVD's, as a extra back-ups.

Sorry for not being clearer, I meant an enclosure to put the FAT32 hard drive in, to allow easy transfer of files.

---

### Post by oomingmak on 2006-12-27
> **bullinchinashop said:**
> This is one of the few things about Ubuntu that really ticks me off. Zenwalk Slackware SUSE & Vector let you decide where the boot loader is installed. You can also choose to not install a boot loader or to install it to a floppy.
Ubuntu really should give you the option to control how where and if a boot loader is installed.
I agree **totally** with the above statement, except in my case it didn't just "*tick me off*", it made me f*****g furious.

I went out and bought separate hard drives when I decided that I wanted to try out different OSs. I did this because I absolutely did not want *anything* messing with my Windows drive (which contains absolutely vital data). I wanted each OS to be strictly confined on its own drive.

Most OSs worked just fine. You specify the drive, and the OS installs to *that* drive (and everything else is left well alone). But when I tried Ubuntu, my Windows drive MBR got trashed even though I never gave Ubuntu permisison to go anywhere near it. I didn't even allow anything from my Windows drive to be mounted in Ubuntu (that's how much I do not want my OSs interacting). If I want to share between OSs (highly unlikely) then I will set up a dedicated partition for this purpose.

Having been so explicit with my instructions during Ubuntu's setup, I was furious to find that not only did Ubuntu write to a totally different drive without my permission, but there was not even so much as a comment or notification saying that this was going to happen.

Anyway, Grub was installed to my Windows drive and I could no longer boot into Windows. I have no idea why, but no matter what I did it just would not work. This was exactly the kind of nightmare I was trying to avoid (and is the reason why I went out and bought extra hard drives in the first place). My ADSL modem card was not recognised by Ubuntu (so I had no net access) and therefore I had no way of trying to find a solution. I am a fairly competent computer user (at least as far as Windows goes), but hacking around the MBR in hex or knowing how Grub works is beyond me (I have never used Linux before). So I needed to consult help on how to fix an issue like this. 

It took many stress filled hours (and a visit to a friend in order to use his PC to search the net) to come up with a soution. Even then it wasn't easy to fix, and the whole time I feared that I might lose all my data. I don't see why I should have even have had to go through this ordeal. Every other OS that I tried did not subject me to this.

I have read comments in this thread about users being confused by choices, or Linux users not liking too many warnings, but such arguments just don't cut it with this particular issue. Arbitrarily deciding to overwrite data on a users PC (behind their back without telling them) is the kind of behaviour I expect from Virus writers, not an operating system. I don't care whether Linux users like warnings or not. If you are going to overwrite **MY** data on **MY** computer, then have the decency to tell me so.

Also, if users really don't want choices then why would they even choose the manual partitioning option in the first place? Ubuntu is happy enough to make you go through the process of something as trivial as selecting where the Swap partition is located, but yet for something as critical (and dangerous) as overwriting the MBR of another disk, there is no option at all. I can understand not providing such an option on the automated default install, but any user who chooses the manual option clearly wants to specify each individual mount point, so they can't exactly be averse to choices can they?

I had not even heard of the "alternative" Ubuntu version till reading this thread. As a first time Linux user how was I supposed to know about this if it's not explained anywhere what it is and why I might want to use it? It's certainly not mentioned anywhere on the Ubuntu download page:

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

and the text mode install of the alternative version doesn't exactly sound suitable for beginners anyway.

No doubt people will be saying that it's all my fault for not spending months beforehand learning about all possible distros and boot loaders before daring to trying one out.

I find it ironic that such a big deal is made about the Ubuntu Live CD (as a means of *safely *trying out Ubuntu without any risk to your existing data). 

It's a shame that the same principal is not applied when it comes to actual installation.

---

### Post by gn2 on 2006-12-28
> **oomingmak said:**
> 
No doubt people will be saying that it's all my fault for not spending months beforehand learning about all possible distros and boot loaders before daring to trying one out.


You would seem to have experienced exactly what I did.

Problem is you don't know what you don't know.

I still use Xubuntu on an old laptop, but use another distro, PCLinuxOS on everything else.

---

### Post by szantaii on 2006-12-28
Hi!
I'm new to ubuntu, I recently installed it.
I have 3 hard drives:
[LIST=1][*]120GB sata with two partitions, Windoxs XP on the first (ntfs), and some data on the other (ntfs)[*]200GB sata (ntfs), just for my stuff :D[*]and a 160GB IDE drive with ubuntu



[/LIST]

I set in the BIOS to boot from the IDE drive first, not the onboard sata. GRUB comes in, everything is cool, but when I want to boot to XP GRUB says Loading please wait... and thats it. It doesn't do anything from this point. No error msgs, no nothing...
I can boot into my windows if I set the boot priority to boot from the onboard sata first, but I'd like to use GRUB instead of setting the BIOS all the time I want to load windows.

```
cat /boot/grub/device.map

(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb
```

```
sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cilinderek of 16065 * 512 = 8225280 bytes

  Eszköz Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6397    51383871   83  Linux
/dev/hda2            6398       19457   104904450    b  W95 FAT32

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cilinderek of 16065 * 512 = 8225280 bytes

  Eszköz Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6553    52636941    7  HPFS/NTFS
/dev/sda2            6554       14593    64581300    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cilinderek of 16065 * 512 = 8225280 bytes

  Eszköz Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24320   195350368+   7  HPFS/NTFS
```

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional - magyar
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by confused57 on 2006-12-28
Your grub entry looks like it should boot Windows...you could try:
rootnoverify  (hd1,0)
instead of
root   (hd1,0)

---

### Post by szantaii on 2006-12-29
Thank you for the reply, I tried it but it didn't help. I got an error when I tried to boot into windows:
Error 23: Error while parsing number
I've checked the grub error list but I didn't get any smarter, it says:
> Error while parsing number
This error is returned if GRUB was expecting to read a numbur and encountered bad data.

---

### Post by Pitt Stains on 2006-12-31
Hello,

I followed the instructions at the beginning of this post but can't seem to get into the GRUB menu!  I even increased the timer setting to 5 seconds to make sure I didn't miss it.  During boot I get prompted to press ESC to enter GRUB, but when I do the timer just keeps counting down.  When it gets to 0, it starts loading Ubuntu.

Any idea what might be going on here?

Thanks,
-Pitt

---

### Post by gn2 on 2007-01-01
> **Pitt Stains said:**
> Hello,

I followed the instructions at the beginning of this post but can't seem to get into the GRUB menu!  I even increased the timer setting to 5 seconds to make sure I didn't miss it.  During boot I get prompted to press ESC to enter GRUB, but when I do the timer just keeps counting down.  When it gets to 0, it starts loading Ubuntu.

Any idea what might be going on here?

Thanks,
-Pitt

Don't understand why you want into a Grub menu, if Ubuntu loads what's the problem? :-?

---

### Post by petteriIII on 2007-01-01
Things keep changing all the time. Lately they made menu.lst to be password protected; I dont remember in what type of Ubuntu. But look in the menu.lst for a sentence beginning with : password. Earlier it was commented but nowadays the default is that it is not. 
Password is asked when you press letter: b . You can change the password but default was ubuntu if I recall right.

---

### Post by Pitt Stains on 2007-01-01
> **gn2 said:**
> Don't understand why you want into a Grub menu, if Ubuntu loads what's the problem? :-?

Ubuntu is my default boot.  The problem is that I have no way of selecting my secondary boot since I can't get into Grub.

---

### Post by Pitt Stains on 2007-01-01
> **petteriIII said:**
> Things keep changing all the time. Lately they made menu.lst to be password protected; I dont remember in what type of Ubuntu. But look in the menu.lst for a sentence beginning with : password. Earlier it was commented but nowadays the default is that it is not. 
Password is asked when you press letter: b . You can change the password but default was ubuntu if I recall right.

The password line is indeed commented out.  I noticed this little bit of code:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

I'm going to comment out the hiddenmenu and see if it goes to Grub by default.  Not ideal, as I'll be booting to Ubuntu 75% of the time or more, but hopefully it will give me access to both OS.  Will let you know how it goes.

---

### Post by Pitt Stains on 2007-01-01
Ha!  OK, I suspected this, but now I'm sure.  It seems that my keyboard is not loaded (or at least it doesn't work) until later on in the boot process.  I got into the Grub menu by commenting out the hiddenmenu line but once there couldn't select a different boot (although I could see that they were all there).

Any ideas on how to get the keyboard working sooner?

Thanks,
Pitt

---

### Post by gn2 on 2007-01-01
> **Pitt Stains said:**
> Ubuntu is my default boot.  The problem is that I have no way of selecting my secondary boot since I can't get into Grub.

Windows on it's own drive with native bootloader can be booted by using F8 Boot Device Selection Menu (where BIOS has this function)

---

### Post by Pitt Stains on 2007-01-01
Oh boy, this is embarrassing.  It seems my keyboard was plugged into my mouse port.  Not sure how that happened... miracle Ubuntu recognized it at all!

But now I have a new problem.  When I select the Windows boot, I get:
> Error 11: Unrecognized device string.

Here are the results of sudo fdisk -l:
```
Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4679    37584036   83  Linux
/dev/hda2            4680        4866     1502077+   5  Extended
/dev/hda5            4680        4866     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4110    33013543+   7  HPFS/NTFS
```

Here's what I've added to /boot/grub/menu.lst:
```
title		Windows NT/2000/XP (loader)
map		(hd0,0)(hd1,0)
map		(hd1,0)(hd0,0)
rootnoverify	(hd1,0)
makeactive
chainloader +1
```

Thanks for your help!

---

### Post by Pitt Stains on 2007-01-03
I should also mention that my version of BIOS doesn't support the ESC option that has been written about in this thread.  I've been manually plugging and unplugging my hard drives between boots!

---

### Post by confused57 on 2007-01-04
Don't know if you've seen this option:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by Pitt Stains on 2007-01-07
> **confused57 said:**
> Don't know if you've seen this option:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Thanks for the link.  Somewhere in the thread I read a comment by someone warning everyone at home to make sure to include a space between the hd values in the mapping section.

I.e.,

[COLOR="Green"]GOOD[/COLOR]

```
map		(hd0,0) (hd1,0)
map		(hd1,0) (hd0,0) 
```

[COLOR="Red"]BAD[/COLOR]

```
map		(hd0,0)(hd1,0)
map		(hd1,0)(hd0,0) 
```

Yay!  Thanks to everyone who helped.

---

### Post by Chazall1 on 2007-02-22
I have a question, or question,s. I have been using Ubuntu for about 1 year and have had many of the GRUB and other configuring frustrations along the way. I have learned allot. I am currently Dual Booting WinXP and Ubuntu Edgy 6.10 on a single HD and would like to convert to using 2 HD's. I have read this thread and I have made sence out of it. I know I have to fixMBR and remove Ubuntu on my current HD. I do not want to start over in Edgy with a fresh install on the new HD!!!
I do have Backup Images of Both OS's, 1st Question, Can I install my Ubuntu Image to the New HD? I do have / and /Home. Or would all the hda info not match up when the Image restored, thus not being able to configure? 
Can I follow Anaconda's and bulldogs sugestions to set up a 2HD boot system with using my Image of Ubuntu?
Any suggestion, or should I do a fresh install and copy my /Home Image to the new Install?
Has anyone tried this!!!!!!!!
Thanks

---

### Post by mxreader on 2007-04-15
> **oomingmak said:**
> 
Having been so explicit with my instructions during Ubuntu's setup, I was furious to find that not only did Ubuntu write to a totally different drive without my permission, but there was not even so much as a comment or notification saying that this was going to happen.

Anyway, Grub was installed to my Windows drive and I could no longer boot into Windows. I have no idea why, but no matter what I did it just would not work.

Yep, same here.  I got XP on the master IDE and a SATA dedicated for Ubuntu.  On installing Ubuntu I never wanted Ubuntu to touch the Windows drive MBR, but it did without warning or giving me clear idea that it would do this.  Fortunately for me I was able to select and boot XP from the grub whilst Ubuntu do not boot, which is fine, and at least enabled me to continue productive work.

---

### Post by la3875 on 2007-04-16
I like how you started and think you can succeed with keeping your installs and separating them to two drives. I think I would first disconnect the existing drive with both systems on it and take the Ubuntu image and install it to the new drive. Once that is complete you can edit grub for dual booting with windows. Try rebooting to make sure all is well with the new install.

After you complete that I'd disconnect the new drive and set it aside and reinstall the drive with both systems installed. I think you could fix the MBR and wipe the Ubuntu partition. Once that's complete, again restart to make sure the windows install is still good. If not reimage the drive with your window backup image. Once confirming all is well. shutdown again.

Finally, reinstall the drives with the Ubuntu system as master and windows as slave and you should be good to go! 

Best of luck! Let us all know how it turns out.

---

### Post by mxreader on 2007-04-18
la3875, I presume you are answering one of the above posts and not mine.  Right?   

Anyway I need some advise about what to do with my screwed up configuration.
ATA master has XP, the MBR has grub inserting itself in it
SATA has Ubuntu 6.0.6 LTS, but that does not boot properly, it comes up with the failed mounting filesystem problem.

I can use a live CD and got this
sudo fdisk -l output:

Disk /dev/hda: 80.0 G....
Device Boot Start....
/dev/hda1 * ...........................HPFS/NTFS
/dev/hda2 .............................W95 Ext'd (LBA)
/dev/hda5 .............................HPFS/NTFS
/dev/hda6 .............................HPFS/NTFS

Disk /dev/sda: 80.0 G....
Device Boot Start....
/dev/sda1 * ...........................Linux
/dev/sda2 .............................Extended
/dev/sda5 .............................Linux swap...

however I cannot seem to get to the grub file.  I dont know enough about linux commands to go further to diagnose this.  Help.

---

### Post by la3875 on 2007-04-19
[QUOTE

however I cannot seem to get to the grub file.  I dont know enough about linux commands to go further to diagnose this.  Help.[/QUOTE]

Yes I was looking more at Chazall1's issue. I'm know I'm not the right person to answer this as I'm still new to this myself, but I can point you to some resources that might help. I've found in my short time here that the answer usually exists, you just need the right search or right person to come along and point you in the right direction. 

If you have not seen these already, I've found them to be invaluable resources for setting up dual-boot and other useful functions. In addition if you search the forum for "edit grub" and I think if you go back to the beginning of this thread you will find the grub edit references as well.

Anyhow, give these a look and be patient and methodical and I'm sure you'll get the result you want.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

All the best.

---

### Post by Ghot on 2007-04-19
Ive only toyed with Ubuntu....I have live CD's for versions 5.x, 6.x and now 7.x............

As I understand it....Linux and by default Ubuntu is an open source OS.  Why after so long....do we still have MBR issues?  I mean like updating the kernel in Ubuntu leaves tracks of the older kernel upgrades.....why doesnt someone fix this?   I admit I'm a windows guy at heart (except VISTA  :/) but i WANT to use Ubuntu becoz I believe it is a better OS.   Untill these live CD's start dealing with all the MBR crap....you are hurting your own community...itll scare ppl off.

What I expected to SEE when I installed Ubuntu for dual boot along side WinXP Pro was:   when i boot system I SHOULD see:

                       Microsoft Windows XP Professional
                       Ubuntu


I dont want to see:         kernel
                                        kernel
                                        kernel
                                        Microsoft Windows XP Professional

This does NOT make people WANT to switch  O.o  I shouldnt HAVE to go back and fix the boot.ini  to make it do what it should do all by itself.  Further ANY messing around with the MBR is just silly...Windows dont LIKE it when you mess with the MBR.

Isnt there a way these issues could be resolved solely by/on the Live CD?????? (w/o user intervention)

I have 2 HD's but BIOS switching is nutz  and Ubuntu's trait of leaving all the past kernal upgrades on the OS choices menu is just sloppy.......lastly  Windows was on there 1st and should be 1st on list....

I KNOW this isn't how Windows works....BUT.....you want the world to Linux...then you gotta do it ...BETTER than Windows did. (and yes I know that if I install Ubuntu first, then XP Pro that most of these issues dont occur.  But I want my cake and to eat it TOO!

There should be NO reason that I should ever HAVE to consider these things....Windows messed up the dual boot issue for all but Windows OS's...maybe YOU guys can fix that so the NEXT Ubuntu release...will put itself 2nd on the OS choice list (automatically) and when u update Ubuntu it should erase the previous entries....(automatically)  I guess if I upgrade the kernel enough times, I'll soon have a ...scroll bar ???? on my OS choices screen???    : )

This Ubuntu is a great alternate OS, in fact, its (ssshhh) better than Windows.....BUT, if it ain't idiot proof..then Windows will win in the end ^^

And I don't want to see THAT day  :(

---

### Post by mxreader on 2007-04-20
> **la3875 said:**
> 
Anyhow, give these a look and be patient and methodical and I'm sure you'll get the result you want.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

All the best.

thanks la3875

It was over 6 months ago that i installed 6.06LTS and soon after install i simply could not boot into it, getting those unable to mount filesystem errors. So I gave up and gone back to XP till a few days ago, I had read hermanzone before, and at your promting, had another look... wow he does keep it updated all the time. Great guy.

Anyway, i did have to spend hours printing and reading various options, and man I do agree with Ghot, i dont really want to waste so much time doing this, but today i found the fix with these three commands from there.

sudo parted /dev/hda p ( to check that its an ext3 filesystem since i couldnt mount the damn thing, was it my typing? no!)

sudo dumpe2fs /dev/sda1 | grep -i superblock (since i saw something about superblock as a possible problem in the error message, but hey would you expect it from a new install?)

sudo e2fsck -b 32768 /dev/sda1

Now how cryptic are all these for a newbie, windows GUI-dependent user? very.  But those three line commands (very nicely explained by hermanzone) fixed it and the dual boot works.  Anyway, thanks for your prompting.

:guitar: 

Now to fixing the wireless problem....

---

### Post by oomingmak on 2007-04-21
> **oomingmak said:**
> I had not even heard of the "alternative" Ubuntu version till reading this thread. As a first time Linux user how was I supposed to know about this if it's not explained anywhere what it is and why I might want to use it? It's certainly not mentioned anywhere on the Ubuntu download page:

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

and the text mode install of the alternative version doesn't exactly sound suitable for beginners anyway.

I had to laugh when I read [**[COLOR="DarkOrange"]my post[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=1937710&postcount=119") back (quoted above).

Since then (end of last year) I've Used Ubuntu a fair few times, and I'm a bit more familiar with how it works these days, so I'm not quite so intimidated by it. I therefore got brave one day and tried out the alternative installer CD. 

I actually found the install procedure to be better and easier to understand than the Live CD (even though I thought that it would be way over my head).

Just when I thought that I'd be using the alternative installs from now on (especially after hearing countless comments about how flexible and detailed it was) I got to the end of the partitioning section of the install, pressed enter (expecting to see Grub options on the next page) but there were none, it just started installing. Then half way though the install it just crapped out.

So I would've got screwed again by the exact same issue as last time (despite using the alternative install). Of course, I had my Windows drive unplugged, so it was all good. I learned that one the hard way, and will never ever again let any Ubuntu install go anywhere my system if there are other drives connected.

I don't know whether I just didn't see the Grub setup options (don't know how I would have missed it, as it was an unfamiliar text-based setup procedure and so I was being very careful to read everything) or whether it isn't included in that installer version (which can't be correct, as that would just be insane given the purpose of the alternative CD). But given that it couldn't even complete the install, I'm past caring to be honest.

---

### Post by la3875 on 2007-04-25
Glad to hear the success stories. Since we only have 2 computers in the house and we all share the box I have Ubuntu on, I too unplugged my Windows HD for fear of really screwing up! So far so good and with Feisty, I'm probably abandoning Windows for good this summer.

As for the wireless issue it should not be too hard to configure. When I tried the live CD on my wife's Dell laptop the wireless settings got corrupted when the live disc took over the hardware. The wireless worked but I had to reinstall the intel wireless driver after ejecting the Ubuntu disc. 

As you noted, patience pays huge dividends.

All the best!

---

### Post by gn2 on 2007-05-04
This thread is now largely irrelevant, as 7.04 has an "Advanced" button at the Grub installation stage, which when pressed gives the option to enter a different location for Grub to be written to.

Superb, and not before time!

---

### Post by RiazM on 2007-07-16
Alright so..If I understand this right..

I currently have: windows xp on a sata drive. I'm getting another sata drive soon. 

Can I plug this sata drive in, partition it so it's got a fat32 partition and ext3 partition, intall ubuntu on the ext partition and then dual boot between the two? Should this work?

I've got the  ubuntu 7.04 alternate cd.

Was thinking of installing sabayon but I'm going with Ubuntu just because the forums are way kinder.

---

### Post by oomingmak on 2007-08-30
> **gn2 said:**
> This thread is now largely irrelevant, as 7.04 has an "Advanced" button at the Grub installation stage, which when pressed gives the option to enter a different location for Grub to be written to.
And a fat lot of good it does, because you can't set it to Hd0,0, so it won't work when you switch drives in the BIOS.

[http://ubuntuforums.org/showthread.php?p=2558032&#post2558032](http://ubuntuforums.org/showthread.php?p=2558032&#post2558032)

---

### Post by gn2 on 2007-08-30
> **oomingmak said:**
> And a fat lot of good it does, because you can't set it to Hd0,0, so it won't work when you switch drives in the BIOS.

[http://ubuntuforums.org/showthread.php?p=2558032&#post2558032](http://ubuntuforums.org/showthread.php?p=2558032&#post2558032)

Flawed as it is, it's still a step in the right direction.

Better documentation and warnings concerning GRUB should be given during the installation process, with a link to Herman's outstanding website.

This won't happen because it would put a lot of new users off.

I learned an enormous amount from the Hermanzone site, sadly only after I had a shedload of problems.

I wish I had been steered towards the Hermanzone site earlier before I got the bad attitude towards Ubuntu, which happily has now changed.

It was largely the contact with Herman himself and others within this community that kept me using Linux.

I use it exclusively now.

Although the wife's PC still has a nasty infection of XP :-(

---

### Post by catnippants on 2007-10-09
Folks, I know this is an old thread, but I'm finding it difficult to find new info.   At the moment, I'm stuck and could use some help.

I'm trying to install Ubuntu on a 2nd harddrive, just like most of these threads discuss.  Windows XP is on hda, and I want to use part of hdb for Ubuntu.  My intent was to use my BIOS boot select menu to select the boot drive - as I don't want to touch my WinXP drive.  I've partitioned the 2nd drive using GParted (164G of available space) into 3 pieces - 80 primary for Ubuntu, 2 extended for Swap, and 82 extended as an NTFS drive for data.   I'm installing Ubuntu Studio - so for the sake of discussion, it's the 7.04 alternate installer.   The install completed fine, and I did NOT install GRUB to the hd0 MBR.  Instead, I specified (hd1).   However, now when I boot (with the Ubuntu drive selected as the boot drive), I get the GRUB boot selection screen, but when I pick Ubuntu, I get 'Error 17: Cannot Mount Selected Partition'.   If I switch the boot drive back to the WinXP drive, WinXP loads normally.

It's only now that I saw the comments on disconnecting the Windows drive prior to installing Ubuntu.   I've also now seen comments stating that this is irrelevent with 7.04 because you can choose the GRUB install location.   However, I'm still unclear on what I did wrong - or how to fix it to get Ubuntu to load.    Any thoughts or direction?   I've read most of the newer tutorials, and it seems like I did all those things, so I'm somewhat at a loss.

Any help would be greatly appreciated,
Mike

---

### Post by confused57 on 2007-10-09
You'll need to change the root from (hd1,x) to (hd0,x)...you can do this by highlighting your first Ubuntu entry in the grub boot menu, press "e", highlight the line with root, press "e" again, change your root from (hd1,x) to (hd0,x), press "enter", then press "b" to boot...x means to leave this value as it is.  This change is temporary, but you can make it permanent in your /boot/grub/menu.lst...open a terminal(Applications---Accessories---Terminal):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
change your root entries to (hd0,x) and be sure to change the line with #groot to (hd0,x):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

quit & save

You could probably add an entry to your menu.lst to boot your Windows drive from grub:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by catnippants on 2007-10-09
Thanks - I do believe I tried (hd0) just for kicks and it also failed (temporary edits to the root line as you descibed above).  I will try hd0,0 tonight to see if that helps (as Ubuntu is in the first partition of  the 2nd disk).    However, this doesn't make sense to me unless my bios physically maps my 2nd disk to hd0 at boot time - but not during the install.  Is this what is happening?

Thanks,
Mike

---

### Post by confused57 on 2007-10-09
> **catnippants said:**
> Thanks - I do believe I tried (hd0) just for kicks and it also failed (temporary edits to the root line as you descibed above).  I will try hd0,0 tonight to see if that helps (as Ubuntu is in the first partition of  the 2nd disk).    However, this doesn't make sense to me unless my bios physically maps my 2nd disk to hd0 at boot time - but not during the install.  Is this what is happening?

Thanks,
Mike

Here is an excellent guide explaining grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

When you installed Ubuntu, your hard drive boot order was probably your Windows drive, then your Ubuntu drive, which would result in your Ubuntu drive being recognized as (hd1) by grub.  Selecting your Ubuntu drive as the first hard drive booted in bios would essentially change it's designation to (hd0), therefore "root (hd1,0)" would result in the error 17 that you're seeing...root would need to be (hd0,0).  I believe if you had set your Ubuntu drive to boot first in bios before you installed Ubuntu, it would have been recognized as (hd0) & "should" have booted correctly.

---

### Post by catnippants on 2007-10-09
That did it!  I'm replying from within Ubuntu right now.   Thanks a bunch for the help.   Now I'm going to screw around with the menu.lst file and see if I can get Windows to load via GRUB rather than using my bios...

Thanks again,
Mike

---

### Post by gobuntu on 2007-10-10
I have two hard disks on my laptop.

For a time, I did give Linux the second drive, but no, that's not my prefered way now.

Now, I have made the first drive the Operating Systems and booter, and the SECOND hard-disk is for DATA.

Why so? Operating systems per-se don't take a whole lot of space. It's data which takes up the space. It's data which is more valuable. Of course working operating systems are quite valuable too, and with this aproach, they are backed up 'separately', often to the second hard disk. From there they can be rescued if necessary with the proper softwares.

I can remove the second hard disk, upgrade it, degrade it, etc, and my operating systems stay pretty much the same.

This has many, many more conveniences that I realized only after quite a bit of suffering.

Ubuntu takes so far less than 4 gigabytes, and a backup of it is like 1.5 GB due to backup images are compressed. The backup is on my second hard drive.

On my second hard-drive, I have separate partions for data that can be mounted for Linux read and write, and also a FAT-32. It depends how one formats those partitions, of course.

The second hard-drive I backup to an external USB drive on 'a partition' basis, and at times, I backup entire disks.

I backup the Master Boot Record to a file using Linux and of the GRUB menu list.

Also, I have encripted passwords at GRUB booter, which always stays in the first disk, because if the GRUB menu is on the second hard disk, and it gets affected by repartitioning, or whatever, no system can boot.

---

### Post by catnippants on 2007-10-10
> **gobuntu said:**
> I have two hard disks on my laptop.

For a time, I did give Linux the second drive, but no, that's not my prefered way now.

Now, I have made the first drive the Operating Systems and booter, and the SECOND hard-disk is for DATA.

Why so? Operating systems per-se don't take a whole lot of space. It's data which takes up the space. It's data which is more valuable. Of course working operating systems are quite valuable too, and with this aproach, they are backed up 'separately', often to the second hard disk. From there they can be rescued if necessary with the proper softwares.

I can remove the second hard disk, upgrade it, degrade it, etc, and my operating systems stay pretty much the same.

This has many, many more conveniences that I realized only after quite a bit of suffering.

Ubuntu takes so far less than 4 gigabytes, and a backup of it is like 1.5 GB due to backup images are compressed. The backup is on my second hard drive.

On my second hard-drive, I have separate partions for data that can be mounted for Linux read and write, and also a FAT-32. It depends how one formats those partitions, of course.

The second hard-drive I backup to an external USB drive on 'a partition' basis, and at times, I backup entire disks.

I backup the Master Boot Record to a file using Linux and of the GRUB menu list.

Also, I have encripted passwords at GRUB booter, which always stays in the first disk, because if the GRUB menu is on the second hard disk, and it gets affected by repartitioning, or whatever, no system can boot.

I may try this at some point, but for now I'm just experimenting with Ubuntu.   My current config allows me to keep my Windows system intact.   However, this comment:

"Also, I have encripted passwords at GRUB booter, which always stays in the first disk, because if the GRUB menu is on the second hard disk, and it gets affected by repartitioning, or whatever, no system can boot."

confuses me.  In my case, if something happens to my second drive, all I have to do is swap boot drives in my bios and I'm up and running with Windows again...

Mike

---

### Post by kgsbu on 2007-11-04
For those still trying to boot from separate hard drives without success, the following is how I got mine working. My configuration is Ubuntu on a  IDE 1 drive configured as master, and XP on a SATA drive 1.
The following was added to menu.lst:

title Windows XP Pro
map (hd0) (hd1)
map (hd1) (hd0)
rootverify (hd1,0)
savedefault
makeactive
chainloader (hd1,0)+1

Without the (hd1,0) in the chainloader line grub kept returning an error 13 : Invalid or unsupported executable format.
After a day of searching this suggestion was found on the Linux/BSD - Whirlpool Broadband Forums.

---

### Post by kgsbu on 2007-11-04
For those still trying to boot from separate hard drives without success, the following is how I got mine working. My configuration is Ubuntu on a  IDE 1 drive configured as master, and XP on a SATA drive 1.
The following was added to menu.lst:

title Windows XP Pro
map (hd0) (hd1)
map (hd1) (hd0)
rootverify (hd1,0)
savedefault
makeactive
chainloader (hd1,0)+1

Without the (hd1,0) in the chainloader line grub kept returning an error 13 : Invalid or unsupported executable format.
After a day of searching this suggestion was found on the Linux/BSD - Whirlpool Broadband Forums.

---

### Post by straptin958 on 2007-11-26
Ok here is my problem i have jus been introduced to ubuntu and i waned to partition my hard drive to dual boot XP and Ubuntu but i would have to format the drive and start over..

Instead I have ordered another harddrive and was wondering if it possible to install ubuntu on that harddrive and dual boot. 

The Method I want to take.

Install ubuntu to new hard drive and since i have this easy boot feature i will select it to load from which ever drive i want it to but is there another way that may be even more simple? Will my method even actually work. 

I dont know what RAID actually is but will that help me?

Thanks for the help

---

### Post by la3875 on 2007-11-27
You're in the right forum thread, just look up a few pages in the posts for the details. I have been doing it successfully for over a year, thus keeping computer harmony in the family while I test drive Ubuntu. 

My recommendation is to follow the directions to dual boot making Ubuntu the master and the other OS the slave. This way you don't have to mess with the BIOS. It does require a simple tweak of the GRUB boot loader menu but if I can do it, anyone can...

I'm sold on the distribution and cant wait to get a computer with more horsepower so I can run XP virtually for those few programs I just gotta have.

Good luck and welcome to the community!

---

### Post by straptin958 on 2007-11-28
when you say tweak the GRUB bootloader... exactly what would i be doing.

---

### Post by la3875 on 2007-11-28
See the first post in this thread and this link for help: 

Here is an excellent guide explaining grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I could not have succeeded without it. Be patient and keep asking questions. Good luck.

---

### Post by peelie on 2008-09-25
hi

so i have a dual boot system with win xp and ubuntu; i want to add a second older ide (pata) drive that has win xp (from my old computer).

the thing is my new computer has its sata drive on the secondary slave IDE channel.

so what is the best way to add my old drive? seems i would need to reinstall win xp and ubuntu on the sata drive connected as master not as slave?

most confusing any help appreciated

---

### Post by caljohnsmith on 2008-09-25
> **peelie said:**
> hi

so i have a dual boot system with win xp and ubuntu; i want to add a second older ide (pata) drive that has win xp (from my old computer).

the thing is my new computer has its sata drive on the secondary slave IDE channel.

so what is the best way to add my old drive? seems i would need to reinstall win xp and ubuntu on the sata drive connected as master not as slave?

most confusing any help appreciated
So is your XP and Ubuntu currently on the SATA drive? Are you able to boot from it? Then you want to add an older IDE drive with just XP on it? And if your SATA drive is on the secondary slave IDE channel, what is on the first channel?

---

### Post by peelie on 2008-09-26
> **caljohnsmith said:**
> So is your XP and Ubuntu currently on the SATA drive? Are you able to boot from it? Then you want to add an older IDE drive with just XP on it? And if your SATA drive is on the secondary slave IDE channel, what is on the first channel?

yes XP Pro and Ubuntu on SATA drive, able to boot from it.

CD is on primary slave channel, nothing on primary master channel.

after some thought i see that maybe it might be easier to put the old pata drive on the empty primary master?
thx

---

### Post by HousieMousie2 on 2008-09-28
Okay, here's my Dual-Boot/GRUB questions.

It seems likely that when I installed Hardy (on IDE HDD-2) that the MBR was over written on my OLD XP HDD-1 (IDE) since both HDD's were in the machine when I installed Hardy and XP was already present... but...

How can I confirm the physical location of the GRUB?

I have a second computer that has a fresh install of XP on a SATA drive.  I want to take the old installation of Hardy (on IDE HDD-2) and stab it into the new machine, and have GRUB on the Hardy HDD-2, so that the NEW XP-SATA's MBR is not altered.

I understand how to set the jumpers/channels, what I don't know is:

How to make sure that the GRUB/necessary changes is/are on the Hardy HDD before I move it to the new machine and if it is not, then how to put GRUB on it while it is in my OLD machine.  (I can edit the GRUB later to include the new XP SATA HDD... or at least I think I can manage that!  Might be a little optimistic of me, but hey, I successfully edited fstab before, how hard can it be? lol)

Any help would be great!

Thank you for reading this!

Cheers

PS, I know about sudo fdisk -l and cat /boot/grub/menu.lst... which imply that GRUB is on Hardy HDD, makes sense... don't understand what is done to the Windows MBR then.

PPS, Is it as simple as grub-install /dev/sdb1?  And then editing it once it is in the new machine to add the XP SATA?

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38536   309540388+  83  Linux
/dev/sdb2           38537       38913     3028252+   5  Extended
/dev/sdb5           38537       38913     3028221   82  Linux swap / Solaris

---

### Post by caljohnsmith on 2008-09-28
HousieMousie2, first, you can install Grub to the MBR of your HDD-2 drive with the following:
```
sudo grub
grub> find /boot/grub/stage1
```
The above command should return your Ubuntu partition in the form of (hdX,Y), for example (hd1,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Your suspicions are probably correct that Grub is in the MBR of your old Windows HDD-1 drive. You could check with:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=512 count=1 2>/dev/null | strings | grep -i grub
```
Where sda should be your "HDD-1" drive, so change it if it isn't. If the above command returns "GRUB", then it is almost certain you have Grub installed to the MBR of sda. If it doesn't return anything, you have some other boot loader in the MBR. If you need to reinstall the Windows MBR to the Windows HDD-1 drive, you can boot your Windows Install CD, press "r" at the first menu to get the "recovery console", and run:
```
fixmbr
```
Let me know how it goes or if you need more info/details.

---

### Post by HousieMousie2 on 2008-09-28
> **caljohnsmith said:**
> If you need to reinstall the Windows MBR to the Windows HDD-1 drive, you can boot your Windows Install CD, press "r" at the first menu to get the "recovery console", and run:
```
fixmbr
```
Let me know how it goes or if you need more info/details.

Unfortunately, that Windows install was done by HP, with no CD provided (just a recovery partition) and the check of the Windows MBR did return "GRUB."

Correct me if I am wrong, please, but can't I use fixmbr from the DOS/Command prompt (Within Windows) and it will use the data in the partition to rewrite the MBR?

It is important to me that I salvage the old XP machine, since I am planning to donate it to charity, with a shiny new (vanilla) XP installation... from the partition.

The results of the grub> codes:
```
[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```

That looks good to me, what do you think?

Thanks a million, caljohnsmith!

---

### Post by caljohnsmith on 2008-09-28
> **HousieMousie2 said:**
> Unfortunately, that Windows install was done by HP, with no CD provided (just a recovery partition) and the check of the Windows MBR did return "GRUB."

Correct me if I am wrong, please, but can't I use fixmbr from the DOS/Command prompt (Within Windows) and it will use the data in the partition to rewrite the MBR?

Yes, if you have "fixmbr" in your Windows install you could run it from there; but I just searched mine (Home Edition) and it doesn't have it. Do you have a Windows Install CD where you can run that command from? If you don't, another easy alternative is to download the "[Super Grub Disk]("http://www.supergrubdisk.org/")", which can install a Windows-compatible MBR that should work just fine. I just checked right now and it looks like their server might be down at the moment. You could google super grub disk and probably find other mirror sites to download it from. 

Your output from running the Grub commands looks great, so you should be able to boot from your Ubuntu drive now, assuming you set the BIOS to do so. You will most likely need to modify the Grub menu entries though to get the OSes to boot, since it looks like Grub was previously in the MBR of your Windows drive. 

So try booting from your Ubuntu drive, select the Ubuntu entry in the Grub menu you want to boot, hit "e" to edit it, select the line that says "root (hd1,X)" where X is a number, press "e" to edit it, change it to "root (hd0,X)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes. Also note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent if it works. Let me know if you get this far or if you run into problems. :)

---

### Post by HousieMousie2 on 2008-09-28
lol Why does that not surprise me?  I don't know if my XP will allow me to fixmbr or not, probably not since it is *also* Home, but perhaps it will, since it is a recovery partition version...  I will have to check on that.  If I do not have the option to fixmbr from within the Windows installation, I do have an XP Home installation disk.  How certain are you that it will not create a problem?... using a non-HP XP disk to make the MBR for the HP XP?

As you can see, I don't know how it does what it does to restore/rewrite the MBR and want to be certain before I proceed.

To double check, are you instructing me to:

Restart, enter BIOS, switch the XP and Linux boot priorities, save & exit, at the Grub screen, select Hardy, edit the hd1,X/hd0,X, save, boot.

If happy with it, then:

```
kedit /boot/grub/menu.lst
```

Changing:

```
## ## End Default Options ##

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
**root            (hd1,0)**
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=5d665106-a47a-44c7-9cd9-7315b25cbbd8 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
**root            (hd1,0)**
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=5d665106-a47a-44c7-9cd9-7315b25cbbd8 ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, memtest86+
**root            (hd1,0)**
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP
**root            (hd0,0)**
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Microsoft Windows XP Home Edition
**root            (hd0,1)**
savedefault
makeactive
chainloader     +1

```

To this:

```
## ## End Default Options ##

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
**root            (hd0,0)**
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=5d665106-a47a-44c7-9cd9-7315b25cbbd8 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
**root            (hd0,0)**
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=5d665106-a47a-44c7-9cd9-7315b25cbbd8 ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, memtest86+
**root            (hd0,0)**
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP
**root            (hd1,0)**
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Microsoft Windows XP Home Edition
**root            (hd1,1)**
savedefault
makeactive
chainloader     +1

```

If I recall correctly, the Linux HDD is set to Slave and the XP HDD is still set to the default Cable Select, via the jumpers... should I put them both to Cable Select?

---

### Post by caljohnsmith on 2008-09-28
> **HousieMousie2 said:**
> lol Why does that not surprise me?  I don't know if my XP will allow me to fixmbr or not, probably not since it is *also* Home, but perhaps it will, since it is a recovery partition version...  I will have to check on that.  If I do not have the option to fixmbr from within the Windows installation, I do have an XP Home installation disk.  How certain are you that it will not create a problem?... using a non-HP XP disk to make the MBR for the HP XP?

As you can see, I don't know how it does what it does to restore/rewrite the MBR and want to be certain before I proceed.

Yes, from the your XP install CD, just run the "fixmbr" command, and it should be fine assuming your Windows drive is still the master drive. Also, all the Windows MBR does is "chain load" or boot the boot sector of whatever partition on your HDD is marked as active, i.e. has its boot flag set on. There are actually many boot loaders that can do this, so you don't even need a Windows MBR technically; therefore you shouldn't have anything to worry about with a non-HP Windows CD creating a MBR for your HP XP. :)

> **HousieMousie2 said:**
> 
To double check, are you instructing me to:

Restart, enter BIOS, switch the XP and Linux boot priorities, save & exit, at the Grub screen, select Hardy, edit the hd1,X/hd0,X, save, boot.

Exactly--make the Linux drive boot first, and then edit the Ubuntu menu entry as give before so you can boot it. Once you are in Ubuntu, open your menu.lst with either of the following:
```
gksudo gedit /boot/grub/menu.lst
kdesu kedit /boot/grub/menu.lst
```
In other words, you have to make sure you run the text editor as root. Next edit your Ubuntu entries as you showed, but for Windows, use the following:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP
root            (hd1,0)
[COLOR="Red"]map        (hd0) (hd1)
map        (hd1) (hd0)[/COLOR]
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Microsoft Windows XP Home Edition
root            (hd1,1)
[COLOR="Red"]map        (hd0) (hd1)
map        (hd1) (hd0)[/COLOR]
savedefault
makeactive
chainloader     +1
```
In other words, you got the drive right with (hd1,X), but you have to use Grub's mapping feature like above to fool Windows into thinking it is actually on the master drive when you boot it, otherwise Windows won't boot. Let me know how it goes or if you run into problems.

---

### Post by HousieMousie2 on 2008-09-29
I got sick of fighting with it in the old machine, went ahead and moved Hardy to the new machine... the grub still isn't right, using the BIOS to switch between OS's.  And honestly, I have bigger fish to fry right now... XP took a nose dive, can ONLY boot to Safe Mode/Command Prompt.  It is probably a bad video driver.  I am considering just dumping it and reinstalling (no personal data on that drive yet.)

I have borrowed a set of HP XP installation disks and am hoping it will work to do the fixmbr, since I could not do it from within Windows, or using the non-HP XP disks.  Will try that tomorrow... it is late-thirty here, 4am.

I don't feel the day was totally wasted: walked my Mom through the upgrade from Dapper to Hardy, provided moral support for the recompile of her beloved calendar ICAL, and installed the driver for my GeForce 9600 GT video card in Hardy.  Now if I can just get the X-Fi audio card to work Hardy will be totally set up... uh, except for the grub, of course. :-k

More later... uh, sorry for the novel, I get even MORE verbose when tired.

Cheers

---

### Post by LinuxTAd on 2009-05-07
title Windows NT/2000/XP (loader)
map (hd0,0) (hd2,0)
map (hd2,0) (hd0,0)
rootnoverify (hd2,0)
makeactive
chainloader +1



Did it for me, Thank you very much! I appreciate it   :popcorn:




Next up... The ATI Catalyst drivers which kill my display (2-3 times now)! :KS

---

### Post by isa.k on 2009-05-11
[CENTER][COLOR=Red]**[FONT=Arial][SIZE=6]! ! ! URGENT HELP NEEDED ! ! ![/SIZE][/FONT]**[/COLOR][/CENTER]

I know absolutely nothing about Ubuntu/Linux OSs...

I dunno if I should start a dedicated thread regarding my problem, or just complain (:P) here?

I will start here, and if mods or Admin decides to move it toits own thread, so be it...

As I stated, I know absolutely minimal info about Ubuntu/Linux... other than it is safe, and very tweakable.

I need to run Adobe CS4 Master Collection on my box, so I thought I would run VirtualBox, or something similar on Ubuntu and run Vista off it, so I could use the Adobe suite.

VirtualBox gave me a really small screen, which does no justice to any graphic designer. Anyway, I could not allocate more than 128MB of my 1GB gc to VirtualBox anyway... As for ram issues, that is another thing... I could successfully only allocate just under half my 8GB ram to the virtual box (or was that maximum upto half?).

[SIZE=4][COLOR=Red]**Ok, my conundrum...**[/COLOR][/SIZE]

I have installed Ubuntu a couple of days ago, not realising I would need to dual-boot in the future.

After my problem of not getting the desired results with VirtualBox, I decided to do a dual-boot and run everything on Ubuntu, and use Vista (on the dual) solely for graphic/multimedia design purposes.

So far I have tried Googling for dual-booting, with Ubuntu installed first, and came across these links:

```
http://users.bigpond.net.au/hermanzone/

http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot

http://burace17.wordpress.com/2008/05/28/how-to-dual-boot-windows-vista-and-ubuntu-ubuntu-installed-first/
```I have followed the last link's instructions, as it seemed the most straightforward.

I get stuck on Step #7

I get the error that I can't use that partition to install Vista on...

So, I then added my spare HDD to see if I could install it on that... Same problem!

Mind you, I now have two HDDs in my box. One 320GB SATA with Ubuntu installed onto it. Following the instructions in the above link, I gave my Ubuntu  30GB and the rest was formatted while trying to setup Vista on it.

The second is a 200GB IDE, partitioned (previously) to 150GB/50GB with the jumper set to Cable Select.

One last note, when I tried installing onto the IDE HDD, Windows' setup did not detect the partitioned part of the SATA HDD [COLOR=Silver](or did it not detect the IDE at all??? Now I am confused! I will check now, and be back in 10-20 minutes. But if the problem lies elsewhere, please do not wait for me to come back. Just say your mind already :))[/COLOR].

I know, you are probably going to say, "Go ask a Microsoft forum!", but I somehow trust the folk here more, than I could any MS forum...

Now, I would like to ask the geeks and/or nerds here at UbuntuForums, if they could please help me resolve my predicament... (btw, I am surprised there are no emotes for "geek" or "nerd" here.. I may have to design one once I get the Vista part running, and run it past Admin here :)

[SIZE=4][COLOR=Red]**EDIT:**[/COLOR][/SIZE] I checked the HDD, and I forgot to plug the other end of the IDE cable into the motherboard :oops:

Anyway, I plugged it in, tried it with Cable Select and Master the switches... Both not working...

I wrote down the error/warning message in Windows setup this time, maybe this may shed some light?

**When I select the partition, it says:**
This computer hardware may not support booting to this disk. Ensure that the disk's controller is enabled in the computer's BIOS menu.

**When I click the Install (or was it the 'Next') button:**
Windows is unable to find a system volume that meets its criteria for installation.

Now, in light of the first message, I tried looking at the BIOS settings to see if I could get the HDD to be detected manually, and I failed

---

