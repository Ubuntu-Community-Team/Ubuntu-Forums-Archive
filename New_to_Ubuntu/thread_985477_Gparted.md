---
title: "Gparted"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by TheJoke on 2008-11-17
I installed it but how do i Move the stuff to the right or left to grow or expand.

Can i get pictures too, i need some visuals.

---

### Post by Gepetto on 2008-11-17
You won't be able to do it through the program built into gnome, you have to boot into it separatly. Grab it from [http://gparted.sourceforge.net/download.php]("http://gparted.sourceforge.net/download.php"), burn it to a disk, and boot from it. Everything should be pretty simple from there

---

### Post by TheJoke on 2008-11-17
So i should just do install? I don't have to extract it?

---

### Post by jenkinbr on 2008-11-17
> **Gepetto said:**
> You won't be able to do it through the program built into gnome, you have to boot into it separatly. Grab it from [http://gparted.sourceforge.net/download.php]("http://gparted.sourceforge.net/download.php"), burn it to a disk, and boot from it. Everything should be pretty simple from there
That really depends on what drive is being formatted.  If the filesystem to be resized is not system-critical, such as a volume mounted at media, it will work fine.  However, if it is a system-critical partition you want to work on, you will have to unmount it, which means that you can't do it from ubuntu.

The link above should have some nice visuals.

btw, Download the liveCD version.

---

### Post by Gepetto on 2008-11-17
Get the gparted-live-0.3.9-4.iso file and burn it to a CD, and boot into it the same way you booted into the Ubuntu CD the first time. No need to install, it runs straight from the CD

---

### Post by kernelhaxor on 2008-11-17
You cannot format/resize disks when they are mounted.  So you need to unmount disks you want to format/resize them.

You cannot unmount your primary partition.  So if you want to resize that, you will have to download and burn the Gparted iso onto a disk (its bootable), so when you boot using that disk, you can make changes to any disk attached to your system.

---

### Post by TheJoke on 2008-11-17
Thanks, i'll tell you guys how it goes.

---

### Post by TheJoke on 2008-11-17
Guys, something happened. I downloaded it and i directly Burnt it to the Disc without doing anything. I then restarted the computer and Gparted did not start.

Advice?

---

### Post by TheJoke on 2008-11-17
Help?

---

### Post by kernelhaxor on 2008-11-17
You burnt the disk from the ISO image right? not the ISO as a file on the disk?
Can u check ur BIOS to see if the CD comes above hard disk in your boot order?

---

### Post by Squonk07 on 2008-11-17
> **TheJoke said:**
> Guys, something happened. I downloaded it and i directly Burnt it to the Disc without doing anything. I then restarted the computer and Gparted did not start.

Advice?

Did you adjust the boot order so that the computer boots from the disc?  By default, most computers will boot from the hard drive, ignoring removable media.  When you first turn the computer on there should be a screen splash of some sort.  At the bottom (the top? somewhere, at least) there should be instructions on accessing the boot order by pressing a specific key (every system is different).  If all goes well, a DOS-like selection screen will come up, at which point you can use the UP/DOWN arrow keys to select the disc drive, and then click ENTER.

Of course you could have already done this and gotten nowhere, in which case forgive me for giving you the step-by-step tutorial. :)

> **kernelhaxor said:**
> You burnt the disk from the ISO image right? not the ISO as a file on the disk?
Can u check ur BIOS to see if the CD comes above hard disk in your boot order?

You beat me to it. :)

---

### Post by TheJoke on 2008-11-17
> **kernelhaxor said:**
> You burnt the disk from the ISO image right? not the ISO as a file on the disk?
Can u check ur BIOS to see if the CD comes above hard disk in your boot order?

Wait what do you mean? If i did nothing and installed it, should it just install the ISO. or should i open it and Find something?

I set the BIOS for CD-ROM.

---

### Post by TheJoke on 2008-11-17
Please do i have to open the Gparted package?

---

### Post by Squonk07 on 2008-11-17
> **TheJoke said:**
> Please do i have to open the Gparted package?

I've never used the Gparted standalone utility, only the one that comes with the Ubuntu LiveCDs (Do you still have one of these? You can boot it instead of the Gparted standalone and use the Gparted program that comes with the LiveCD.).  However, the way I understand it, it's a bootable ISO, which means you just need to boot from the disc drive in which you put the disc and the program should start without having to navigate the disc or anything.

If I'm horribly wrong, I apologize, and I'm sure somebody will set you (and me) straight. :)

---

### Post by TheJoke on 2008-11-17
> **Squonk07 said:**
> I've never used the Gparted standalone utility, only the one that comes with the Ubuntu LiveCDs (Do you still have one of these? You can boot it instead of the Gparted standalone and use the Gparted program that comes with the LiveCD.).  However, the way I understand it, it's a bootable ISO, which means you just need to boot from the disc drive in which you put the disc and the program should start without having to navigate the disc or anything.

If I'm horribly wrong, I apologize, and I'm sure somebody will set you (and me) straight. :)

I know, But what i've been asking is that if i have to Extract the file and burn it or just leave it and burn it or do something else.

---

### Post by Squonk07 on 2008-11-17
> **TheJoke said:**
> I know, But what i've been asking is that if i have to Extract the file and burn it or just leave it and burn it or do something else.

You should be able to just burn the ISO directly to disc (using Brasero or similar).  If it's compressed (in a ZIP or TAR file), go ahead and extract it first.

---

### Post by TheJoke on 2008-11-17
If i extract it. It looks like it opens the folder and i can't install.

---

### Post by kansasnoob on 2008-11-17
Whoa! Slow down!

If you have an Ubuntu live CD there is no need to burn a Gparted Live CD. In fact I've found the Gparted live Cd's to be much more "fiddly" as far as getting things to a workable screen resolution, etc.

You can boot any Ubuntu Live CD (at least since 7.10) and go to System > Administration > Partition Editor, and that is Gparted!

But I'd like to know what you want to do. Do you already have Ubuntu installed?

---

### Post by TheJoke on 2008-11-17
> **kansasnoob said:**
> Whoa! Slow down!

If you have an Ubuntu live CD there is no need to burn a Gparted Live CD. In fact I've found the Gparted live Cd's to be much more "fiddly" as far as getting things to a workable screen resolution, etc.

You can boot any Ubuntu Live CD (at least since 7.10) and go to System > Administration > Partition Editor, and that is Gparted!

But I'd like to know what you want to do. Do you already have Ubuntu installed?

Yes i have it installed and Vista was deleted somehow. Right now i have to free up space to install vista again so i'm tried to use the LiveCD for it but it says i should move a bar to the left or right and i don't see a bar. I asked for pics but i was told i need the live CD for important partions.

---

### Post by Squonk07 on 2008-11-17
> **kansasnoob said:**
> Whoa! Slow down!

If you have an Ubuntu live CD there is no need to burn a Gparted Live CD. In fact I've found the Gparted live Cd's to be much more "fiddly" as far as getting things to a workable screen resolution, etc.

You can boot any Ubuntu Live CD (at least since 7.10) and go to System > Administration > Partition Editor, and that is Gparted!

But I'd like to know what you want to do. Do you already have Ubuntu installed?

Beat me to the punch again!  (I'm slow today)  I agree; I've never used the standalone Gparted.  The version on the Ubuntu Live CD is just fine.  In any case, if you use either the version that comes with Ubuntu or the standalone one, then you don't need to install anything in Ubuntu itself.

EDIT: If you had Vista installed already but it got deleted, shouldn't you already have the space on the drive where Vista used to be?  Or did Vista get deleted when you installed Ubuntu?

---

### Post by TheJoke on 2008-11-17
> **Squonk07 said:**
> Beat me to the punch again!  (I'm slow today)  I agree; I've never used the standalone Gparted.  The version on the Ubuntu Live CD is just fine.  In any case, if you use either the version that comes with Ubuntu or the standalone one, then you don't need to install anything in Ubuntu itself.

But what about that bar? Can i get a picture or a detailed explanation on how to use it?

And i thought you couldn't edit primary partitions on a mounted disk or something?

Ubanutu holds my whole Drive, i think it overwrited or something. I don't know.

---

### Post by Squonk07 on 2008-11-17
> **TheJoke said:**
> But what about that bar? Can i get a picture or a detailed explanation on how to use it?

And i thought you couldn't edit primary partitions on a mounted disk or something?

If you're using an OS that is located in a mounted drive (e.g. Ubuntu), then you can't edit the partition in which that OS is installed because it's mounted (you're using it).  You need to get outside of it, hence the Live CD version of Gparted.

I think I know what you're talking about with the bar.  As part of the Ubuntu setup process (when you booted the Ubuntu Live CD), there was a screen with options on where to install the OS.  There would have been a graphic at the top with a sliding bar, and radio buttons for "Guided" and "Manual" partition formatting.

---

### Post by TheJoke on 2008-11-17
> **Squonk07 said:**
> If you're using an OS that is located in a mounted drive (e.g. Ubuntu), then you can't edit the partition in which that OS is installed because it's mounted (you're using it).  You need to get outside of it, hence the Live CD version of Gparted.

I think I know what you're talking about with the bar.  As part of the Ubuntu setup process (when you booted the Ubuntu Live CD), there was a screen with options on where to install the OS.  There would have been a graphic at the top with a sliding bar, and radio buttons for "Guided" and "Manual" partition formatting.

So there should be an options screen that says that stuff in the live CD?

---

### Post by kansasnoob on 2008-11-17
> **TheJoke said:**
> Yes i have it installed and Vista was deleted somehow. Right now i have to free up space to install vista again so i'm tried to use the LiveCD for it but it says i should move a bar to the left or right and i don't see a bar. I asked for pics but i was told i need the live CD for important partions.

OK! That's what I needed to know!

In Ubuntu go to Accesories > Terminal and "copy-n-paste" this command:

```
sudo fdisk -l
```

That is a lower case L! Not a 1 (one)!

---

### Post by TheJoke on 2008-11-17
> **kansasnoob said:**
> OK! That's what I needed to know!

In Ubuntu go to Accesories > Terminal and "copy-n-paste" this command:

```
sudo fdisk -l
```

That is a lower case L! Not a 1 (one)!

This showed up. 


Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         805     6464512    6  FAT16
Partition 1 does not end on cylinder boundary.
/dev/sda2             806       30401   237729870    5  Extended
/dev/sda5           30073       30401     2642661   82  Linux swap / Solaris
/dev/sda6             806       29743   232444422   83  Linux
/dev/sda7           29744       30072     2642661   82  Linux swap / Solaris



What should i do now?

---

### Post by TheJoke on 2008-11-17
Help?

---

### Post by jenkinbr on 2008-11-17
I'm sure that this is what is ment by the bar for resizeing partitions:
[IMG]http://www.rasyid.net/wp-content/uploads/2008/06/parted2.png[/IMG]

However, what good are screenshots if you don't get gparted up and running.

Insert your Ubuntu installation CD into your CD-rom Drive and reboot.
The ubuntu installation menu should come up and present it's options to you.

choose "try ubuntu without installing" (or whatever it says...)

wait....for it to load....

go to "system -> Administration -> partition editor".

Select the drive in the list to the far right (defaults to /dev/sda)
Select the partition that you want to resize, then right-click it and select "resize partition"

drag the right facing arrow to the left until you have your desired balance in size (note that vista is a pig, so give it plenty of room to get nice and fat...at least 10-15 GB or 10240 - 15360 MB

Click OK and Apply Changes when you are ready to do so.

[color=#ff0000]**_BE VERY CAREFUL WITH THE ABOVE!!!!_**[/color]  Changing partitions can ruin your filesystem, and backups are STRONGLY advised.

Hope this helps to some extent.

---

### Post by TheJoke on 2008-11-17
> **jenkinbr said:**
> I'm sure that this is what is ment by the bar for resizeing partitions:
[IMG]http://www.rasyid.net/wp-content/uploads/2008/06/parted2.png[/IMG]

However, what good are screenshots if you don't get gparted up and running.

Insert your Ubuntu installation CD into your CD-rom Drive and reboot.
The ubuntu installation menu should come up and present it's options to you.

choose "try ubuntu without installing" (or whatever it says...)

wait....for it to load....

go to "system -> Administration -> partition editor".

Select the drive in the list to the far right (defaults to /dev/sda)
Select the partition that you want to resize, then right-click it and select "resize partition"

drag the right facing arrow to the left until you have your desired balance in size (note that vista is a pig, so give it plenty of room to get nice and fat...at least 10-15 GB or 10240 - 15360 MB

Click OK and Apply Changes when you are ready to do so.

[color=#ff0000]**_BE VERY CAREFUL WITH THE ABOVE!!!!_**[/color]  Changing partitions can ruin your filesystem, and backups are STRONGLY advised.

Hope this helps to some extent.


Thanks for the advice. Do i move the yellow or just move the arrows.

---

### Post by kansasnoob on 2008-11-17
> **TheJoke said:**
> This showed up. 


Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         805     6464512    6  FAT16
Partition 1 does not end on cylinder boundary.
/dev/sda2             806       30401   237729870    5  Extended
/dev/sda5           30073       30401     2642661   82  Linux swap / Solaris
/dev/sda6             806       29743   232444422   83  Linux
/dev/sda7           29744       30072     2642661   82  Linux swap / Solaris



What should i do now?

As you suspected Windows is gone but you also have a bit of a mess. It appears you have two Linux operating systems in play. Please go back to terminal and:

```
sudo apt-get install gparted
```

Then go to System > Administration > Partition Editor just to take a screenshot.

If you're not sure how to do that go to Applications > Accessories > Screenshot. It should be saved to desktop by default. Then click the "paper clip" thingy here on the forum page and select desktop > screenshot, etc.

I hope I explained that well enough:confused:

Like here's mine:

[ATTACH]93073[/ATTACH]

---

### Post by kansasnoob on 2008-11-17
> **jenkinbr said:**
> I'm sure that this is what is ment by the bar for resizeing partitions:
[IMG]http://www.rasyid.net/wp-content/uploads/2008/06/parted2.png[/IMG]

However, what good are screenshots if you don't get gparted up and running.

Insert your Ubuntu installation CD into your CD-rom Drive and reboot.
The ubuntu installation menu should come up and present it's options to you.

choose "try ubuntu without installing" (or whatever it says...)

wait....for it to load....

go to "system -> Administration -> partition editor".

Select the drive in the list to the far right (defaults to /dev/sda)
Select the partition that you want to resize, then right-click it and select "resize partition"

drag the right facing arrow to the left until you have your desired balance in size (note that vista is a pig, so give it plenty of room to get nice and fat...at least 10-15 GB or 10240 - 15360 MB

Click OK and Apply Changes when you are ready to do so.

[color=#ff0000]**_BE VERY CAREFUL WITH THE ABOVE!!!!_**[/color]  Changing partitions can ruin your filesystem, and backups are STRONGLY advised.

Hope this helps to some extent.

Sorry to be the turd in the punch bowl but let's figure out exactly what the OP wants!

Like, let me do this, OK?

---

### Post by TheJoke on 2008-11-17
> **kansasnoob said:**
> As you suspected Windows is gone but you also have a bit of a mess. It appears you have two Linux operating systems in play. Please go back to terminal and:

```
sudo apt-get install gparted
```

Then go to System > Administration > Partition Editor just to take a screenshot.

If you're not sure how to do that go to Applications > Accessories > Screenshot. It should be saved to desktop by default. Then click the "paper clip" thingy here on the forum page and select desktop > screenshot, etc.

I hope I explained that well enough:confused:

Like here's mine:

[ATTACH]93073[/ATTACH]


So i'll just load up the CD and do it. I'll then post it.

---

### Post by kansasnoob on 2008-11-17
> **kansasnoob said:**
> Sorry to be the turd in the punch bowl but let's figure out exactly what the OP wants!

Like, let me do this, OK?

I hope that didn't sound bad! It just get's confusing when too many people are firing off ideas!

You may well be better at this than I am!

Apologies if I sound cranky! I'm a cranky old man1

---

### Post by kansasnoob on 2008-11-17
> **TheJoke said:**
> So i'll just load up the CD and do it. I'll then post it.

NO! You're not paying attention! Do that from yyour instaled Ubuntu!

---

### Post by jenkinbr on 2008-11-17
> **kansasnoob said:**
> Sorry to be the turd in the punch bowl but let's figure out exactly what the OP wants!

Like, let me do this, OK?

Go for it - couldn't delete the post and I posted it after yours.

---

### Post by kansasnoob on 2008-11-17
> **jenkinbr said:**
> Go for it - couldn't delete the post and I posted it after yours.

That's cool! I just see someone really lost, and I've been there!

---

### Post by Squonk07 on 2008-11-17
> **TheJoke said:**
> Thanks for the advice. Do i move the yellow or just move the arrows.

The yellow represents the amount of the partition that is already in use.  For example, if you have a 10 GB drive and the yellow extends to about half of the rectangle, then there is about 5 GB of data already on the partition.  Making the partition smaller than the amount of space than is already in use (e.g. smaller than 5 GB) would be destructive, and if I remember correctly Gparted will not even allow you to do this.

Also, for future reference, if you ever resize a Windows partition, make sure to **defragment the drive first**.  Windows is boneheaded and often places data right at the end of the partition, so if you resize it that data might be destroyed, rendering the OS unbootable.  Just a heads up.

It might be better to just type in the size you want.  Take the partition you want to resize, and subtract the amount of space you want to shrink it by from the total size (e.g. if you have a 10 GB, or 10240 MB, partition and want to shrink it to 9 GB, subtract 1024 MB, or 1 GB, from the 10240 MB, and make this result the new size of the partition).  Then form a new partition in the unallocated space.  Vista uses NTFS.

As noted, Vista is a hog and needs a lot of space.  And, as also noted, be very careful when you edit partitions.  I've done this sort of thing many times in the past, and I only screwed it up once.  I was left with a totally unbootable system and I had to start all over from a blank slate.  Luckily I was newly setting up the system anyway, so I just had to start all over.

EDIT:

> **kansasnoob said:**
> Sorry to be the turd in the punch bowl but let's figure out exactly what the OP wants!

Like, let me do this, OK?

Point taken.  I understand; it's like the old saying about too many cooks in the kitchen.  Have fun, and good luck! :)

---

### Post by karlr42 on 2008-11-17
The OP has formatted her whole disk and it's all Ubuntu. She wants to shrink the Ubuntu partition to install Vista on the resulting free space.
To do so, she would need to use 
a)the live CD Gparted iso.
b)the ubuntu live cd,which had gparted.

---

### Post by TheJoke on 2008-11-17
> **Squonk07 said:**
> The yellow represents the amount of the partition that is already in use.  For example, if you have a 10 GB drive and the yellow extends to about half of the rectangle, then there is about 5 GB of data already on the partition.  Making the partition smaller than the amount of space than is already in use (e.g. smaller than 5 GB) would be destructive, and if I remember correctly Gparted will not even allow you to do this.

Also, for future reference, if you ever resize a Windows partition, make sure to **defragment the drive first**.  Windows is boneheaded and often places data right at the end of the partition, so if you resize it that data might be destroyed, rendering the OS unbootable.  Just a heads up.

It might be better to just type in the size you want.  Take the partition you want to resize, and subtract the amount of space you want to shrink it by from the total size (e.g. if you have a 10 GB, or 10240 MB, partition and want to shrink it to 9 GB, subtract 1024 MB, or 1 GB, from the 10240 MB, and make this result the new size of the partition).  Then form a new partition in the unallocated space.  Vista uses NTFS.

As noted, Vista is a hog and needs a lot of space.  And, as also noted, be very careful when you edit partitions.  I've done this sort of thing many times in the past, and I only screwed it up once.  I was left with a totally unbootable system and I had to start all over from a blank slate.  Luckily I was newly setting up the system anyway, so I just had to start all over.

Ok thanks i'll try it.

> **kansasnoob said:**
> NO! You're not paying attention! Do that from yyour instaled Ubuntu!


I can't use the partion from  Ubantu, It is only on the Live CD.

Would formating my hardive and starting over work?

---

### Post by Squonk07 on 2008-11-17
> **karlr42 said:**
> The OP has formatted her whole disk and it's all Ubuntu. She wants to shrink the Ubuntu partition to install Vista on the resulting free space.
To do so, she would need to use 
a)the live CD Gparted iso.
b)the ubuntu live cd,which had gparted.

It's not quite that simple, as noted above:

> **kansasnoob said:**
> As you suspected Windows is gone but you also have a bit of a mess. It appears you have two Linux operating systems in play. Please go back to terminal and:

```
sudo apt-get install gparted
```

Then go to System > Administration > Partition Editor just to take a screenshot.

If you're not sure how to do that go to Applications > Accessories > Screenshot. It should be saved to desktop by default. Then click the "paper clip" thingy here on the forum page and select desktop > screenshot, etc.

I hope I explained that well enough:confused:

Like here's mine:

[ATTACH]93073[/ATTACH]

I think kansasnoob has this one down.  Let's watch the man work. :)

---

### Post by TheJoke on 2008-11-17
The forum won't let me upload the forum?

Should is just tell you whats on it?

---

### Post by kansasnoob on 2008-11-17
> **TheJoke said:**
> The forum won't let me upload the forum?

Should is just tell you whats on it?

Are you currently running Ubuntu? If so is it from the Live Cd or from a mounted drive? And is it from the computer we're working on?

---

### Post by TheJoke on 2008-11-17
Yes. I installed Ubantu so i guess it's mounted. Yea it's from the computer.

---

### Post by kansasnoob on 2008-11-17
> **TheJoke said:**
> Yes. I installed Ubantu so i guess it's mounted. Yea it's from the computer.

Did you do this from terminal:

```
sudo apt-get install gparted
```

And if so just open System > Administration > Partition Editor and then go to Accessories > Screenshot and save it to desktop?

If so you should be able to click the "paper clip" thingy and post it here.

---

### Post by kansasnoob on 2008-11-17
Well, I guess I killed this thread unintentionally!

My point was that your fdisk -l already showed two Linux OS's. Unless that was intentional then someone has tried to install twice.

Now you want to install Vista!

That requires knowing where to install it!!

If it were simple this would work:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by Squonk07 on 2008-11-17
> **kansasnoob said:**
> Well, I guess I killed this thread unintentionally!

My point was that your fdisk -l already showed two Linux OS's. Unless that was intentional then someone has tried to install twice.

Now you want to install Vista!

That requires knowing where to install it!!

If it were simple this would work:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

It happens to the best of us.  Remember, this stuff can be really complicated, especially to a new user.  Looking at your post count, you've definitely got some experience. :)

Looking over this whole thread, it might be simpler for the OP to just start from scratch again.  After all, with Windows blitzed and the double installation of Linux, there's not much to lose.  Plus, it's easier to install Linux after a Windows OS is on the computer than to do it the other way around.

BTW, this whole mess is why I never use anything but the Manual option for creating and organizing disk partitions whenever I install Ubuntu.  A little more complicated, especially for a new user, but it offers a lot more control and, to me at least, is somewhat more intuitive (i.e. I know exactly what the installer will do and I have granular control over everything).

To the OP, don't give up!  The Ubuntu community is one of the most helpful and knowledgeable tech forums anywhere, and I'm sure that the community can get you up and running again.

---

### Post by kansasnoob on 2008-11-17
> **Squonk07 said:**
> It happens to the best of us.  Remember, this stuff can be really complicated, especially to a new user.  Looking at your post count, you've definitely got some experience. :)

Looking over this whole thread, it might be simpler for the OP to just start from scratch again.  After all, with Windows blitzed and the double installation of Linux, there's not much to lose.  Plus, it's easier to install Linux after a Windows OS is on the computer than to do it the other way around.

BTW, this whole mess is why I never use anything but the Manual option for creating and organizing disk partitions whenever I install Ubuntu.  A little more complicated, especially for a new user, but it offers a lot more control and, to me at least, is somewhat more intuitive (i.e. I know exactly what the installer will do and I have granular control over everything).

To the OP, don't give up!  The Ubuntu community is one of the most helpful and knowledgeable tech forums anywhere, and I'm sure that the community can get you up and running again.

You're exactly right! 100%!

The OP was getting a lot of info about downloading gparted, but almost none about what's really going on!

---

