---
title: "Setting up a Dual boot from Scratch."
date: 2011-11-04
forum: New to Ubuntu
---

### Post by Greywolft on 2011-11-04
[FONT="Georgia"][SIZE="2"][COLOR="Purple"][I]
Greetings All,

My earlier attempt to put Ubuntu on an external Drive came to a dead end. I kept running into issues getting them both to show up as options with no real way around it. 
Now I'm going to try it from scratch. 
My 3 main reasons for doing a clean install are:
1 my USB ports wont recognize anything until the PC is rebooted
2 There's far to much stuff on the PC I don't recognize or even know how it got there
3 I'm sick to death of having to tip toe around XP's various issues and restrictions and having to read tons of work around info just to get a game up and running. Figure if I'm going to be researching anyway might as well do it learning a new OS;plus having both will be a nice reprieve and keep me from shipping my PC to MS in pieces.

Here's my set-up and questions to get this done right.

I have an HP Pavillion Media Center PC m7650n
Intel Core 2 CPU 6300 @1.86 each
2GB Ram
Geforce 9800 GT PCI-E Video Card
40" RCA HDTV as Monitor
Hitachi HDD 320Gb Sata
WD Mybook External HDD 1Tb
Running XP Media Center Sp3

I'm currently making a backup right now 48,967 Files 173.89GB so it's going to take a while and I'm wondering am I backing up the issues this OS is having too? Doesn't seem to make sense to reinstall if I'm just going to put the problems back on. 

Once done I'm going to format the 320Gb drive to have XP MCE and Ubuntu in their own separate partitions and the rest of the space for other programs and files. With 2Gb memory should I create a swap for virtual mem? 
What's the best way to partition the main drive with least amount of hassles for both OS. 

The External will be where all my media such as games, music, Movies etc are stored for both to access. What's the Best Linux OS for multimedia and sharing over network to other PC's and Xbox 360?

Is there a guide or walk through that will help me do this?

Any other hints, tips or tricks to make this not so daunting is much appreciated. Not expecting anyone to reinvent the wheel, pointing me in the right direction is just fine by me.

Thanks in advance and have a Great Weekend!
Tob


[/I][/COLOR][/SIZE][/FONT]

---

### Post by Ricx94 on 2011-11-04
ok, lets see how much i can help with...

ubuntu is fine dealing with windows, but windows doesn't like ubuntu, which means windows should be put on the pc first, having everything it's way (i don't like the idea of it, but less hassles that way). when you put in the disc for windows xp, it loads everything up while on a blue screen. when you get the opportunity to do so, erase all partitions, then CREATE a new one, the size you want windows to be. install windows on that partition, get all the drivers and such from [HP's website]("http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?cc=us&dlc=en&lc=en&product=3245034&") (i checked, and they have all the drivers for that computer for xp, vista, and 7)

after doing that, install ubuntu on the open space on the drive, making sure not to delete windows in the process. it should give the option to install ubuntu in the open space on the drive. i believe it should set up GRUB to choose an OS each time you turn on, as well.

I am not sure which linux OS would work best for media sharing, etc., but i figure ubuntu is probably as good as any.

---

### Post by elgordodude on 2011-11-04
There are lots and lots of guides available I don't have any bookmarked but google can do it in a second.

1) 49,000 files sounds like your backing up your system files, so yes you may end up with some of the same problems, but you might have 40,000 music files or 40,000 pictures so it's hard to say without knowing the program or method you're using to back up. When I wipe a disk I prefer to do it manually, it can take a long time, but is well worth it. Some common things to grab: emails, pictures, music, saved game files (you'll need to reinstall the games themselves) quick books files, documents etc.

2) Definitely, it's always a good idea to create swap space, and 2 gigs isn't that much anymore.

3) Install Windows first on an NTFS partition, then install Ubuntu on an ext3 or ext4, and create the swap partition during Ubuntu installation.

4) Ubuntu seems to work as well as anything else over a local network, if you're comfortable with it I'd use that, and you do mean to access the drive right? You don't need an OS on network drives.

Finally take your time, if you have the space on the 1TB I would mirror the entire 320 in a partition then copy all of the files and folders you want on to a second partition on the drive. Double check yourself often, once you reformat there's no going back. Also grab a favorite beverage, and turn something on the tv that will pass the time, but doesn't require your attention. I prefer baseball, but hockey or soccer works as well. It takes a long time to backup, then a long time to install windows and ubuntu, and another long time to tweak your settings, programs, and updates, and copy all your files back

---

### Post by Rex Bouwense on 2011-11-04
Here are a couple of web sites:

[http://ubuntuforums.org/showthread.php?p=10257675](http://ubuntuforums.org/showthread.php?p=10257675)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Are these what you are looking for?

---

### Post by Greywolft on 2011-11-08
> **Rex Bouwense said:**
> Here are a couple of web sites:

[http://ubuntuforums.org/showthread.php?p=10257675](http://ubuntuforums.org/showthread.php?p=10257675)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Are these what you are looking for?

Yup, exactly, thanks!

> **elgordodude said:**
> There are lots and lots of guides available I don't have any bookmarked but google can do it in a second.

1) 49,000 files sounds like your backing up your system files, so yes you may end up with some of the same problems, but you might have 40,000 music files or 40,000 pictures so it's hard to say without knowing the program or method you're using to back up. When I wipe a disk I prefer to do it manually, it can take a long time, but is well worth it. Some common things to grab: emails, pictures, music, saved game files (you'll need to reinstall the games themselves) quick books files, documents etc.

2) Definitely, it's always a good idea to create swap space, and 2 gigs isn't that much anymore.

3) Install Windows first on an NTFS partition, then install Ubuntu on an ext3 or ext4, and create the swap partition during Ubuntu installation.

4) Ubuntu seems to work as well as anything else over a local network, if you're comfortable with it I'd use that, and you do mean to access the drive right? You don't need an OS on network drives.

Finally take your time, if you have the space on the 1TB I would mirror the entire 320 in a partition then copy all of the files and folders you want on to a second partition on the drive. Double check yourself often, once you reformat there's no going back. Also grab a favorite beverage, and turn something on the tv that will pass the time, but doesn't require your attention. I prefer baseball, but hockey or soccer works as well. It takes a long time to backup, then a long time to install windows and ubuntu, and another long time to tweak your settings, programs, and updates, and copy all your files back



Damn you weren't kidding! I backed it up twice for good measure. Odd thing is, Kaspersky's version was 248GB and took almost 2 days. Western Digital's Mybook Backup program was 173GB and took about 8 hours. Not sure why there's such a big difference in space and time since they both "supposedly" backed up the whole system.

I'm looking around for a Sata HDD from friends and such to avoid formatting at all. If I can trade some of these IDE drives I have for a Sata drive and just install them on that. I can deal with formatting the 320GB drive once I have things set up and running the way I want. 

I just remember how aggravating it was last time to do it all from scratch and NOT have the info to fall back on. Plus it never fails, I ALWAYS remember something I need after it's gone. 

Thanks for the Tips and hopefully this will go much better.

---

