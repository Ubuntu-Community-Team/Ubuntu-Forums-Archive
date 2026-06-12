---
title: "My Eyes Are BLEEDING, I'm so frustrated!"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by misteralexander on 2008-09-20
I have been all over the internet, I have read pages upon pages of forum posts, I followed a very recent post of Grub21 error here for almost an hour . . . nothing is working.

I have a laptop that has two 160GB HDD's.  HD0 & HD1. Both are CLEAN with a simple ext3 partition & NO OTHER DATA. I install Ubuntu, use the "guided use entire partition" option & install it to HD0 (sda), leaving the HD1 (sdb) with nothing but a clean ext3 partition.

Install goes GREAT. I reboot and get
```

Grub Stage 1.5
Grub Loading . . . 
Grub Error 2

```

I have tried to boot with the LiveCD and repair GRUB
```

I've tried...
grub-install --no-floppy /dev/sda
//and//
fdisk -l
//and//
mkdir /fix
mount /dev/sda1
grub-install --no-floppy --root-directory=/fix /dev/sda

```

I've installed 8-times so far with either "GRUB ERROR 21" or "GRUB ERROR 2" as my result.

What is happening?:confused: How do I fix this?:confused:

-MisterAlexander

---

### Post by dhughes on 2008-09-20
> **misteralexander said:**
> ...HD0 (sda), leaving the HD1 (sdb)...

 Not really sure but at least I'll bump this. Also, I think that should be sda1 not sda, but obviously Guided Install should pick the only partition there unless you didn't create one, somehow?? Just a wild guess.

---

### Post by Shazaam on 2008-09-20
On your laptop you have one internal and one external drive, correct? You might try disconnecting the external and run the install again.

---

### Post by Sef on 2008-09-20
GRUB error 2:

> 2 : Bad file or directory typeThis error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO.

Here is [one fix]("https://answers.launchpad.net/ubuntu/+question/7137") I found:

> Most of these are created by the grub loader reading (or attempting to read) an area that it can't see because of the DMA settings.


 Fix: Rather simple really go into your BIOS and reset the IDE hard-drive settings from (Auto) to a DMA mode the hard-drvie does not recognise,


Let us know if that works.

---

### Post by panhandle on 2008-09-20
If the above post doesn't work for you...

Which threads have you been following? Can you list a couple of them here?

I ask so as to get a better idea of the problems (and similarities to other problems) you are having.

---

### Post by misteralexander on 2008-09-20
Thanks to EVERYONE for your helpful replies . . . 

I think i MAY have solved my problem . . . a simple oversight MAY have been the cause of all this grief.

While looking through the BIOS for the Auto/DMA option mentioned in an earlier reply, I noticed an option tucked away that simply said "Show RAID -- on/off". It was set to "off", so I enabled it, seeing no further BIOS options on the matter. Confused, I rebooted, planning on going to the LiveCD. Then as it was booting a screen came up and then disappeared (like on then gone in 2sec), I rebooted again and saw "CTRL-I" before it disappeared again. I rebooted and this time franticly hit "CTRL-I", and was ushered into a RAID-Configuration Screen (INTEL RAID-BOOT ROM) or something similar. I saw that this utility was holding both internal 160GB disks in a RAID-0 configuration. I chose the option to convert the disks to "Non-Raid" and asked that these two separate disks be let free.

I booted into the LiveCD and using Terminal went into GParted. I deleted the Partition on the first HDD (SDA / SDA1) and reformatted the second disk (SDB / SDB1) as ext3.

I rebooted and am now going to try a fresh install, using the "Guided - Use Entire Disk" option. Hopefully this was the problem all along.

I never knew these disks were in a RAID config from the start, seeing is, Linux only saw two internal drives. I think that when I installed on HD0,0 (SDA / SDA1) the OS was put there, but when I rebooted the computer was looking over the whole thing (the 2 disks) and nothing it saw made any sense, hence my GRUB Error.

We'll see! I'll post here again to let you know how it goes!!

-Alex.
P.S. - I'm deployed to IRAQ right now, so my time zone compared to the states is all messed up, sorry if these posts are coming in at strange times, but I do appreciate all your help!

---

### Post by misteralexander on 2008-09-20
THAT WAS IT:) THE RAID FIX, FIXED MY PROBLEM.

I never would have been rooting around in the BIOS if it hadn't been for the suggestion to check the "Auto/DMA" option, thanks!

-Alex.
[THREAD SOLVED]

---

### Post by Crajy B on 2008-10-05
So what I gather from you is that RAID is causing the problem?

I have the same error (Grub Error 2) but I do not have my HD's in a raid, they are set to run in IDE mode.

Infact, Gutsy and Hardy all worked, why not Interpid? This is what is really confusing me.

The only catch is in Gutsy and Hardy I had to modify my menu.1st before rebooting after a fresh install.

My HD's would get flipped for some reason. During the installation my HD on the normal mobo channel was hd0 then my HD's connected to my IDE/RAID controller were hd1 and hd2 but in the menu.1st/device.map this got changed. My boot hd was recognized as hd2... so I had to modify this back to hd0 to get grub to load.

The following link describes my problem very well. 

[http://ubuntuforums.org/showthread.php?t=151682](http://ubuntuforums.org/showthread.php?t=151682)

I have an Asus A8V-Deluxe with an AMD 3200+ CPU, 2 GB of ram and 3 HD's and 2 Rom's.

1 HD is on the Primary channel and the other 2 are on the IDE/RAID controller (onboard controller).

All 3 HD's are 200gb each.

I don't know about you guys, but this does seem to be a problem if after 1st boot the OS is dead :(.

What do you guys think? I was thinking of trying the above post, but.. I have to reformat again... :( :( :(.

Is there anyway to try installing 8.10 intrepid without blowing out my working 8.04 Hardy?

I would like to upgrade and the only think I can think to do this is to disable the onboard IDE/RAID controller, install, re-enabled it, find out all the UUID's for both the HD's and mount them in the fstab.

Seems like a bit to do for something that should work... seems like I am not the only one that is having this problem and it has been around for a while.

This is my 1st post, so forgive me.. had a lot to say and just am throwing it out there.

If anymore information is required, just ask I will gladly provide it.

Anything to get this resolved before the final release of Intrepid 8.10.

---

### Post by Crajy B on 2008-10-05
I did some more testing and it would seem that if I disable my IDE/RAID controller, the boot drive goes from sdcX (x=the partition number) to sdaX, and then when I enable it again, it goes back to sdcX.

This would lead me to believe if I disabled my IDE/RAID controller, formatted/installed Intreprid, then re-enabled IDE/RAID... I will have the same Grub Error 2 issue :(.

---

### Post by Kellemora on 2008-10-05
Just a small unrelated suggestion since Raid 0 & 1 have been mentioned here.

They are NOT what you think!

I would do some very SERIOUS study on RAID before enabling Raid 0 or Raid 1, it is NOTHING like Raid 5, not even close.

You data is at just as much at risk as having a single hard drive, maybe even worse!

I'm saying this because we had a couple of newer computers in the office that came with Raid 0 turned on by default and nobody knew it.
Data was NOT where it was supposed to be, volatile data that was supposed to be isolated was found easily accessable using simple hacking methods and worst of all, all the backups to these machines turned out to be nothing more than LINKS back to those hard drives.  Needless to say, the backups were USELESS and much important and irreplacable data was lost when only one drive failed.

These newer hard drives don't last longer than an ice cube in that proverbial hot place.  We have old drives, small, that are a decade old that work fine, just don't have enough room.  But these new hard drives are replaced faster than popcorn in the popcorn machine or coffee in the coffee urn.

I think it's a PLOY to push everyone to these data Sticks that fry just about as fast.  I have enough DEAD SD cards here too, that I could use them as Lego blocks and build a model skyscraper!

Just be wary of using Raid 0 or 1 until you learn what it really is and does, that's all!

TTUL
Gary

---

### Post by Crajy B on 2008-10-06
Hey Gary,

Thanks for the heads up.

I don't use RAID 0 anymore.. I was using it before for the pure speed of things.

I try to keep everything backed up on DVD.. you do what you can..

As for the many issue I was having... it is very odd, I have figured it out and a possible reason why it occurs.

This is what I found my channels and HD's mapped to.

SCSI 5 - sda1 (hd0,0)
SCSI 5 - sdb1 (hd1,0)
SCSI 6 - sdc1 (hd2,0)

SCSI 5 is on my IDE/RAID controller.

So what was happening was the installer would install on (0,0,0) which points to the first HD on SCSI 6 sdc1, otherwords hd0 on that channel.

Then when the system would install and boot it would point to (hd0,0) which was wrong because that didn't account for my SCSI 5 channel.

So what I did was clicked the ADVANCED button and installed the bootloader on (hd2).

Then no more Grub error 2, instead error 15 which I can deal with, just remap my root in the menu.1st to (hd0,0) from (hd2,0).

BUT now, after an update, seems that I had to point my grub root back to (hd2,0)... maybe someone fixed this???

I will try a reformat again once the final release is out.

Forgive my ramble, as it may all be wrong and I am a noob. ;)

---

### Post by Kellemora on 2008-10-08
Hi CB

I'm only a Noob too, trying to muddle through things the best as I can.

Just lost 12 hours of work time trying to figure out why something that was working fine, suddenly didn't work anymore.

Turned out I was doing it differently and Ubuntu apparently doesn't support the logical method only the standard method.  Whereas most other Distro's and the Doze uses both Logical and Standard methods.

It trying to save time and reiteration of files that would need deleted, I did something Ubuntu can't handle, and that's saving a shared file onto another computer rather than the host (originating) computer where it would need deleted.

But we all learn by DOING and finding out what works best for us!

TTUL
Gary

---

