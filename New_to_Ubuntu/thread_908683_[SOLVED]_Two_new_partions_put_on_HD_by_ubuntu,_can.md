---
title: "[SOLVED] Two new partions put on HD by ubuntu, can I format them safely?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Tyler Zambori on 2008-09-02
hi all,

I just installed ubuntu hardy heron to my system, as a
windows/ubuntu dual boot system.  It installed fine, 
but it created two new partitions on my hard drive. 
They are unformatted.  Since I cannot see any ubuntu
files on my C and D drives (C for windows, D for programs)
I don't know if it's safe to go ahead and format these
two additional partitions in windows so that I can use 
this HD space.  It's a huge amount. 

Is it safe?

---

### Post by ByteJuggler on 2008-09-02
No those partitions are likely your Ubuntu partitions.  It only looks "unformatted" to Windows since Windows can't read Linux partitions by default.   I suggest you boot into Ubuntu, install "gparted" (Partition Editor) if needed, then use it to view your partitions instead.  (Go to System->Administration->Partition Editor.)

---

### Post by Vadi on 2008-09-02
Ubuntu creates a swap partition and a normal partition. It needs both to operate, and yes, chances are Windows didn't recognize them properly.

---

### Post by Tyler Zambori on 2008-09-02
Thanks guys.  I guess it doesn't matter because I'm planning
to add another HD anyway, but ubuntu didn't give me the option
to tell it how much of the HD it could take. 

Also, as far as I can tell, even after installing gparted,
I can't see these partitions.  It shows the D drive, 
and a 32 gb media drive (why??), so I dunno, I guess I will 
leave it until my ubuntu books arrive.

---

### Post by ByteJuggler on 2008-09-02
> **Tyler Zambori said:**
> Thanks guys.  I guess it doesn't matter because I'm planning
to add another HD anyway, but ubuntu didn't give me the option
to tell it how much of the HD it could take. 

Also, as far as I can tell, even after installing gparted,
I can't see these partitions.  It shows the D drive, 
and a 32 gb media drive (why??), so I dunno, I guess I will 
leave it until my ubuntu books arrive.

What are you seeing?  Can you post a screenshot of your gparted?  Alternatively, open a terminal (Applications->Accessories->Terminal), then copy and paste the following command into the terminal at the command prompt, and press enter (do not type it to help prevent errors):
```
sudo fdisk -lu >/tmp/fdisk.txt && gedit /tmp/fdisk.txt
```
It will ask for your password, enter it when prompted.  Then some information will be opened in an editor.  Copy and paste that here, or attach the file.  This will list all the partitions on your system in textual form.

---

### Post by Tyler Zambori on 2008-09-03
I did that, thank you, and here is the result: 


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61432559    30716248+   7  HPFS/NTFS
/dev/sda2        61432560   976768064   457667752+   f  W95 Ext'd (LBA)
/dev/sda5        61432623   243577529    91072453+   7  HPFS/NTFS
/dev/sda6       243577593   309154859    32788633+   7  HPFS/NTFS
/dev/sda7       309154923   952991864   321918471   83  Linux
/dev/sda8       952991928   976768064    11888068+  82  Linux swap / Solaris

What a mess.

---

### Post by Elfy on 2008-09-03
They look normal enough to me - you have 3 windows partitions (HPFS/NTFS) and 2 linux partitions - one with the installation on and a swap.

---

### Post by kansasnoob on 2008-09-03
> **ByteJuggler said:**
> No those partitions are likely your Ubuntu partitions.  It only looks "unformatted" to Windows since Windows can't read Linux partitions by default.   I suggest you boot into Ubuntu, install "gparted" (Partition Editor) if needed, then use it to view your partitions instead.  (Go to System->Administration->Partition Editor.)

That would certainly be the most helpful to me!

```
sudo apt-get install gparted
```

Just for an example I'll show mine:

[ATTACH]83938[/ATTACH]

You can see that I have a win partition (sda1), and an extended partition (sda2) that contains two linux OS,s and a shared swap.  And you can also see how much space is used and how much is free.

You may also want to install ntfs-config so Ubuntu can read your ntfs drives, then again you may not need to ............. I just can't remember off the top of my head:confused:

---

### Post by egalvan on 2008-09-03
> **kansasnoob said:**
> ...
You may also want to install ntfs-config so Ubuntu can read your ntfs drives, then again you may not need to ............. I just can't remember off the top of my head:confused:

As of 8.04.1, Ubuntu sees and uses NTFS OK, no need for anything extra.

At most you have to access the drive.
 They show in "Places' under Ubuntu, (and USB drives show on the desktop)
They show in  'System Menu" under Kubuntu.

Clicking them to open a file-browser, or right-clicking and choosing 'mount"

Simple. "It Just Works"

This is my experience from dual-booting XP/8.04.1 on six different machines in the past three months.

Linux, you've come a long way, baby! :guitar:

---

### Post by Tyler Zambori on 2008-09-04
well it does seem to see the files on my D drive, which is where
I'm installing my windows programs and files. 

So, would it be safe to resize that 300-plus GB partition
that ubuntu made?

---

### Post by Tatty on 2008-09-04
> **Tyler Zambori said:**
> well it does seem to see the files on my D drive, which is where
I'm installing my windows programs and files. 

So, would it be safe to resize that 300-plus GB partition
that ubuntu made?

If you wanted to resize it, i would probably boot into a live CD and use gparted to resize... i dont think i would trust the windows partitioner handling non-windows filesystems.

You probably dont want to make this any smaller than 20Gb  (10gb for root filesystem and 10Gb for home), but its up to you. I think the minimum ubuntu needs is around 4Gb.

Ubuntu should have given you an option to select how much space you want to allocate to it before installing, have a read of this tutorial before your next install :) 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

EDIT: when i said not smaller than 20Gb i was reffering of course to your main ubuntu partition... your swap partition should generally be around 2x the size of your RAM. :)

---

### Post by Tyler Zambori on 2008-09-04
hi, thanks for the link.  That tutorial doesn't seem to tell you
how to choose a partition size either, but no matter, it's already done.

I went into gparted, and got a nice graphic representation the partitions at the top of the screen, but I can;t figure out how to resize that 300+
Gb partition.  Ubuntu is only taking up 5 gb of it. 

Yes, I'll remember to give it at least 20GB, but I think 300gb is a little too much. 

so how can I resize it in gparted? Do I have to un-mount it or something? 
The option to re-size stays "ghosted"  the way it is, so I can't do it.

---

### Post by Tatty on 2008-09-05
Yes, the drive has to be unmounted to alter the partitions,  you should boot into a live CD to edit your partitions.  Gparted should be installed by default on your live CD.  And of course with any partition changes to your hard drive, make sure you have all your valuable data backed up, just in case.

[http://www.psychocats.net/ubuntu/images/installinghardyplus10.png](http://www.psychocats.net/ubuntu/images/installinghardyplus10.png)
[http://www.psychocats.net/ubuntu/images/installinghardyplus11.png](http://www.psychocats.net/ubuntu/images/installinghardyplus11.png)
If you have a look at these screenshots from the psychocats tutorial, it shows the part of the installer where you can select how much space you want to give to windows and how much to ubuntu.  I know this isnt helpful to you now, but itll be useful to know for your next install :)

---

### Post by Tyler Zambori on 2008-09-06
hi tatty,

I saw that tutorial on psychocats, and what ubuntu does on my
computer is completely different. 

It does not show any block for windows xp.  It only shows
a block for the main linux partition, and a block for the
swap linux partition. I can choose the partistion size 
between those two all I want, but not to resize between
xp and linux.

Where can I get the version they show on psychocats?

---

### Post by Bucky Ball on 2008-09-06
You can unmount the drives by pasting this in a terminal:
[B]
sudo umount -a[/B]

Then go back to gparted partition editor (it should be in System->Administration->Partition Editor for easy access now you have it installed) and away you go. To remount, back to a terminal and;

**sudo mount -a**

Tyler - Paste this into a terminal (Applications->Accessories->Terminal)

**sudo apt-get install gparted**

Then;

**sudo gparted**

... or choose the easy way as described above and should open the gui and you can see all the drives in your box.

 \\:D/

---

### Post by Tyler Zambori on 2008-09-06
Thank you bucky, I tried it the easy way with gparted
form the live cd, and it worked until after I installed
the mobo drivers from the windows side.  After that
I got grub loading error 17 messages. 

I' m about fed up.  I don;t know where to get ubuntu
that looks like the psycho cats partition setup. 

Maybe I I will just practice installing ubuntu studio
with no windows until I can get the partitioning
figured out on that one, but I'm getting tired of
re-installing and re-formatting everything over and
over again.

Thanks for trying though.

---

### Post by Elfy on 2008-09-06
Error 17 usually just refers to the filesystem not being recognised by grub - could be as simple as it pointing to the wrong partition.

Run the livecd to check your menu.lst

If the partition schem is as it was before then do this to mount the linux partition and get the menu list. In the original linux was on sda6 - run sudo fdisk -l to check it's the saem if not replace sda6 below with the correct partition.

```
sudo mkdir /mnt/recovery
sudo mount -t etx3 /dev/sda6 /mnt/recovery
cat /mnt/recovery/boot/grub/menu.lst
```

That should give you your menu list - go down until you reach similar to 

> ## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)your root should be different, if linux is still on sda6 then root should be (hd0,5), if it is not then

```
gksudo gedit /mnt/recovery/boot/grub/menu.lst
```

Change the root to (hd0,5) and save. Try to reboot.

If though fdsik -l gives a differnt result then amend the root to suit - if sda6 then hd0,5, sda5 would be hd0,4

---

### Post by Tyler Zambori on 2008-09-06
oh dear. that menu list stuff is a bit advanced for me
at this point, but I got it working now. 

I re-did everything, saw that I just wasn't reading the
data blocks right, resized them the way I wanted, then
ended up having to resize the partitions in gparted with
the live CD anyway, because ubuntu does what it wants 
anyway.

It worked, I made sure to install all drivers before doing
anything with ubuntu, and the partition re-size worked,
so now I can have the main chunk of the HD useable by
both OS's. 

Man, they really need to make the paritioning easier to
do and understand.  

Thanks everybody for your help.

---

### Post by Tatty on 2008-09-06
> **Tyler Zambori said:**
> hi tatty,

I saw that tutorial on psychocats, and what ubuntu does on my
computer is completely different. 

It does not show any block for windows xp.  It only shows
a block for the main linux partition, and a block for the
swap linux partition. I can choose the partistion size 
between those two all I want, but not to resize between
xp and linux.

Where can I get the version they show on psychocats?

Thats odd, The screenshots from the psychocats tutorial are from a standard ubuntu install.  Are you using the text based installer by any chance?

---

### Post by Tyler Zambori on 2008-09-06
no, I'm not using the text based installer, I just didn't
see that it said:  microsoft windows xp on the block.

But it still installed itself by taking up just about all the available disk space.  The partition manager was actually having me choose partition size on the C: drive partition, but then it took up everything beyond the C:partition.

So it's good I was able to re-partition using gparted from the
live CD, but man it has taken me a whole week to be done with this. I hope they can make this a little smoother in the future.

---

### Post by Bucky Ball on 2008-09-06
[quote=[Tyler Zambori]("http://ubuntuforums.org/member.php?u=651474")]man it has taken me a whole week to be done with this[/quote]

Which means next time you'll probably be able to tackle and fix the same problem in 15 minutes! And to jog your memory, you have this thread ...

Welcome, Rock on, don't be shy asking questions when this happens ](*,) -  and have fun with your new OS.  \\:D/

---

### Post by Tyler Zambori on 2008-09-07
Thank you I sure am planning on having fun with it :).

---

### Post by Tatty on 2008-09-07
> **Tyler Zambori said:**
> no, I'm not using the text based installer, I just didn't
see that it said:  microsoft windows xp on the block.

But it still installed itself by taking up just about all the available disk space.  The partition manager was actually having me choose partition size on the C: drive partition, but then it took up everything beyond the C:partition.

So it's good I was able to re-partition using gparted from the
live CD, but man it has taken me a whole week to be done with this. I hope they can make this a little smoother in the future.

There is an option there to tell ubuntu to simply use all the unpartitioned space on the disc.  Perhaps this is what you did?

Im not sure as I have never experience this problem before.  However, its good that you have now got round this.

---

### Post by Tyler Zambori on 2008-09-07
> **forestpixie said:**
> Error 17 usually just refers to the filesystem not being recognised by grub - could be as simple as it pointing to the wrong partition.

Run the livecd to check your menu.lst

If the partition schem is as it was before then do this to mount the linux partition and get the menu list. In the original linux was on sda6 - run sudo fdisk -l to check it's the saem if not replace sda6 below with the correct partition.

```
sudo mkdir /mnt/recovery
sudo mount -t etx3 /dev/sda6 /mnt/recovery
cat /mnt/recovery/boot/grub/menu.lst
```

That should give you your menu list - go down until you reach similar to 

your root should be different, if linux is still on sda6 then root should be (hd0,5), if it is not then

```
gksudo gedit /mnt/recovery/boot/grub/menu.lst
```

Change the root to (hd0,5) and save. Try to reboot.

If though fdsik -l gives a differnt result then amend the root to suit - if sda6 then hd0,5, sda5 would be hd0,4

Ok, I did all this, and on the menu list, right after end default option,
it said that the root is (hd0,4),( and it should be (hd0,5).)
so how do I change it to (hd0,5)? 

I am having grub error loading problems again.  I got it fixed to
the point that I can load windows, but it won't load ubuntu.
It says the partition is unmounted, but when I go into gparted
that part is ghosted and I can't touch it that way. 

Anyway, I guess I need to know how to change the root this way, please.

---

### Post by Bucky Ball on 2008-09-07
Try supergrubdisk. This page will teach you a heap about Grub but to get it up for now, (and this probably will) download, make a cd, boot from it and follow your nose. See how you go.

[www.supergrubdisk.org](www.supergrubdisk.org)

\\:D/

---

### Post by Tyler Zambori on 2008-09-08
hi, thank you very much everyone, I got it perfect now, but
with ubuntu studio. I did a fresh install of that. 

I tried all the suggestions, and just couldn't get the root 
drive mounted. So it turns out that ubuntu studio is actually
the most civilized one, for partitioning, as long as you 
remember to tell it something like 350GB not 30Gb just for 
the ext3  partition (for a 500gb HD).  

First I learned how to fix the mbr myself, finally, 
then made sure both C: and D: were formatted by windows.
That is how you get the requester line in ubuntu 
studio setup that lets you actually specify the partition 
size. Then I told it 360gb, and now I have something like 
a 77gb partition for ext3 partition for ubuntu, and 
about 50gb that I had already set up beforehand, for 
windows.  No resizing, no worrying about mounting, no 
more mbr fixing, yay.

I am highly relieved.

---

### Post by Bucky Ball on 2008-09-08
Normal ubuntu comes in an alternate install too (text version, no gui). Does the same. You can manual partition in either. Just choose 'manual partitioning' when it gets to the partitioner.

Having said that, congratulations and have fun. If you want, you can go:

sudo apt-get install ubuntu-desktop

and that will give you the best of both worlds. Unless you're heavily into high-end audio, ustudio probably has a lot of apps you will probably never use.  \\:D/

---

### Post by Elfy on 2008-09-08
> it said that the root is (hd0,4),( and it should be (hd0,5)The last command I gave was to allow you to edit the file - you just needed to change it :)

Glad all is sorted now.

---

### Post by Tyler Zambori on 2008-09-08
> **Bucky Ball said:**
> Normal ubuntu comes in an alternate install too (text version, no gui). Does the same. You can manual partition in either. Just choose 'manual partitioning' when it gets to the partitioner.

Having said that, congratulations and have fun. If you want, you can go:

sudo apt-get install ubuntu-desktop

and that will give you the best of both worlds. Unless you're heavily into high-end audio, ustudio probably has a lot of apps you will probably never use.  \\:D/

Thank you :).  I will do that.  Well, there is a member 
of the house who is into composing music, and it's 
probably just as well I learned how to do it right 
on my own computer before I build a new one for him. 
I'm more into 3D animation and video editing.

I did find a tutorial on manual partitioning in regular 
ubuntu, through psychocats, but it was so long and 
complicated that I just didn't feel up to trying it.  

I did try that supergrub disk like you said, and it 
did bring back my grub menu, but I just couldn't get 
the disk mounted.

---

### Post by Tyler Zambori on 2008-09-08
> **forestpixie said:**
> The last command I gave was to allow you to edit the file - you just needed to change it :)

Glad all is sorted now.

Thank you forest pixie, I didn;t know how to change it, sorry,
but thank you very much. At least everything worked up to that point.  I'm afraid I'm not the programming type, but I was able
to gt the commands in there correctly, and see the result.

Is ok, my b/f was feeling very nervous about me messing with my valuable asset (the computer) which took me many months to earn the money for. At least  I was able to stop re-installing windows.

---

### Post by Elfy on 2008-09-08
You should be pleased with yourself :)

Even if the commands mean nothing to you at the moment they will one day and the light will dawn - I've only been here a year and a half myself, so it will happen.

I'm no programmer either, but the command line will become more an more useful as you progress.

If you do come back here can you mark the tread solved, thread tools at page top.


i see you looked at the partitioning tutorial - ,>  but it was so long and complicated that I just didn't feel up to trying it. - it isn't as long as it looks once you start, it is better imho to deal with all the partition work before you even start the installer.

Good luck

---

### Post by Tyler Zambori on 2008-09-08
> **forestpixie said:**
> You should be pleased with yourself :)

Even if the commands mean nothing to you at the moment they will one day and the light will dawn - I've only been here a year and a half myself, so it will happen.

I'm no programmer either, but the command line will become more an more useful as you progress.

If you do come back here can you mark the tread solved, thread tools at page top.


i see you looked at the partitioning tutorial - , - it isn't as long as it looks once you start, it is better imho to deal with all the partition work before you even start the installer.

Good luck

Thank you forest pixie, that is encouraging.  I'm sure it will
all get more comfotrable and familiar as I go.

---

### Post by Bucky Ball on 2008-09-08
Cool. You can't break the hardware, that is one thing! :)

Mount a drive:

**sudo blkid**

Gives you a list of your drives/partitions. sda, sdb etc are the drives. sda1, sda5 are two partitions on the sda drive. That simple.

**sudo mount /dev/sda?** (number of your partition - eg sda1, sda5 whatever)

... and that should do it. To mount it permanently is a little more complex (but not much) but you'll get there in no time, I'm sure. Just post again if this happens - ](*,)

Have fun!

\\:D/

---

### Post by Tyler Zambori on 2008-09-10
> **Bucky Ball said:**
> Cool. You can't break the hardware, that is one thing! :)

Mount a drive:

**sudo blkid**

Gives you a list of your drives/partitions. sda, sdb etc are the drives. sda1, sda5 are two partitions on the sda drive. That simple.

**sudo mount /dev/sda?** (number of your partition - eg sda1, sda5 whatever)

... and that should do it. To mount it permanently is a little more complex (but not much) but you'll get there in no time, I'm sure. Just post again if this happens - ](*,)

Have fun!

\\:D/

Oh yea, I would have wanted to mount it permanently, so it's
fine that I found a way for now. I hope my ubuntu books get here soon....

---

### Post by Elfy on 2008-09-10
If you do want to do so, I did this for someone else

[http://ubuntuforums.org/showpost.php?p=5720510&postcount=5](http://ubuntuforums.org/showpost.php?p=5720510&postcount=5)

---

