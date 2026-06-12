---
title: "HowTo: Automount NTFS Drives"
date: 2008-05-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Joeb454 on 2008-05-07
Ok, I decided to write this - because over the last week or 2 I've been seeing **a lot** of threads asking how to AutoMount drives in Ubuntu. Most of the time these also happen to be NTFS drives ;)

I know what it's like - I still dual boot too :) So anyway - here's how to do it the nice easy way :D

**_NB:_** Please note that there are some images attached just for you ;)

-------------------------------------------------------------------------

Fire up a terminal, to do this click **Applications > Accessories > Terminal**
Then type (or copy/paste) the following - **_1 line at a time_**```
sudo aptitude update
sudo aptitude install ntfs-config
```

**Ubuntu 10.10** doesn't come with aptitude installed, so simply run these 2 commands in place of those above. ```
sudo apt-get update
sudo apt-get install ntfs-config
```

Ok so when that returns you to **user@pcname**, that should be it installed :)

Next, make sure you have **NO** drives mounted (they'll usually appear on your desktop). And then run the program from **Applications > System Tools**

**Note:** In Ubuntu 9.04 (Jaunty) and later it appears that the configuration tool has moved to **System > Administration**.

Enter your password when prompted - and then choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" and click OK.

Enjoy your automounted NTFS Drives :D

**Note:** If you want to undo this for whatever reason, StolenPie posted a walkthrough [later in the thread]("http://ubuntuforums.org/showpost.php?p=8221939&postcount=139") :) So kudos for that!

---

### Post by lecter255 on 2008-05-09
how about a FAT32 usb stick?

---

### Post by Joeb454 on 2008-05-09
I'm not sure about that, though I do know that it allows you to do this for External Drives.

Also why would you want to auto-mount a USB Drive?

---

### Post by lecter255 on 2008-05-09
well the problem is i can't mount it at all. that's why i started this thread:
[http://ubuntuforums.org/showthread.php?t=784970](http://ubuntuforums.org/showthread.php?t=784970)

in fact, i still can't mount external hard drives or my usb key even using ntfs-conf. I can only mount partitions from my internal hard drive on my laptop.

---

### Post by Xiong Chiamiov on 2008-05-09
I've never had to do anything special to mount my NTFS partition.  I just have a line in my fstab:
```

/dev/sda4       /windows        ntfs    defaults,umask=007,gid=46,noatime   0       0

```

---

### Post by lecter255 on 2008-05-09
> **Xiong Chiamiov said:**
> I've never had to do anything special to mount my NTFS partition.  I just have a line in my fstab:
```

/dev/sda4       /windows        ntfs    defaults,umask=007,gid=46,noatime   0       0

```

but can you mount external drives though? i can mount NTFS partitions in my internal hard drive too, no problem, but I can't use my usb key or external hard drive.

---

### Post by Xiong Chiamiov on 2008-05-09
I don't have any external drives in my apartment right now, but shouldn't it be essentially the same?  Or do they not show up in /dev?

---

### Post by lecter255 on 2008-05-10
they show up in /dev but when i try to mount it it always gives an error saying wrong mount point or bad mount point or something.

---

### Post by Rixii on 2008-05-10
Thank you for this post but I am still having problems. With NTFS Config, it goes straight to the third thumbnail, I never see the second. (Using 7.10) Also, I can only select the external option (it's checked), but that should be what I need right? I'm trying to mount an external drive...

I had it removed properly from XP, and it shows up fine there. It doesn't appear to mount in Ubuntu but when I use the Sys Info tool it does show up. And in GPartition, it says it's unallocated?

It's a 250 GB Seagate drive, but it is almost full.. That wouldn't be a problem would it? I asked in the hardware forums last week but received no replies, can anyone help?

---

### Post by Joeb454 on 2008-05-10
Hmm, I've not got an external NTFS drive I can try this with, though I know it shouldn't be mounted before running NTFS config is run (could be an issue/bug with external drives).

If the drives NTFS Config finds that can be mounted are **already** mounted - it will skip the first screen

---

### Post by Nythain on 2008-05-10
> **lecter255 said:**
> they show up in /dev but when i try to mount it it always gives an error saying wrong mount point or bad mount point or something.
well, we're gettin a little off topic here, but ill try to help, or at least get enough info out of you to let someone else help

results of
fdisk -l (sudo?)

next, results of
blkid

next, contents of
/etc/fstab

if its giving you a mount point error, maybe give what
ls -la
looks like in the directory CONTAINING the mountpoint... not inside the mountpoint itself

hopefully, we'll get you squared away :)

---

### Post by ukblacknight on 2008-05-30
Question: Why did they stop auto-mounting NTFS drives in 8.04?  They auto-mounted in 7.10, seems like a step backwards to me.  Is it a bug or did they remove the feature?

---

### Post by Joeb454 on 2008-05-30
They didn't auto-mount in 7.10 :)

You'll find that in both 7.10 and 8.04 the NTFS drive would appear under Places, and you had to click them to mount them.

The method I described in the original post just provides an easy way to auto-mount the drives :)

---

### Post by ukblacknight on 2008-05-30
Im positive they did auto-mount, otherwise I wouldn't of noticed them not auto-mounting?  The NTFS drive always appeared on my desktop, mounted, in 7.10 right out the box.

Either way, I installed ntfs-config to mount them on start up :D (didn't need this in 7.10)

---

### Post by Joeb454 on 2008-05-30
Hmm, strange - I had to install ntfs-config to auto-mount them in 7.10 (and 7.04)

---

### Post by devils horns on 2008-05-31
i tried what you said and its telling me i dont have permieson to mount the hard drive any answers

---

### Post by Joeb454 on 2008-05-31
Are you using NTFS config?

Also do you have any drives currently mounted?

---

### Post by aizo on 2008-06-04
Thanks for the advice Joeb454,
That was exactly what I was looking for! 

Now Amarok won't keep getting confused when all that work from scanning my music collection disappears every time I reboot. :)

---

### Post by Joeb454 on 2008-06-05
Hehe :)

**aizo** That's *exactly* what I use it for :D

---

### Post by martinolsson84 on 2008-06-08
Thanks! Solved my problem in no-time =)

---

### Post by Joeb454 on 2008-06-09
Glad it worked :)

---

### Post by kansasnoob on 2008-06-09
For hot-plugging USB devices ie: pen drives, cameras, etc I've found that installing usbmount or, if prefered, both pmount and hal to be simple and straight forward. 

The only advantage of pmount + hal over usbmount is that a desktop icon pops up on the desktop automatically when most devices are plugged in. Of course either can be done using synaptic or apt.

Also I've found ntfsprogs to be invaluable for extended capabilities of working with ntfs partitions. It's also available in the repos.

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

Of course the real beauty of Ubuntu is that there are almost always several ways of accomplishing the same goal and it all becomes a matter of personal preference. I love options :)

---

### Post by Joeb454 on 2008-06-09
I'm not sure how well ntfs-config works with External drives - as I've not got any to test it with :)

Though USB-Mount sounds like a good little app :) Not sure how it's directly relevant to mounting NTFS drives though ;)

---

### Post by Sally on 2008-06-10
I'm having a similar problem.

I have a Western Digital (My Book) external hard drive that I use for tons of media and doc storage. As of yesterday it was working, no problem. Today I can't see it at all. It was originally formatted on a windows machine and I tried plugging it in to a windows box (I have limited access to it so may not be able to try this again soon) and again, NOTHING.


I've tried a few different things including swapping out the usb cable, unplugging it, restarting ubuntu, etc. No dice. I also tried installing the NTFS Config tool and it doesn't see any drives mounted.

Other usb ports still work -- I can connect my iPod and it is recognized, etc -- so I'm really at a loss here.

Can anyone help?

---

### Post by Sally on 2008-06-10
ETA: Nothing worked, so I put the drive in the freezer for an hour. And now it's back! This doesn't make me feel very secure, though. 

Anyone know of a really reliable, tough external hd with a long lifespan? :)

---

### Post by Joeb454 on 2008-06-10
I'd take everything off that drive ASAP if you can ;)

Take it back to the shop if you can still get your money back or a different drive. If not - I can't recommend anything, as I've not currently got an external drive :)

---

### Post by 449 on 2008-06-10
> **Rixii said:**
> Thank you for this post but I am still having problems. With NTFS Config, it goes straight to the third thumbnail, I never see the second. (Using 7.10) Also, I can only select the external option (it's checked), but that should be what I need right? I'm trying to mount an external drive...

I had it removed properly from XP, and it shows up fine there. It doesn't appear to mount in Ubuntu but when I use the Sys Info tool it does show up. And in GPartition, it says it's unallocated?

It's a 250 GB Seagate drive, but it is almost full.. That wouldn't be a problem would it? I asked in the hardware forums last week but received no replies, can anyone help?

Try it through terminal. Here's what I did:

```
erik@erik-desktop:~$ ntfs-3g
ntfs-3g: No device is specified.
Please type 'ntfs-3g --help' for more information.
erik@erik-desktop:~$ ntfs-3g --help

ntfs-3g 1.2216 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2006-2008 Szabolcs Szakacsits
Copyright (C) 2005-2007 Yura Pakhuchiy

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro (read-only mount), force, remove_hiberfile, locale=,
          uid=, gid=, umask=, fmask=, dmask=, streams_interface=.
          Please see the details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force

Ntfs-3g news, support and information:  http://ntfs-3g.org

```

And this is the command I used to mount it:

```
ntfs-3g /dev/sda1 /media/windoze -o force
```


Now I have a question. How do I save it so I don't have to use the command everytime I want to mount it?

---

### Post by Sally on 2008-06-11
> **Joeb454 said:**
> I'd take everything off that drive ASAP if you can ;)

Take it back to the shop if you can still get your money back or a different drive. If not - I can't recommend anything, as I've not currently got an external drive :)

Yeah, I was only able to see the drive for a short time, now I'm back to not being able to see it under Ubuntu or Windows. 

Not sure what to do here. If I let it sit (or re-freeze the damn thing) what's my best bet for getting in long enough to repair it so it's (somewhat) stable so I can try and move those files?

(aaahhhh!)

---

### Post by medic2000 on 2008-06-12
"chkdsk /f DRIVE:" on an Windows system.

---

### Post by charstar on 2008-06-17
Thanks kansasnoob.  Installing pmount and it worked for me on 8.04.  I originaly installed xubuntu and automount was working, then i installed kde desktop and it stoped working, but this fixed it right away.

---

### Post by sosalini on 2008-07-16
Hello joeb 454 and all , Ive also had problems getting my external hard drive set up . I read what you wrote to help others and copied the instructions as best I could , and THINK  Ive managed to install the external hard drive . Ive wiped the windows xp off it at least , after managing to download my music etc to ubuntu . But the problem I have now is . Its telling me I have 70 odd gigabytes of unallocated space . Does that mean its all set up and I can use it to put files on in ubuntu , or do I have to do something else to format it to linux . AS it doesnt seem to appear anywhere except in gparted when I do a scan . How do I access it to put files on it ? 
Any help will be gratefully received .

---

### Post by money2themax on 2008-07-22
I'd thank you but i can't seem to find the thanks button

---

### Post by Joeb454 on 2008-07-22
@sosalini - try using the External Hard Drives option. I can't comment beyond that, as I don't have an External Drive

@Money2TheMax - the bottom right of each post :)

---

### Post by sosalini on 2008-07-24
Thank you all for your help ......again . i wasnt being unkind to cog and his advice to start a new thread , it was meant to be humour , ahhh the english humour , the comments were from a tv show called the fast show and harry enfield , being from the uk i thought cog would recognise them . no insult intended i promise . thank you all again .

---

### Post by diwas on 2008-07-28
I have a problem. I installed it correctly then executed it. Now, it doesnt show the sda5 partition, which is the one i need to mount automatically during startup. Furthermore when i try to mount through places>Music (Music is sda5, just changed the volume name), there is an error message "You are not priviledged to mount the volume 'Music'".
What is the problem? No, my hard disk is not external. Yes, it is one of the partition of the one and only Hard Drive I have. 

Thank you.

---

### Post by Joeb454 on 2008-07-28
Is the Music partition an NTFS partition?

Also, if it is, did you cleanly unmount the drive? If not it won't let you mount it :)

---

### Post by diwas on 2008-07-28
Oh well...may be the CLEAN UNMOUNT was the problem. Now it works fine. Thank you

---

### Post by Joeb454 on 2008-07-28
Ah glad it works. You have to cleanly unmount it before it will work.

Hopefully they'll be able to change this in future versions of ntfs-3g, and have it check the file system when you mount it :)

---

### Post by crtlbreak on 2008-07-30
Just a quick comment on this - my external USB 2.0 harddrive with NTFS partition was not unmounted properly from the windoze box when removed and would thus not mount in ubuntu when plugged in.
[-X
 There is obviously some file lock that indicates that the drive is still mounted to the windoze session. 
So advice is - remember to cleanly unmount from any OS before removal. :grin:

---

### Post by kjaggu on 2008-07-30
Thanks a lot for the tip :)

---

### Post by Joeb454 on 2008-07-30
I found earlier you *can* force mount the drive, though I wouldn't recommend it (obviously).

---

### Post by NWAdawg on 2008-08-22
Thank you for the post. I had no problems getting my NTFS backup drive to auto mount.\\:D/

---

### Post by Joeb454 on 2008-08-22
> **NWAdawg said:**
> Thank you for the post. I had no problems getting my NTFS backup drive to auto mount.\\:D/

Glad it worked for you :)

---

### Post by rolls on 2008-08-29
I gave this a go and it worked fine. I then restarted and it had mapped two of my drives two the same physical drive. I opened the utility hoping to have it let me reassign the mapping but it does not allow you to.

I unmounted all the drives and reinstalled the application, it still does not let me reset the mounting options.

Basically I have 3 NTFS drives which I want to all be auto mounted at boot. How can I achieve this?

---

### Post by Joeb454 on 2008-08-29
From what I'm aware, if you name the drives, they should all automount together just fine. I have XP and Vista (they both automounted on an old install I had) and they both worked fine.

Naming the Drives (maybe from Windows) may help

---

### Post by rolls on 2008-08-29
Hmm I just restarted a few times and now its fixed itself. Oh well

---

### Post by Joeb454 on 2008-08-29
Better than not fixing itself ;)

---

### Post by geezerone on 2008-09-11
Thanks for the 'how-to' JoeB :)

---

### Post by Joeb454 on 2008-09-11
> **geezerone said:**
> Thanks for the 'how-to' JoeB :)

It's quite alright :D

---

### Post by kaykav on 2008-10-03
thank you...not bad!!...Rich

---

### Post by (pr) on 2008-10-05
What should be the mount point for the nfts-partition? I can't press apply when I put in "/media/windows"

---

### Post by demios on 2008-10-05
> **Xiong Chiamiov said:**
> I've never had to do anything special to mount my NTFS partition.  I just have a line in my fstab:
```

/dev/sda4       /windows        ntfs    defaults,umask=007,gid=46,noatime   0       0

```
could you elaborate on what you did there? mostly, what each of the columns is for so I can try it -- never edited fstab before

---

### Post by Joeb454 on 2008-10-07
I've found that if the directory already exists, ntfs-config doesn't play nice, for example I manually mounted my windows partition to /media/Vista, THEN installed ntfs-config.

Turns out I had to remove the /media/Vista directory before it could continue.

Naturally, the directory name will be different for everybody I would assume :)

---

### Post by crazyness003 on 2008-10-27
I gave you a thanks down here because it wouldnt let me on the OP.

This app helped me stay away from getting my hands dirty with fstab- which generally is a bad thing to me. But since this computer is  the one that has to work "perfect" (its a family pc) then I have to do things safely.

Im gonna hack the crap outta my laptop tho.

Again thanks zillions.

Oh and a word of advice to some ppls out there, if you cant mount an NTFS drive, try [chkdsk /f]("http://www.ehow.com/how_2052292_run-chkdsk-f-windows-xp.html") in windows first. I did it twice on each drive (1: 300gb, 2:500gb so it took a while). But it was worth it. Now my drives run like...harddrives that run...i guess. And now they automount! w00t!!111one

Power to the People!

---

### Post by Joeb454 on 2008-10-28
> **crazyness003 said:**
> I gave you a thanks down here because it wouldnt let me on the OP.

This app helped me stay away from getting my hands dirty with fstab- which generally is a bad thing to me. But since this computer is  the one that has to work "perfect" (its a family pc) then I have to do things safely.

Im gonna hack the crap outta my laptop tho.

Again thanks zillions.

Oh and a word of advice to some ppls out there, if you cant mount an NTFS drive, try [chkdsk /f]("http://www.ehow.com/how_2052292_run-chkdsk-f-windows-xp.html") in windows first. I did it twice on each drive (1: 300gb, 2:500gb so it took a while). But it was worth it. Now my drives run like...harddrives that run...i guess. And now they automount! w00t!!111one

Power to the People!

Glad it helped you :)

---

### Post by Gustave on 2008-11-06
Thank you for this post.  I was trying to manually edit the fstab, and this does it all automatically, at startup, so it did what I needed!  Thanks!

---

### Post by Joeb454 on 2008-11-06
> **Gustave said:**
> Thank you for this post.  I was trying to manually edit the fstab, and this does it all automatically, at startup, so it did what I needed!  Thanks!

Thanks to this - I've never yet had to edit fstab :) That's why I love it :D

---

### Post by tvtech on 2008-11-08
Thanks for the help on this one, I was having a bit of trouble getting my uuid recognized in fstab, apparently I was getting ahead of myself on that front it, and should have just copied and pasted the mount location information direct from the properties dialog.  thanks again for this  easy tuts make life... well easy!

---

### Post by Joeb454 on 2008-11-08
Easy is the way forward ;) Either that or I'm lazy :p

---

### Post by 2hot6ft2 on 2008-12-01
Thanks Joeb454, I was looking for something to let me know if I had edited my fstab correctly before making it permanent until I found this thread. By the way NTFS-config is standard in ultimate edition 2.0.
:guitar:

And just to make it clear for others. The drive must be unmounted and if you created a folder in /media for it already you need to remove that folder first before using ntfs-config as it will try to create the folder.

---

### Post by Joeb454 on 2008-12-02
> **2hot6ft2 said:**
> Thanks Joeb454, I was looking for something to let me know if I had edited my fstab correctly before making it permanent until I found this thread. By the way NTFS-config is standard in ultimate edition 2.0.
:guitar:

Really? I've never used Ultimate Edition.

> **2hot6ft2 said:**
> 
And just to make it clear for others. The drive must be unmounted and if you created a folder in /media for it already you need to remove that folder first before using ntfs-config as it will try to create the folder.

Thanks for confirming, I wasn't sure whether it was just something I'd done on my system :p

---

### Post by cshaobui640990 on 2008-12-02
is [jordan shoes](http://www.b2bsneaker.com) good enough for play basketball?

---

### Post by darijan on 2008-12-04
thx man. verry easy way :)

---

### Post by herrBua on 2009-01-21
I didn't want to start another thread asking how to automount a fat32 internal drive so I thought it was best to reply to this one.

I have read the entire thread and I did the ntfs-config install and indeed, my ntfs partition is recognized, but my fat32 parition is not :S

I did have my HDD split up in my Win Vista install, then another partition (the fat32 partition) to make it easier for Linux distros to manipulate it and last but definitely not least my Ubuntu partition. So all my files (docs, music, vids...) are in my fat32 partition but I just can't automount it on startup :( which definitely sucks because some applications (including my player, Exaile) use that drive :S

I hope someone can help me out on this, I had it fixed in my last Ubuntu install, but I can't remember where I found the info, nor how to do it all :S

Oh, and while I'm at it... which one do you guys (and hopefully girls... xD) think is better: NTFS or fat32? I need it to be compatible with Windows since I still have it... mostly for gaming purposes and easier videocalls xD

---

### Post by Joeb454 on 2009-01-21
Now, I don't think there's any harm in using NTFS instead of FAT32, as ntfs-3g is pretty solid from what I've used of it.

Naturally, that would mean re-formatting your existing FAT32 partition, so here's a link I found with a quick search :)

[http://ubuntuforums.org/showthread.php?t=905929](http://ubuntuforums.org/showthread.php?t=905929)

That thread contains a link which should help you a bit further :)

---

### Post by dwieeb on 2009-01-21
I have 2 hard drives in my laptop. One (8-9 gigs) is for Ubuntu. The other (35-40 gigs) is for my pictures/music and personal files. It doesn't automount my second one. The second one doesn't have any operating system or anything on it at all, really. When I install NTFS Config it only discovers my first one (the one with Ubuntu). This is annoying because when I open up the music player it doesn't "find" my music on the second hard drive because its not even mounted. How can I automount this second hard drive when Ubuntu starts up?

---

### Post by Joeb454 on 2009-01-21
Is the 2nd hard drive NTFS formatted?

---

### Post by dwieeb on 2009-01-21
Filesystem type: ext3
Location: /media

I guess not. How can I format it to NTFS?

---

### Post by crazyness003 on 2009-01-21
Just wanted to drop this piece of info:
Disk Manager (disk-manager)
Can do what ntfs-config does and then some. It might do a fat32 auto-mount. So if anyone wants to give that a shot.
```
sudo apt-get install disk-manager
```
I think its in the Universe Repos.
It also lets you permanently do a -force on your drives every time they attempt to mount. Sometimes windows dosnt completely let got of your NTFS partitions, so this option was created to overcome this, BUT CORRUPTION CAN OCCUR (use at your own risk).

---

### Post by herrBua on 2009-01-21
hey, thanx for that program! it did work with vfat, just had to edit a little bit, but it works fine (at least this last boot it did, will report if it starts acting up)

umm, about the other problem, dwieeb, NTFS-config won't detect that partition because it is not NTFS formatted. ext3 (as far as I know :S) is native to linux so it should have no problem finding it.

Can u mount it manually?

---

### Post by dwieeb on 2009-01-22
Yes it mounts manually without problems.

---

### Post by crazyness003 on 2009-01-22
you need to manually edit fstab to get ext3 to auto-mount....or
use disk manager (it does it for you...automagically ^.^)

ntfs-config uses the ntfs-3g layer to auto-mount them. Without the -3g layer, you could only get it to work with something else like fuse (or whatever. i sound so smart, but i really am not).
Otherwise, even editing fstab would not yield results since you wouldnt even be able to manually mount it.

In the end. If you want no headach, use disk-manager.

if (you != headach){
    run disk-manager}
else{
    whatever, im trying to code in...dumba**
}

---

### Post by dwieeb on 2009-01-22
I installed disk-manager but I can't even find it in my menus.

---

### Post by crazyness003 on 2009-01-23
System-> Admministration -> Disk Manager
The icon looks like the on in this pic
[IMG]http://andregondim.eti.br/wp-content/uploads/2008/02/notify1.png[/IMG]


Or just Alt-F2 and type ```
gksu disk-manager
```

---

### Post by The_Rebel52 on 2009-01-23
[QUOTE="/etc/hal/fdi/policy/preferences.fdi"]<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<!--
  Some examples how to use hal fdi files for system preferences
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
<deviceinfo version="0.2">
<!--
  The following shows how to hint gnome-volume-manager and other programs
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->

  <device>
    <match key="storage.hotpluggable" bool="true">
      <match key="storage.removable" bool="true">
        <merge key="storage.automount_enabled_hint" type="bool">true</merge>
      </match>
    </match>
  </device>


</deviceinfo>
[/QUOTE]

Write this file and reboot, then enjoy.

---

### Post by g33k on 2009-02-06
Thanks for the tip!

---

### Post by eggy1962 on 2009-02-06
help.... another newbie here unable to get his ntfs external hard drive working
have ntfs config and ntfs -3g installed
i can see the hard drive in PLACES but it won't mount to allow me to access my mp3s which i want to add to the main hard  drive

---

### Post by The_Rebel52 on 2009-02-06
> **eggy1962 said:**
> help.... another newbie here unable to get his ntfs external hard drive working
have ntfs config and ntfs -3g installed
i can see the hard drive in PLACES but it won't mount to allow me to access my mp3s which i want to add to the main hard  drive

Have you tried what i have posted above?

All you have to do is "sudo gedit /etc/hal/fdi/policy/preferences.fdi" and paste in the quoted text(then reboot).

---

### Post by eggy1962 on 2009-02-06
ok this is what it said going to reboot now
?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<!-- 
  Some examples how to use hal fdi files for system preferences 
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
<deviceinfo version="0.2">
<!-- 
  The following shows how to hint gnome-volume-manager and other programs 
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->

  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>


</deviceinfo>

---

### Post by eggy1962 on 2009-02-06
didn'twork  still won't mount

---

### Post by eggy1962 on 2009-02-06
ok i'm off to bed here but if anyone else can advise....

---

### Post by eggy1962 on 2009-02-07
hello anybody out there to sort out my problem, please note i am a novice

---

### Post by The_Rebel52 on 2009-02-07
> **eggy1962 said:**
> ok this is what it said going to reboot now
?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<!-- 
  Some examples how to use hal fdi files for system preferences 
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
<deviceinfo version="0.2">
<!-- 
  The following shows how to hint gnome-volume-manager and other programs 
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->

  <device>
    <match key="storage.hotpluggable" bool="**false**">
      <match key="storage.removable" bool="**false**">
        <merge key="storage.automount_enabled_hint" type="bool">**false**</merge>
      </match>
    </match>
  </device>


</deviceinfo>

Just so were on the same page, you did change "false" to "true", correct?

---

### Post by eggy1962 on 2009-02-07
Hi all i did was copy the command from previous poster... this was the result, i have not "changed" it ... because i don't know how...if you  can walk me thru any steps i would be grateful... but it will have to wait till morning as its late here in uk and my eyes are drooping

i am very surprised tho that usb hard drives don't auto mount in ubuntu...not wishing to upset anyone here....my external hard drive was auto detected in pclinuxos
mark

---

### Post by The_Rebel52 on 2009-02-07
> **eggy1962 said:**
> Hi all i did was copy the command from previous poster... this was the result, i have not "changed" it ... because i don't know how...if you  can walk me thru any steps i would be grateful... but it will have to wait till morning as its late here in uk and my eyes are drooping

i am very surprised tho that usb hard drives don't auto mount in ubuntu...not wishing to upset anyone here....my external hard drive was auto detected in pclinuxos
mark

I guess it's try what they say.. the OS is only as good as the defaults.

Anywhozer, try pressing ALT + F2 to bring up the "run" dialog box then paste this into it and click/press enter "sudo gedit /etc/hal/fdi/policy/preferences.fdi" (without the quotes, also be sure to click "Run in terminal" checkbox).

That will open the text editor with root permissions so you can modify that system policy for hal.

---

### Post by eggy1962 on 2009-02-08
ok did as you advised 
repeated ealier command after restarting pc this is what i get
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<!-- 
  Some examples how to use hal fdi files for system preferences 
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
<deviceinfo version="0.2">
<!-- 
  The following shows how to hint gnome-volume-manager and other programs 
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->

  <device>
    <match key="storage.hotpluggable" bool="true">
      <match key="storage.removable" bool="true">
        <merge key="storage.automount_enabled_hint" type="bool">true</merge>
      </match>
    </match>
  </device>


</deviceinfo>

tried the external hard drive..... still will not mount... tho remains recognisable  in the places tab ie knows its an 80 gig

---

### Post by eggy1962 on 2009-02-08
my usb memory stick opens up fine, so it has to be something re ntfs recognition, have i missed anything? is there a command line  question i can ask of the system to see what is missing?

---

### Post by a_px on 2009-02-16
Hi,

I just bought a 1TB external USB drive which came formatted with NTFS. I reformatted this to ext3 & modified my fstab to attempt to automount at boot:

/dev/sdb1 /home/disk ext3 defaults,auto,rw 0 0


However fdisk -l gives:

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

Still says NTFS, although gparted says ext3. I couldn't get this drive to automount at boot, so I tried installing ntfs-config and enabling write support. Drive now auto-mounts no problem. Why should this be when the drive is ext3?

---

### Post by nicobeukes on 2009-03-23
thanks for the help on how to automount ntfs partitions,
it worked for a while and it even mounted my drives on the desktop,
now it still automounts if i click on places but my icons does not apeer on the desktop like it use to,
any ideas why my hdd icons have gone missing, the same applys to my usb drives

please help

---

### Post by Joeb454 on 2009-03-23
> **nicobeukes said:**
> thanks for the help on how to automount ntfs partitions,
it worked for a while and it even mounted my drives on the desktop,
now it still automounts if i click on places but my icons does not apeer on the desktop like it use to,
any ideas why my hdd icons have gone missing, the same applys to my usb drives

please help

Hit Alt+F2 and enter ```
gconf-editor
```

Once that has loaded up, you'll want to follow the menu's on the left down through apps > nautilus > desktop

Once you're there, you need to make sure "Show Volumes" is enabled :)

---

### Post by ktmom on 2009-03-23
Joeb454, thanks for the post.

---

### Post by Joeb454 on 2009-03-25
> **ktmom said:**
> Joeb454, thanks for the post.

No worries, I hope it helped

---

### Post by opendevlite on 2009-04-08
this is very useful

thanks

---

### Post by Andy06 on 2009-05-13
@crazyness003,

Do you have any idea what happened to the Disk manager program?
I was a big fan of it too and preferred it to NTFS config but I could not find it anywhere in the 9.04 repos after a new clean install. 

There is a pysdm (storage device manager) package that looks similar (icon+description) but with a different name and different GUI and functionality, is this a newer version?

Thanks

---

### Post by sathgarcia on 2009-05-13
try to have a look at this -> [http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

**sudo apt-get install pysdm** if the above help would help :D

---

### Post by whiteman on 2009-05-29
How do you mount the Vista drives on another computer in your network? I tried the ntfs..no dice. I have a Macbook pro..and it can "see" everybody. I can copy and paste from Ubuntu to the Vista. Anything. THE PROBLEM..My wife has a vista machine. She wants to save files to my external hardrive which is connected to my ubuntu desktop. I dont want her unplugging it all  the time. SHe wont unmount it. Too impatient. Just leave it alone! You..windoze user!. The windoze and the ubuntu are hardwired to dlink router. The Macbook is wireless. BTW I can see her drives, in fact she can print.(All printers connected to ubuntu)We all use CUPS. She has an external Passport that I am able to access. But She has this C,,C$, D$..f and F$ thing going. (F is the readable drive) WhenI click on one ofthe $ drives I amprompted for passwd, but it wont accept correct passwd. In my Samba shares..I have everybody allowed. There is no firewall. Does any of this make sense? She says.."Get rid of that dumb linux and put xp back on yer desktop. Never!

---

### Post by Rebelli0us on 2009-05-30
ok I did this so I could share my Thunderbird profile on my Windows partition. But now every time Ubuntu boots it does a "routine check of drives". How do I stop that?

I tried unmounting the volume but I get "You are not privileged to unmount the volume xxxxx".. "only root can do that". Who the heck is root? he better show up soon. Is this Linux's version of "contact your administrator".

---

### Post by Joeb454 on 2009-06-01
Does Ubuntu do a disk check every time you boot up? If not just allow it to do the disk check (I think the default is once every 25 boots), it doesn't take long :)

---

### Post by johnny_xie on 2009-06-04
Hi, everybody,

    I've installed Ubuntu 9.04 in my hard driver.( I have windows XP which has 4 ntfs patitions.) I create a new ext4 partition and a swap partition. 
    I installed ntfs-3g and ntfs-configure.But there are something strange.
    I can write files to NTFS partition ,but when I reboot to windows , the new writen file by Ubuntu disapeared~~~.
    I also check the fstab in my disk,it shows as follow:

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=47d793b1-d0ab-4e3f-bde5-776b2d6382cc / ext4 relatime,errors=remount-ro 0 1
# Entry for /dev/sda4 :
UUID=6bb7d22f-78d4-4782-9d6f-c09c5d8abd95 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda6 /media/Work ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/Softwares ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/System ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda7 /media/Games&others ntfs-3g defaults,locale=en_US.UTF-8 0 0


  It seems all the ntfs was well mounted. Why I lost all the file after reboot?

Thank you!

---

### Post by excbuntu on 2009-06-17
i'm confirming that the OP's method works on 9.04 Jaunty Jackalope.

---

### Post by Joeb454 on 2009-06-17
> **johnny_xie said:**
> Hi, everybody,

    I've installed Ubuntu 9.04 in my hard driver.( I have windows XP which has 4 ntfs patitions.) I create a new ext4 partition and a swap partition. 
    I installed ntfs-3g and ntfs-configure.But there are something strange.
    I can write files to NTFS partition ,but when I reboot to windows , the new writen file by Ubuntu disapeared~~~.
    I also check the fstab in my disk,it shows as follow:

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=47d793b1-d0ab-4e3f-bde5-776b2d6382cc / ext4 relatime,errors=remount-ro 0 1
# Entry for /dev/sda4 :
UUID=6bb7d22f-78d4-4782-9d6f-c09c5d8abd95 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda6 /media/Work ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/Softwares ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/System ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda7 /media/Games&others ntfs-3g defaults,locale=en_US.UTF-8 0 0


  It seems all the ntfs was well mounted. Why I lost all the file after reboot?

Thank you!

You mean if you write a file to your Windows partition from Ubuntu, and then reboot into Windows - the file is no longer present?

> **excbuntu said:**
> i'm confirming that the OP's method works on 9.04 Jaunty Jackalope.

Thank you :D Glad it still works

---

### Post by invaderchin on 2009-06-27
thanks! i had problems on the first attempt bcuz it never appeared on my Applications > System Tools menu. After a reboot, the 2nd attempt was successful!

---

### Post by Joeb454 on 2009-06-28
Ah I believe in Jaunty it moves to System > Administration

I'll have to check later when I'm at home and edit the original post :)

---

### Post by farroos on 2009-07-03
Thanks Joeb454
much better than manually editing text files.

Works like a charm.

---

### Post by emshains on 2009-07-03
Dude, exposing your public ip like that is just plain dangerous.

---

### Post by Joeb454 on 2009-07-04
> **emshains said:**
> Dude, exposing your public ip like that is just plain dangerous.

My IP's changed since then - but I had realised that at the time. I was just too lazy to change the images ;)

---

### Post by Melhisedek on 2009-07-07
Thanks a lot this worked great, but I wonder if it is possible to have drives showing on my Desktop on boot? Like they did after I mounted them before using ntfs-config...
Thank you for your time!

---

### Post by The MAX on 2009-07-09
this is a really clean automount. thanks. was wondering how to do this for a while.
Now I don't have to worry about Exaile crashing when I forget to mount my partition with all my music on it before I open it. :p

---

### Post by Joeb454 on 2009-07-09
> **Melhisedek said:**
> Thanks a lot this worked great, but I wonder if it is possible to have drives showing on my Desktop on boot? Like they did after I mounted them before using ntfs-config...
Thank you for your time!

How do you mean? I believe the default nautilus option is to show mounted drives on the desktop - if they're not mounted, they won't show.

> **The MAX said:**
> this is a really clean automount. thanks. was wondering how to do this for a while.
Now I don't have to worry about Exaile crashing when I forget to mount my partition with all my music on it before I open it. :p

That's almost the EXACT same reason I wrote the guide :)

---

### Post by Kastrasyon on 2009-07-10
Works great! Thanx for this very useful app.

---

### Post by Alabamian on 2009-07-19
Joeb454,

Tried your post and it worked perfectly, the firs time!  Man, Ubuntu 9.04 is SO cool!  The video comes to life in a way the previous versions just didn't have up to steam.  Thanks again for your exacting instructions and visuals.  Even a chimp should be able to figure this out.

Happily from the branches,

Alabamian

---

### Post by Joeb454 on 2009-07-20
Thanks for the feedback :) Glad to know it's still working as written.

I'll have to make sure to review it for 9.10 :)

---

### Post by oogmsn on 2009-07-21
wow thanks for the info! this saves alot of time for me & works perfectly! :)

---

### Post by supersaki on 2009-07-30
Thank you Joeb for the tip.  You've made it that much easier in the transition towards linux :)

---

### Post by Pierrot Lafouine on 2009-08-19
Hi
I tryed this:
```
sudo aptitude install ntfs-config
```
and give me this :
```
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  ntfs-config 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": n
Unrecognized input.  Enter either "Yes" or "No".
Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": No
Abort.

```
No one mention this in the complete thread, am I the only one to have this problem ?
Why do I have this ?

I'm using version 7.10.
Thanks

---

### Post by Joeb454 on 2009-08-19
It looks like it may be an unauthorized repository. Though I believe 7.10 reached EOL a few months ago, I could be wrong though

---

### Post by Pierrot Lafouine on 2009-08-19
ok
How can I get this app in an other repository ?
Thanks

---

### Post by Pierrot Lafouine on 2009-08-20
How can I get this app in an other repository ?
Thanks

---

### Post by probedb on 2009-08-20
Hi folks,

Another newbie here.

Question relates to automounting NTFS USB drives again but I do not have any GUI running.

Is there any way to automount when you just boot into the commandline?

When I plug a drive in it registers and I can manually mount it but I want to be able to automount them?

Any thoughts?

Cheers!

Paul.

---

### Post by guru1968 on 2009-08-27
@probedb:
you need autofs: sudo apt-get install autofs
this installs the automounter package; configuring is via /etc/auto.* scripts - look into them for additional information (they're well commented) or try "man autofs", it's quite straitforward...
 
@Joeb454:
I am also doing it the hard way - i.e. w/o GNOME, only commandline
- but I still did not succeed automounting ntfs drives/partitions!?
 normal ntfs-mounting works out of the box, but: I have an automounter entry where I successfully do auto-mount a remote nfs-filesystem; but when I try to automount a local ntfs partition it fails!?!?
 
could you please post the according (ntfs relevant) /etc/auto.* files here???
 
 
Thx,
guru

---

### Post by probedb on 2009-08-27
> **guru1968 said:**
> @probedb:
you need autofs: sudo apt-get install autofs
this installs the automounter package; configuring is via /etc/auto.* scripts - look into them for additional information (they're well commented) or try "man autofs", it's quite straitforward...
 

Cheers guru, will give it a go over the weekend :)

---

### Post by RaveJunkie on 2009-08-27
this was helpful to me when i started and i still use it.  I vote this should be added to the ubuntu mount info (non forum) and or this thread should be made a sticky.

thanks again     :KS

---

### Post by Joeb454 on 2009-08-28
You mean the mount info on the ubuntu wiki?

I may have a look at that page sometime soon

---

### Post by Matt Damon on 2009-09-07
Works great. Thanx Joeb454, i've been trying to figure this out for a while.

---

### Post by aaron424 on 2009-09-19
How did you get the sidebar with all the computer information?

---

### Post by Joeb454 on 2009-09-20
> **aaron424 said:**
> How did you get the sidebar with all the computer information?

It's an application called [conky]("apt://conky") - you can find a whole host of config files in [this thread]("http://ubuntuforums.org/showthread.php?t=281865") ;)

---

### Post by erictherev on 2009-10-07
Thanks Joeb454 for pointing us toward an extremely useful tool. Works like a charm!

btw... Nice conky.

---

### Post by Joeb454 on 2009-10-08
> **erictherev said:**
> btw... Nice conky.

Thanks :) I haven't got it set up anymore actually, I need to get it back, I still have the conkyrc somewhere :)

---

### Post by kevinguillorytraining on 2009-10-09
> **lecter255 said:**
> how about a FAT32 usb stick?

FAT32 USB Thumb drives should auto mount under ubuntu.

---

### Post by Renzo-M on 2009-10-11
Hey Joeb,
I used the ntfs-config thing the other day and I'm well satisfied but I accidently "configured" another partition that I don't want automounted, but I can't seem to find where or how to turn it off. Any help?

Note: "If this has already been asked before, I'm sorry, just don't have the time to read through all the pages atm."

Renzo-M

---

### Post by vchris on 2009-10-11
I did this on the wrong drive. How do I unmount the auto mounted drive? It says I don't have the privileges.

---

### Post by Alterkakker on 2009-10-29
Hello,

I tried your advice, perhaps my situation is a bit different.

My present desktop has a 60G HD with Ubuntu 9.04 running great.

The motherboard on another computer I had died and left me a 160G HD (Seagate Barracuda 7200, NTFS formatted). It has a SATA cable to hook to the motherboard, my motherboard (ASUS P3B-F) only has IDE. 

So I went to cooldrives.com and got a SATA to USB adapter for $20 that is supposed to let me plug the HD into a USB port and use it. When I try that, nothing pops up on my desktop like with all the other USB stuff - but when I go to the "Computer" folder I can see the drive, marked "USB Drive". When I right-click on it and choose "Mount volume", I get the error 'UNABLE TO MOUNT LOCATION (CAN'T MOUNT FILE). I am pretty new at all this so any help you or others can give in less-technical terms (I'm pretty good at typing commands into Terminal but can't "build" or "compile" anything yet). Thanks so much and sorry for the long post.

---

### Post by geezerone on 2009-10-29
Sounds like a pain!

Were you able to read NTFS filesystems before on your Ubuntu box?

If not you could try (from a terminal):

```
sudo apt-get install ntfs-3g
```ntfs-3g allows read/write access to NTFS filesystems.

If you have this can you output the ```
dmseg
``` file output for analysis?

---

### Post by Joeb454 on 2009-10-31
> **vchris said:**
> I did this on the wrong drive. How do I unmount the auto mounted drive? It says I don't have the privileges.

You probably need to use ```
sudo umount
``` to unmount, so you'll have root privileges to do it :)

> **geezerone said:**
> Sounds like a pain!

+1

Though as far as I'm aware, ntfs-3g is included as standard now. And you seem to have been given a less than helpful error, which sucks :( I'm not sure what that could be. As geezerone said, dmesg may help :)

---

### Post by emigrant on 2009-10-31
@ [[COLOR=#22550C]**Joeb454**[/COLOR]]("http://ubuntuforums.org/member.php?u=373057"), thanks for the tutorial.
btw, is'nt ntfs drives are by default automounted? atleast from jaunty?
or you mean this tute is for those who need to automount the ntfs drive for the non-sudoers?

sorry for my ignorance :(

---

### Post by Valis667 on 2009-10-31
Does anybody know why this doesn't work in 9.10? In both config and PySDM the options are greyed out. In config only the checkbox for external is available. I have an internal SATA drive for storage. Any help would be appreciated :)

---

### Post by StolenPie on 2009-11-01
I'm having a similar problem!
> You probably need to use  	Code:
 	sudo umount 
 to unmount

That's all very well... but how do I get it stop automounting? When I load up NTFS config, the drive in question isn't even listed!

---

### Post by StolenPie on 2009-11-01
sorry accidentally double-posted...

---

### Post by Temetka on 2009-11-02
Hai guys!

It's my first post here! 

So I just wanted to say thanks to the OP.

Your instructions on page 1 worked perfectly for me with no problems.

Much easier than editing my fstab file which I can do no problem, I was just looking for a lazier solution and you provided it. So thanks! :)

---

### Post by StolenPie on 2009-11-02
Managed to solve my problem!

I just did some basic googling... learned how to edit the fstab file.

Maybe it would be good to include these instructions in the original post... it's generally good to tell people how to undo the things they do right? Especially in such a popular post.

Run

```
cat /etc/fstab
```To view your drive mount settings.

For the automounting drive, mine looked like this:

```
/dev/sda1 /media/XP ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```In my system the ntfs drive is called "/dev/sda1", and /media/XP is the mount point.
Note that "defaults" implies that the drive will auto-mount. There might also be an "auto" command here which means the drive is auto-mounting. We need to change this so run:

```
gksudo gedit /etc/fstab
```Then edit the line so that "defaults" is accomanied by a "noauto" command, or that "auto" reads "noauto":

```
/dev/sda1 /media/XP ntfs-3g defaults,noauto,locale=en_GB.UTF-8 0 0
```Note that this fix means that in order to remount the drive you will have to use root priveliges in the terminal by running sudo mount.

Hope this helps anyone in my situation.

(This is my first time posting a solution on this website... take this as gratitude for all you Ubuntu masters have done for me! Kudos guys!)

---

### Post by Joeb454 on 2009-11-02
Thanks StolenPie! :D

I added that to the end of the first post :)

---

### Post by protector2020 on 2009-11-26
thanks, it's quite more convenient than "Places>Drive_Name (then password)" for listening all my music on a ntfs drive.

---

### Post by Joeb454 on 2009-11-27
> **protector2020 said:**
> thanks, it's quite more convenient than "Places>Drive_Name (then password)" for listening all my music on a ntfs drive.

That's the exact same reason I use it :)

---

### Post by tguh on 2009-11-30
Thanks mate. work flawlessly on my HP Mininote netbook with UNR 9.10 :)

---

### Post by TechMaven on 2009-12-01
That worked great. Program showed up in System>Administration.
Thx

---

### Post by webless on 2009-12-01
I used ntfs-config and have the drives mounting like I want them but I don't want them visible on the desktop. Is there any way to have them mounted but not visible on the desktop?

Les

---

### Post by manicnerd on 2009-12-03
> **webless said:**
> I used ntfs-config and have the drives mounting like I want them but I don't want them visible on the desktop. Is there any way to have them mounted but not visible on the desktop?

Les

the only way I know to not have them show up is to not have volumes be visible.

open terminal 
type 'gconf-editor'
under APPS - NAUTILUS - DESKTOP uncheck volumes_visible and they should disappear

---

### Post by Goth Mneph on 2009-12-06
Here is the quick fix.

-System/administration/disk utility

-click on the drive you want and manage it.

simple, really

ya gotta love Ubuntu once you figure out how simple they've made it.

---

### Post by nuffy on 2010-01-16
I tried the NTFS config install and all went well....until I went to use NTFS to mount /dev/sdb1 /media/Cranks 1 - 320.

I ticked the Add check box, hit Apply and was greeted with this error message...

Error : An error has occurred when configuring
 /media/Cranks 1 - 320, please retry.

So I went to Places>Cranks 1 320 and clicked on the drive and was greeted with and Authentication window to entered my password, clicked the button and the drive was mounted.

What I want to know is how do I do away with the Authenication window so the mounting happens when the pc starts?

Since I added this post I found that sudo ntfsfix /dev/sdb1 may shed some light on my problem.... it successfully completed it's task, but now I don't have an option in NTFS Config to mount the drive...

Am I in trouble?

---

### Post by Methanoid on 2010-01-21
Is there a way to do this without a Gnome desktop? 

I have a minimal install (ie no desktop) with XBMC running on a small SATA drive but want I have a E-SATA 1.5Tb drive full of media which is NTFS formatted. Be a right pain to have to shift it onto other HDDs and then reformat back to EXT3. 

I'm totally confused by all this create a directory called NTFSDRiveName in /mnt and editting /etc/fstab

I don't know what to put it etc/fstab to get it to work and make it auto mount WITHOUT these nice desktop tools. I know I need ntfs-3g (installed) and I want to read/write to the drive

Help me Obi-Wan you're my only hope !! :popcorn:

---

### Post by paulqueen on 2010-01-26
thanks very very very very very very much.  this helped immensely.  i was trying much more difficult configurations that all failed on me.. thanks again

---

### Post by Geraba on 2010-02-04
The ntfs-config package worked quite well... Thanks!

I would like to know WHAT makes it work... I checked the fstab file after setting ntfs-config up, then I noticed the line it added was something that I already tried, but Nautilus couldn't mount it anyway...

What does this tool do? What else it changes?

---

### Post by mo.mashi on 2010-03-03
> **lecter255 said:**
> but can you mount external drives though? i can mount NTFS partitions in my internal hard drive too, no problem, but I can't use my usb key or external hard drive.
I've just done exactly that on an external Sata drive following Xiong Chiamiov's instructions. I'm running Karmic Koala (Kubuntu). The main thing that I did differently from Xiong was put in the UUID number of the partition I wanted to mount instead of /dev/sda3 (as the /dev/ reference tends to change frequently and the UUID is permanent and is unique to each partition):

UUID=387C4E017C4DBB00 /home/fadi/External ntfs  defaults,umask=007,gid=46,noatime   0       0

you can get the UUID number by opening up gparted, right clicking on the partion of interest and selecting information.

I like this technique over the ntfs-config b/c I have more control over the directory my partition mounts in...

---

### Post by bfckarlos on 2010-04-02
OP

Thank you - worked a treat, had been looking at this for a while.

;)

---

### Post by The MAX on 2010-04-04
> **StolenPie said:**
> Managed to solve my problem!

I just did some basic googling... learned how to edit the fstab file.

Maybe it would be good to include these instructions in the original post... it's generally good to tell people how to undo the things they do right? Especially in such a popular post.

Run

```
cat /etc/fstab
```To view your drive mount settings.

For the automounting drive, mine looked like this:

```
/dev/sda1 /media/XP ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```In my system the ntfs drive is called "/dev/sda1", and /media/XP is the mount point.
Note that "defaults" implies that the drive will auto-mount. There might also be an "auto" command here which means the drive is auto-mounting. We need to change this so run:

```
gksudo gedit /etc/fstab
```Then edit the line so that "defaults" is accomanied by a "noauto" command, or that "auto" reads "noauto":

```
/dev/sda1 /media/XP ntfs-3g defaults,noauto,locale=en_GB.UTF-8 0 0
```Note that this fix means that in order to remount the drive you will have to use root priveliges in the terminal by running sudo mount.

Hope this helps anyone in my situation.

(This is my first time posting a solution on this website... take this as gratitude for all you Ubuntu masters have done for me! Kudos guys!)

This isn't an okay solution for me. This is a workaround. 
I recently installed the 10.04 beta, and for some reason ntfs-config seemed a bit figity when first setting it up. I must have accidentally set all my partitions to auto mount WHICH I DO NOT WANT. I also do not want to have to open a terminal and run a root command every time I need to look into a partition for some reason. Uninstalling ntfs-config changed nothing.

Thanks for the workaround stolenpie, but Joeb454 it would be really nice if you told me what ntfs-config did to auto mount those partitions so I can undo it, becuase it is not in /etc/fstab as far as I can tell. Thanks.

---

### Post by The MAX on 2010-04-04
Okay I think I may have fixed this bungle.

**If you accidentally set partitions to automount that you did not want, or want to uninstall ntfs-config and revert the automounting here is what I did**

After accidentally setting all my partitions to automount I checked my /etc/fstab 

```
cat /etc/fstab
```

and it looked like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda2 :
UUID=61ad19aa-716d-4db4-9b82-f974309cbe62	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=D0788FBB788F9EBA	/media/Backup	ntfs	defaults,noauto,nls=utf8,umask=0222	0	0
#Entry for /dev/sda4 :
UUID=3E048EFD048EB803	/media/Data	ntfs-3g	defaults,locale=en_CA.utf8	0	0
#Entry for /dev/sdc1 :
UUID=90A0C899A0C88766	/media/System_Reserved	ntfs	defaults,noauto,nls=utf8,umask=0222	0	0
#Entry for /dev/sdc2 :
UUID=4A32CEDC32CECBDF	/media/Windows7 	ntfs	defaults,noauto,nls=utf8,umask=0222   	0	0
#Entry for /dev/sda1 :
UUID=C2001A9B001A970F	/media/WindowsXP	ntfs	defaults,noauto,nls=utf8,umask=0222	0	0
#Entry for /dev/sda3 :
UUID=abdfa495-f8a5-4098-9f8b-a3a343fde90e	none	swap	sw	0	0


```

Now a [previous solution]("http://ubuntuforums.org/showpost.php?p=8221939&postcount=139") was to just put the option "noauto" in all of the drives you don't want mounting on startup. HOWEVER, this requires that if you do want to mount it, rather on just clicking on the drive in the "Places" menu, you have to open a terminal and mount them MANUALLY as ROOT. This did not seem like a pleasant or convenient solution for me. So after a little bit of playing and a little reading of the fstab wiki I tried a couple of things, but here is what seemed to work.

```
hughie@Green-Lantern:~$ cd /etc
hughie@Green-Lantern:/etc$ ls |grep "fstab"
fstab
fstab-ntfs-config-save

```

there are two files there. The file fstab-ntfs-config-save appears to be a backup that ntfs-config makes upon rewriting fstab. Mine looked like this

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=61ad19aa-716d-4db4-9b82-f974309cbe62 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=abdfa495-f8a5-4098-9f8b-a3a343fde90e none            swap    sw              0       0
```

So it only contained my original Linux and Swap partitions.

rename your current fstab to fstab.OLD or something to keep it just in case. 

```
sudo mv fstab fstab.OLD
```

then you can restore your old fstab

```
sudo cp fstab-ntfs-config-save fstab
```

you can then re-run ntfs-config if you wish to try and automount partitions again, or learn how to write your fstab file to do it.

I only wanted to automount the partition called "Data" so now my fstab looks like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda2 :
UUID=61ad19aa-716d-4db4-9b82-f974309cbe62	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda4 :
UUID=3E048EFD048EB803	/media/Data	ntfs-3g	defaults,locale=en_CA.utf8	0	0
#Entry for /dev/sda3 :
UUID=abdfa495-f8a5-4098-9f8b-a3a343fde90e	none	swap	sw	0	0


```

Hope this helps.

---

### Post by SOS2 on 2010-05-19
After staking time to go through this long thread ...I think that all solutions presented here are not practical in terms of manually  manipulating core configurations.

The following solution is very easy.. straight foward ..does not require any modification on system configuration level or cause any future unsuitability issues.

First : 
install the The gnome-mount package contains programs for mounting, unmounting and ejecting storage devices. either using terminal 
```
sudo apt-get install gnome-mount
```Or using menu:
system > administration > synaptic 

Second:
After installation go to :
System > preferences > startup applications 
Click "Add"
in the command filed enter :
```
gnome-mount -p Data
```Where "Data" is the label for the drive you need to Automount at login.
enter what ever you want in the "name" and "Description" fields 
Click "Save" button and Your Done!!!

You can mount any number of drives using the same method.
If you wish to remove the Auto mount for this drive just remove the command from the startup applications list.

Enjoy !!!
 
:popcorn:

---

### Post by Fox Dark Master on 2010-05-28
Hello everyone :)
You all seem to have some problems because all partitions are automatically mounted, mine is the opposite. Instead of mounting the ntfs, everitime i reebot i have to first go to nautilus and click on the disk i want and open it. it's a bit inconvenient since it's the partition i have my dropbox folder and everytime the computer stars i have to login and set where the folder should be.

This only happens with my netbook with UNR 10.04. In normal cases i use the ntfs-config program but i can't run it on the netbook. Here's the output if i try to run it on the console:
[INDENT]foxdarkmaster@minimini:~$ sudo ntfs-config
Traceback (most recent call last):
  File "/usr/bin/ntfs-config", line 102, in <module>
    main(args, opts)
  File "/usr/bin/ntfs-config", line 75, in main
    app = NtfsConfig()
  File "/usr/lib/pymodules/python2.6/NtfsConfig/NtfsConfig.py", line 56, in __init__
    os.mkdir(HAL_CONFIG_DIR)
OSError: [Errno 2] Ficheiro ou directoria inexistente( translation: file or directory non-existent ): '/etc/hal/fdi/policy'
[/INDENT]
My netbook is a asus eeepc 1000HE. I'd appreciate if you could lend a hand :)

---

### Post by Fox Dark Master on 2010-06-04
Just to say i'e solved the problem :) i had to uninstall every package labed NTFS on software center application, restart and then install again the main packages.

---

### Post by JPS77 on 2010-09-20
hi i want to mount an ext4 volume, it just dosent mount. can u pleeez help????

---

### Post by The MAX on 2010-09-20
well first you can try to mount it manually.

Do an fdisk -l command as sudo user to see what that partition is called (ex: /dev/sda1 ) and then try to mount it using the mount command (ex: sudo mount /dev/sda1 /mount/myext4 ). The mount location has to be created before hand however. unmount using the umount command.

If that works, then you should be able to edit the fstab file to auto mount it. Check the fstab page on wikipedia.

---

### Post by JPS77 on 2010-09-20
Dude thanks helping but that did not work
here is what it says
> ubuntu@ubuntu:~$ sudo mount /dev/sda6 /media
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


presently just need files that are on the partition, actually i have kubuntu installed on it. Kubuntu now boots into BusyBox which i don't know how to use.
Now the partition dosent mount at all... i think it is because it wasnt unmounted properly...
Thanks for helping

---

### Post by Joeb454 on 2010-09-20
Is the NTFS partition a Windows installation? If so, try booting into that, defrag & clean shutdown, see if that makes a difference.

Unfortunately, that's the only thing I can think of currently

---

### Post by JPS77 on 2010-09-21
Joeb454,
That was an ext4 partition with kubuntu installed on it

---

### Post by Joeb454 on 2010-09-21
What I meant was, what is the NTFS partition for? Is it simply a storage partition, or does the NTFS partition have Windows installed on it?

---

### Post by JPS77 on 2010-09-21
hi,
I'm a newbie............. I can't understand what you're trying to tell me...
sorry

i started a thread [http://ubuntuforums.org/showthread.php?t=1578257]("http://ubuntuforums.org/showthread.php?t=1578257")

i've put the bootscript out there...
i don't understand much of it but i think you sure will

thanks
JPS

---

### Post by JPS77 on 2010-09-22
Thank God it worked

Thanks gusy 4 helping

---

### Post by majedaly on 2010-10-23
> **Xiong Chiamiov said:**
> I've never had to do anything special to mount my NTFS partition.  I just have a line in my fstab:
```

/dev/sda4       /windows        ntfs    defaults,umask=007,gid=46,noatime   0       0

```
Honestly, I like this solution better. Worked well for me without the need to install anything

---

### Post by NITROCARIO on 2010-12-28
In Ubuntu 10.10 the commands given are not supported:

sudo aptitude update
sudo aptitude install ntfs-config

So instead type these commands:

sudo apt-get update
sudo apt-get install ntfs-config

And the installed software will be available under the tabs **System > Administration > NTFS Configuration Tool**

Rest of the process goes as is stated above :D

---

### Post by Joeb454 on 2010-12-29
Thanks. I updated the first post to reflect that. It's also worth noting that you could also run ```
sudo apt-get install aptitude
``` which would then make the initial post valid still :p

---

### Post by rpete on 2011-01-13
Hi, I've read through a lot of the posts above but can't automount.  sudo fdisk -l shows sdb1, there is a directory for it in media/usb, I have the latest ntfs-3g application, and can't figure out how to see my external hard drive icon on the desktop and access the files in it. I am using an Acer Aspire One with 10.10 netbook remix OS.  The drive is immediately mounted and pops up on the desktop on my other computer with 10.04.  

Does anything look wrong with the output below?



richard@richard-AO532h:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a4a5f639-e587-4300-8afb-4ea4e9ffc30a none            swap    sw              0       0

---

### Post by facelikebambi on 2011-01-17
> **Joeb454 said:**
> I've found that if the directory already exists, ntfs-config doesn't play nice, for example I manually mounted my windows partition to /media/Vista, THEN installed ntfs-config.

Turns out I had to remove the /media/Vista directory before it could continue.

Naturally, the directory name will be different for everybody I would assume :)

Ah that might explain why when I run ntfs-config and enter the password, it just closes instantly. I already have a NTFS drive that mounts at /media/Storage (though not automatically!).

I'm a noob though and don't know how to "remove the directory" without breaking something. Any advice?

Thanks

---

### Post by Joeb454 on 2011-01-19
It depends how you manually mounted it. If you haven't edited /etc/fstab then you should just be able to run ```
sudo rmdir /media/Storage
``` while the drive **isn't** mounted.

---

### Post by Joeb454 on 2011-01-19
It depends how you manually mounted it. If you haven't edited /etc/fstab then you should just be able to run ```
sudo rmdir /media/Storage
``` while the drive **isn't** mounted.

---

### Post by federal_topone on 2011-01-23
i'll try it first.. thanks

---

### Post by naelya on 2011-01-29
Hello Joeb454,

I have 64bit Ubuntu 10.10
I followed your advice however the NTFS-Config "enable write support for internal device" is greyed out and not enabled.

sudo fdisk -l

returns the following:


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b77a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         498     3998720   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2             499        2988    19998721    5  Extended
/dev/sda3            2988       60802   464387072    b  W95 FAT32
/dev/sda5             499        2988    19998720   83  Linux


It is /dev/sda3 is the device I wish to automount.

Your help is appreciated,

Regards.

---

### Post by Morbius1 on 2011-01-29
>  I followed your advice however the NTFS-Config "enable write support for internal device" is greyed out and not enabled.That's the thing I find most spooky about ntfs-config. It asks you if you want to enable write support for ntfs. Ntfs has had write support by default for about 3 years now so I'm not sure what its doing if you select "yes".

Anyway in your particular case you have no ntfs partitions so it doesn't matter if it's grayed out.

The following procedure is just an example:

Make a permanent home for your partition:
```
sudo mkdir /media/Data
```Edit fstab as root:
```
gksu gedit /etc/fstab
```Add the following line at the end of fstab:
```
/dev/sda3 /media/Data vfat utf8,umask=007,uid=1000,gid=46 0 1
```Save fstab and back in the terminal run the following command to test for errors and mount the new partition:
```
sudo mount -a
```

---

### Post by Morbius1 on 2011-01-29
Joeb454, a thousand apologies. It's early here ( that's my excuse anyway ) and I had no idea I was posting in a HowTo. I consider that quite rude and I wouldn't have done it if I wasn't so feeble minded. Feel free to remove it.

---

### Post by Joeb454 on 2011-01-29
No apologies needed - it was a helpful post, and I have nothing against people helping out if they know the answer :)

---

### Post by RottNKorpse on 2011-02-01
thank you very much for this HowTo....exactly what I was looking for.

**Edit:** this still does exactly what I wanted but it has one slight bug with network shared folders after mounting.

The bug is fairly easy to solve though so not to worry.

I originally manually mounted these drives and then shared some folders through Samba. This worked just fine and even after unmounting and remounting the shared folders continue to work just fine over the network. However, once I installed ntfs-config the folders were no longer seen over the network as permissions/ownership had been altered. So here is what I did to fix that.

1. Press Alt+F2 (run dialog) or open a terminal
2. Run the following:
```
gksu gedit /etc/samba/smb.conf
```3. Enter your root password. gedit will need root access to edit this file.
4. Add the below line to the [global] section of Global Settings.
```
usershare owner only = false
```3. Save and exit.

[[IMG]http://visuex.com/images/share/smb-conf-ntfs-config-fix-th.png[/IMG]]("http://visuex.com/images/share/smb-conf-ntfs-config-fix.png")

Hope this helps anyone else who runs into this issue.

---

### Post by XBMC old School on 2011-02-01
> **RottNKorpse said:**
> thank you very much for this HowTo....exactly what I was looking for.

**Edit:** this still does exactly what I wanted but it has one slight bug with network shared folders after mounting.

The bug is fairly easy to solve though so not to worry.

I originally manually mounted these drives and then shared some folders through Samba. This worked just fine and even after unmounting and remounting the shared folders continue to work just fine over the network. However, once I installed ntfs-config the folders were no longer seen over the network as permissions/ownership had been altered. So here is what I did to fix that.

1. Press Alt+F2 (run dialog) or open a terminal
2. Run the following:
```
gksu gedit /etc/samba/smb.conf
```3. Enter your root password. gedit will need root access to edit this file.
4. Add the below line to the [global] section of Global Settings.
```
usershare owner only = false
```3. Save and exit.

[[IMG]http://visuex.com/images/share/smb-conf-ntfs-config-fix-th.png[/IMG]]("http://visuex.com/images/share/smb-conf-ntfs-config-fix.png")

Hope this helps anyone else who runs into this issue.

Sweet Fix. But how do you enable read/write & remove passwords.

---

### Post by RottNKorpse on 2011-02-01
> **XBMC old School said:**
> Sweet Fix. But how do you enable read/write & remove passwords.
I am not exactly sure what issues you are having as I would need much more detail but what I think your issue is that you need to make your SambaShare saved the login password when you connect to it. Be sure to click "Remember forever":
[IMG]http://visuex.com/images/share/smb-samba-remember-pass.png[/IMG]


As for the write permissions...you will need to add write permissions in NTFS-Config:

[IMG]http://visuex.com/images/share/smb-ntfs-config-settings.png[/IMG]


You also need to make sure that Write access is activated for the SambaShare from the original sharing computer:

[IMG]http://visuex.com/images/share/smb-my-music-samba.png[/IMG]

Hope this helps...

---

### Post by junnitta on 2011-02-09
@Joeb454
Hi I want to add something about NTFS configuration tool. There is a bug that NTFS Configuration Tool won't launch after installing it on ubuntu 10.10 maverick (I don't know this problem arises on all 10.10 but I had it and when googled about it there were other people facing it.) There is a bug report on launchpad about it on here.

[https://bugs.launchpad.net/ntfs-config/+bug/630348](https://bugs.launchpad.net/ntfs-config/+bug/630348)

I am just copynig the important part from that bug report below in case someone needs it
[quote=MD Ashraful Alam]ntfs-config was previously dependent on libhal. They removed hal dependency from lucid. But the dependency residue is still in the maverick package. You can either install libhal or you can just make an empty directory as "/etc/hal/

fdi/policy". Then ntfs-config will work. well it worked for me.[/quote]

Maybe you should add a note or at least the bug link about this bug because it very favourable to use NTFS Configuration Tool since it is simple and easy. Many people (mee included) would tend to automount NTFS drives with it. And when searched in google this topic is at top or among top results so it would help lots of people knowing that when reading how to automount even before they install ntfs-config.
Thanks for this topic bytheway.

---

### Post by nilsnh on 2011-04-03
Thank you for posting this! Was dreading the fact having to trawl the net for some kind of solution, but luckily I happened upon your simple walkthrough. :)

---

### Post by Utrader on 2011-06-14
Hi,

I need help to create an "auto install" (at boot or after login) for the "ntfs-config" package everytime I start Ubuntu 11.04.

I have install it on 11.04 and it works fine but I have to "activate" it everytime I start the pc and that is very annoying. So it would be perfect if someone could tell me how to do so that "install" itself during upstart or after login if that is easier?

I'm a complete newbe so a step-by-step instruction would be much appreciated!
 
After alot of searching on the net have I found this 'instructions' but as I wrote earlier I'm a newbe so I don't know if this is will work in Ubuntu 11.04 or at all?
======================
sudo apt-get -y install ntfs-3g
 
After doing this substitute ntfs-3g for ntfs in your fstab file.
 
/dev/hda1       /media/windows ntfs-3g  defaults  0   0
 
You will now have read/write access when you login.
(source: [http://www.stchman.com/part.html](http://www.stchman.com/part.html))

======================


Many thanks for your help!

---

### Post by Paschalis89 on 2011-07-31
I put my solution also.Maybe works for somebody.

**Story: **I have a 400GB internal disk. In two partitions. Main and Data.
In main, i have Win7 and ubuntu 10.10 installed.
On other disk, "data", which is NTFS, i store all my downloads, and i have a common dropbox place, in which both Win7 and Ubuntu sync.

Every reboot in Ubuntu, dropbox had problems, because my "data" disc wasnt auto-mounted!




**[SIZE="3"]WHAT I DID:[/SIZE]**

1) Got root acces with sudo -s ..

2) typed: blkid
and got result:

```
/dev/loop0: UUID="4c09fa42-ee6f-447e-8e48-0cc75c663a2b" TYPE="ext4" 
/dev/sda1: LABEL="WinRE" UUID="FECA075BCA071017" TYPE="ntfs" 
/dev/sda2: LABEL="System Reserved" UUID="52AA90E9AA90CB3D" TYPE="ntfs" 
/dev/sda3: UUID="30B6986CB6983476" TYPE="ntfs" 
[COLOR="Red"]/dev/sda5[/COLOR]: LABEL="[COLOR="Navy"]DATA[/COLOR]" UUID="01CC4EC64E397020" TYPE="ntfs"
```

and because when data is mounted, is at [COLOR="Lime"]/media/DATA[/COLOR]

3) i edited: /etc/fstab
and added the following line at bottom:
[COLOR="Red"]/dev/sda5[/COLOR] [COLOR="lime"]/media/DATA[/COLOR] ntfs-3g defaults,locale=en_US.utf8 0 0



_Info:_ To find all locale availiable on your ubuntu, type: locale -a

It worked like charm! :) Hope somebody get's helped from this! :KS
Dont be responsible if doesnt work for anybody else.
Dont even know if this can harm your system, so dont blame me!

---

### Post by phidia on 2011-08-16
What a charm :p  after trying the steps here my system (10.4) won't boot normally-it's boots to cli but I can get gui--it's just that now it wants to boot to the commandline and I still can't mount my usb ntfs drive.

I give up!

---

### Post by swapii on 2011-11-08
hey     I have installed       ntfs-config tool      n did sm settings....
bt     nw  itz giving an error       that     [B]"Unable to mount location..
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda8 on /media/Media"[/B]
now        what to do???

---

### Post by mastapat11 on 2011-12-27
> **swapii said:**
> hey     I have installed       ntfs-config tool      n did sm settings....
bt     nw  itz giving an error       that     [B]"Unable to mount location..
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda8 on /media/Media"[/B]
now        what to do???

what command did u run? looks like u need 'sudo' in front of that command to get it working.
also what ver of ubu u on?

---

