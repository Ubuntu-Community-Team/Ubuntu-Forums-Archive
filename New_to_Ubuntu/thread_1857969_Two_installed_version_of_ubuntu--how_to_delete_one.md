---
title: "Two installed version of ubuntu--how to delete one?"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by woollyworm on 2011-10-11
I have tried to google this, and the answers I'm finding either don't apply to me (wrong windows os) or the answer assumes that the poster knows certain things.

I installed ubuntu 11.04 on a netbook that had a questionable harddrive.  I liked it, but then the computer completely crashed on me.

While I was trying to find a new laptop, I read up on Ubuntu and convinced myself that 10.04 would be better because it had long term support.  So, when I get my new Dell mini, I download and install 10.04, but I didn't care for it, b/c it couldn't detect the wi-fi.  It was prompting me to type in the SSID and other stuff.  I remembered that the 11.04 detected the wi-fi and connected really easy.

So, I went and downloaded 11.04 and installed it.  I assumed that b/c it was a more recent version, it would overwrite the other ubuntu installation.  

I installed the ubuntu from a thumb drive and had it installed alongside my windows 7.

however, whenever I turn the computer on, the screen shows both versions of ubuntu along with the windows.  How do I delete the 10.04?

Some results I found when googling will be specific about some things, but then they'll say, "Delete the partition."  I don't know how to do that.  Any answer I get will have to be real specific on how to do things like that.

I want to keep the 11.04, just delete the 10.04.  And I want to keep the windows 7 if for any reason I have need of a program that won't run in Ubuntu.

Thanks in advance.

---

### Post by Elfy on 2011-10-11
Hi , if you boot with the version of ubuntu that you wish to keep and run mount or df -h then the drive that is marked as / is the one you DO NOT want to delete

you can find the other with fdisk probably.

It's possible that you have more than one swap as well. 

If you're not sure which - then post the information from the following here and someone will help you.

You will though I suspect need to do this from a live environment - boot with your livecd/usb

Run these and post the results here.

```
mount
sudo fdisk -l
cat /etc/fstab
```

Please use code tags.

---

### Post by woollyworm on 2011-10-11
OK, I did not understand a word of that.  I'm a complete noob.  Where am I supposed to type those commands?  In windows?  Or in ubuntu?  Because if it's in ubuntu, I don't know how to get to a command prompt.  That's why I need real specific directions.

---

### Post by fantab on 2011-10-11
> **woollyworm said:**
> I want to keep the 11.04, just delete the 10.04.  And I want to keep the windows 7 if for any reason I have need of a program that won't run in Ubuntu.



[LIST=1]
[*] **BackUp** all your important data.
[*]**Install GPatred** from the Software Center. Or download an .ISO image of Gparted from [**here**]("http://gparted.sourceforge.net/livecd.php"), burn it to a CD or USB and boot (recommended).
[*]Run GParted then locate and select the disk-Partition on which Ubuntu 10.04 is installed.
[*]**Delete** that Partition **OR** just **Format** it to either NTFS, to be used with Windows or Ext4, to be used as linux partition.
[*]From the Terminal run this: ***sudo update-grub***
[/LIST]
That should do. If you need more help take a screen-shot of the GParted showing your disk partition scheme and post here.

---

### Post by Elfy on 2011-10-11
To open a terminal

Ctrl+Alt+T

Paste the commands in to the terminal.

Sudo will need your password - it will not show as you type it, this is normal.

If both the installs are in the extended partition you'll not be able to do post #4 until you do so from a livecd or whatever you installed from.


mount - this will tell us what partitions are currentl mounted
sudo fdisk -l - this will tell us what partitions you have
cat /etc/fstab - this will tell us what partitions are set to mount when you boot

---

### Post by woollyworm on 2011-10-11
Thanks for the info on how to open a terminal.  I actually like typing in commands.  I used to do quite a few things in DOS, but that was way back when it was windows 3.1.  Once things started taking off with windows 95 then 98 and all the rest, I just lost interest, b/c I don't have the personality type to want to keep up with something that's so fast moving.  I think it might be cool to learn linux, but I should probably take a class, otherwise, I won't be motivated to study.

Anyway, how do I take screen shots so I can post them?

---

### Post by Elfy on 2011-10-11
prtscrn button works :)

though if you've run the commands - better to paste them.

You can easily copy - open a new post, select the text - go to the post and middle click - should paste it all

Not any good for a picture though of course.

---

### Post by woollyworm on 2011-10-11
Update:

Ok, it appears I have 8 partitions.
1 says Dell utility
2 and 3 are NTFS, which is windows, right?
4 says extended (whatever that means)
5 and 6 are Linux and Linux swap/solaris
and 7 and 8 are linux and Linux swap/solaris

when I do the df -h it brings up partition 7.  So 7 and 8 are for the 11.04, I'm assuming, which makes sense, since I installed it last.  

I also downloaded the partition editor mentioned above.

So, what's the next step?

---

### Post by Elfy on 2011-10-11
Boot with the livecd - then remove the partitions you don't need - you should be able to resize to use up that now freed space.

Check and check again that you're removing the right ones :)

Once you've done that and rebooted - open a terminal and run 

sudo update-grub

That will remove the other ubunu from the boot list.

As said before - backup important data.

Don't run gparted on a laptop that's running on battery, don't assume that gparted has hung if it appears to not be doing anything.

---

### Post by woollyworm on 2011-10-11
Ok, just to be clear before I do anything...

When I boot up with the thumb drive in, I should run it off the drive like I did when I was trying it out before I installed it?

And then once I'm running off the drive, I should run the partition editor (with it plugged into the wall)?

And then bring up the terminal and do the grub command?

Also, I just wanted to say thank you very much to everyone who replied.  I like how willing to help you all are, and I also liked how you didn't want to insult my intelligence.  I practically had to beg you to go ahead and insult me, cuz I know nothing.  :-)

---

### Post by Elfy on 2011-10-11
yep - choose - try ubuntu - or if you have the gparted disc then it will boot to that

then run the partition editor 

then you need to reboot and then run the grub command

---

### Post by woollyworm on 2011-10-11
Is there a reason why i can't just run the partition editor from ubuntu proper?  Why do I have to be running off the disk?  As long as I know which partition to delete, why does it matter?

---

### Post by -kg- on 2011-10-12
Woolyworm does have a point, and it might be a bit safer.  You can't perform partitioning operations on a mounted partition, and the partitions 11.04 are installed in will be mounted.  The 10.04 partitions won't be.  There would be no mistaking which partitions are which and editing the wrong ones.  Then he would already be in the installation and would be able to run the "update-grub" command.

You can also reformat the partitions from there, if you desire.  If you don't have much space on your drive (or in your 11.04 partition), I would just delete those partitions (I'd delete the extra swap partition in any case...you only need one) and expand your "/" (root) partition into the free space.  That, you will have to do from the Live CD.  As I've already said, you can't do partitioning operations on a mounted partition.

Do a little reading at the link in my signature block.  It will give you some idea of what you're doing.

Another caveat...

Some time back I was doing some experimenting.  When you delete logical partitions, the partition designations for logical partitions following those you delete will change.  In your case, sda7 and sda8 would become sda5 and sda6.  That's not at all acceptable, because you would have to change settings in GRUB to point to those partition numbers (I've had that experience and trashed an installation).

In your situation, if you want to reclaim the space taken up by the other partitions, it might be best to format and then shrink those partitions to as small as you possibly can, moving them over all the way to the left.  Then you preserve your partition designations and have the vast majority of free space in which to expand your sda7 partition.

That, or you'll have to correct your GRUB bootloader, which can be a PITA.  I'd rather someone confirm this, though.

---

### Post by Elfy on 2011-10-12
You can do that assuming that none of the partitions you are using are in extended partition along with the not used ones.

But they are - > 4 says extended (whatever that means)
5 and 6 are Linux and Linux swap/solaris
and 7 and 8 are linux and Linux swap/solaris

To work in the extended you'll need to unmount it - to do that you'll need to unmount the partition you are booting as well.

---

### Post by -kg- on 2011-10-12
OK, my Kubuntu installation is on my second hard drive (sdb).  The entire drive is an extended partition with several logical drives.  Kubuntu is on sdb10 and sdb8.

What you said didn't sound right according to my experience, so I ran an experiment.  I have an old OpenSUSE installation on sdb9 and I have successfully resized it from the installation within the same extended partition.  Apparently you don't need to unmount all the logical partitions...just the ones you're going to do operations on.

The only time you would need to unmount all logical partitions in an extended partition is if you're performing an operation on the extended partition itself.

Now I'm going back and putting sdb9 back the way it was.

---

### Post by Elfy on 2011-10-12
Thanks for experimenting - something new to me that is (not the experimenting the extended partition thing) 

It's likely though that this would have morphed into a "now how do I get the unused space to be used" 

ty -kg- :)

Edit - just had a go on an exisiting unused partition in extended - nice one to be aware of.

---

### Post by woollyworm on 2011-10-13
Hmm, this is starting to sound complicated.  I think I'll just do it from the install disk.  Either that or just leave the dang thing the way it is.  :-)  I didn't realize I had to have a degree in computer science to free myself from microsoft and google.

---

### Post by -kg- on 2011-10-13
> **woollyworm said:**
> I didn't realize I had to have a degree in computer science to free myself from microsoft and google.

You don't, but as with everything, there ***is*** a learning curve. I had heavy computer experience, in more OSes than Windows (MSDOS, Amiga DOS, OS/2, BeOS, etc.) when I came on board.  You should have seen me! ](*,)

Along with a lot to learn, there is a lot to ***_un_learn!*** ;)

---

