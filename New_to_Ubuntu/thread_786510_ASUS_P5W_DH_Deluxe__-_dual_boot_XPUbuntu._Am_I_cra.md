---
title: "ASUS P5W DH Deluxe  - dual boot XP/Ubuntu. Am I crazy?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by hawse1978 on 2008-05-08
Hi

I have an ASUS P5W DH Deluxe motherboard with 2x320gb Seagate SATA drives. I would like to dual boot XP and Ubuntu (ideally Hardy), preferably using RAID 1. Failing that, as separate disks, or if all else fails, as a single large drive.

I have tried heaps of different settings, swapping the SATA ports on the board, changing the jumpers and twiddling with BIOS, and I think I'm going crazy. 

Has anybody managed to configure this setup with this hardware? If so, I would be most grateful if you could share:

1) which SATA ports on the board are being used,
2) your bios settings.
3) the RAID_SEL jumper settings.

I shall be keeping my fingers crossed!

Cheers all!
Mike

---

### Post by executive on 2008-05-11
i also have a similar setup and would like to know as well!

---

### Post by hawse1978 on 2008-05-11
Finally managed to get this working. For info, I have 2x Seagate SATA drives plugged into SATA1 and SATA4. The RAID_SEL is in the default RAID1 (safe) mode, though it is not actually acting RAID 1, they are shown as separate disks configured in BIOS. My DVD drive (configured as IDE Master) is connected to PRI_IDE (next to floppy controller).

Steps:
* Installed XP - the setup identified both drives, but claimed to be unable to access the second. This was confirmed when I logged in and checked under Computer Management, and only one disk was detected. 
* Installed Hardy - both drives found, partitioned, grub on hd0. Hardy sees both drives. 

Dual boot working fine

BIOS settings to follow, but I think JMicron support can be disabled with this combo of SATA ports, and IDE Configuration needs to be in AHCI mode... will check next time I reboot.


[Current issues with board]
optical out not working, but onboard 5.1 (analog) is fine
lsusb hangs, but I think this is a Hardy problem 

[Untested]
wireless
firewire
DH remote
eSata

Hope this helps!

Mike

---

### Post by Cornova on 2008-05-11
I have a similar setup and noticed that under Ubuntu I can see the hard drive that XP is on, but under XP I cannot see the hard drive that Ubuntu is on (under mycomputer).

---

### Post by hawse1978 on 2008-05-11
Beware! After reading through my notes, I am a bit concerned now that XP doesn't see the second drive. maybe XP *is* trying to use RAID 1, but Ubuntu isn't. haven't booted into XP since installing Ubuntu, and don't want to for a while in case recent file changes I made get lost. 

Please be careful. Oh, and if yopu try it and XP destroys the Ubuntu drive, please tell me!

---

### Post by Cornova on 2008-05-11
I have had this setup for a month and there haven't been any problems so far. The only reason it concerned me was when I updated to Hardy and had some problems - I thought I'd have to move files back to XP since I planned to wean off of XP and it wasn't working out at first with Hardy.

---

### Post by hawse1978 on 2008-05-11
well it's a relief that the XP install didnt try and RAID over Ubuntu, but i know what you mean about Hardy issues. I'm having a hell of a time trying to get my DVICO TV card working. All the tutorials so far are for 7.10. Also, my usb drive isn't being recognised for some reason. i know that usb works, because I managed to get my webcam working.

My PC is currently flat on its back with its guts out, so i might just try the tv card in another PCI slot and see what happens. unfortunately, the troubleshooting articles ask for info from lsusb, but that doesn't work on mine - just hangs. i believe this is a Hardy issue as well.

---

### Post by shifty_powers on 2008-05-11
> **hawse1978 said:**
> Beware! After reading through my notes, I am a bit concerned now that XP doesn't see the second drive. maybe XP *is* trying to use RAID 1, but Ubuntu isn't. haven't booted into XP since installing Ubuntu, and don't want to for a while in case recent file changes I made get lost. 

Please be careful. Oh, and if yopu try it and XP destroys the Ubuntu drive, please tell me!

heh, bit of a misunderstanding on your part there.

the raid you are using is transparent to either operating system as it is handled by a chip on the motherboard.

what windows/ubuntu will see is the PARTITIONS that you have set up. windows will not see the ubuntu partition as it is using, probably, the etx3 journalling file system, which windows can't see. (there are drivers for windows to do so, but can't remember what they are called ;)). However, ubuntu will happily see, read and write ntfs partitions ;)

so, tbh, sounds like everything is working fine.

---

### Post by hawse1978 on 2008-05-11
I have to admit, configuriung RAID and this mobo seems like a black art to me, so I'm not surprised I was confused :-)  
My concern when adding the "Beware" post was that XP couldn't see the drive through the "Computer Management" control panel in administrative tools. When I had Gutsy partition previously (RAID 0), Computer management at least *saw* the disk, even if it couldn't read the filesystem to assign drive letters.

With Gutsy, I used the Ext2IFS([http://www.fs-driver.org/]("http://www.fs-driver.org/")) drivers to map ext3 partitions in explorer, but if XP doesn't know the disk exists, even that wouldn't work.

---

### Post by shifty_powers on 2008-05-11
> **hawse1978 said:**
> I have to admit, configuriung RAID and this mobo seems like a black art to me, so I'm not surprised I was confused :-)  
My concern when adding the "Beware" post was that XP couldn't see the drive through the "Computer Management" control panel in administrative tools. When I had Gutsy partition previously (RAID 0), Computer management at least *saw* the disk, even if it couldn't read the filesystem to assign drive letters.

With Gutsy, I used the Ext2IFS([http://www.fs-driver.org/]("http://www.fs-driver.org/")) drivers to map ext3 partitions in explorer, but if XP doesn't know the disk exists, even that wouldn't work.

what do you mean by it doesn't see the ubuntu partition?

does it not show up in my computer? what happens when you go control panel>administrative tools>disk management? what size does this report, (and not just for the xp partition. you should see that and then some unidentified space after that on the disk).

either way, xp cannot just overwrite anything on the ubuntu partition. xp does not control how the raid array works, the raid controller on the motherboard does that, nicking a few cpu cycles in the meantime btw.

i'm not going to make any gaurantees of course, but i honestly do not see anyway in which xp could do anything to your ubuntu partition in this situation...

---

### Post by hawse1978 on 2008-05-11
> what do you mean by it doesn't see the ubuntu partition?

control panel>administrative tools>disk management only reports the 320gb drive that XP is installed on. no mention of the second drive at all. During XP install at the point of choosing the installation partition, the setup acknowledged the existence of the second drive - with size etc, but said something along the lines of: "setup cannot access this disk"

Thanks for settling my nerves about XP messing with my ubuntu drive :-)

Mike

---

### Post by shifty_powers on 2008-05-11
do me a favour and go into the disk management and take a screenshot and post it will ya ;)

plus, why raid?

Firstly, onboard raid, as you have found out is not the greatest. If you REALLY want it, get hold of a good quality, (approx. £80-100), raid controller. It will make it so much easier and make it such a btter job of it.

Secondly why raid 1? If i was going to use raid it would only be raid 0 or possibly 5, which combines elements of both mirroring, (raid 0), and striping (raid 1). I'm not convinced that the performance boost is anywhere near enough for the risks to be worth it.

Are you aware that in a raid 1 array, if one disk fails, for whatever reason, you lose the whole array? So if you ubuntu drive failed, you woul effectivley lose the contents of your xp drive. not a risk i would want to take personally.

If it was my pc, I would just use it as two separate disks, with xp on one and ubuntu on the other. Just install xp first and then ubuntu, to make sure that grub is not overwritten.

Oh and a tip. When you install xp, create a 10-15 gig partition, on which you put only, and i mean ONLY, your windows installation. Partition the rest as you like, just make sure that as much as possible, everything else does NOT go onto the windows installation partition. This means that your windows partition will take a lot longer to fragment and your system will keep running nice andsmoothly for longer. Oh and get hold of diskeeper, essential program. (disk defragmenter, hint, look on pirate bay if you have to ;)).

As for ubuntu, i usually have a 500meg partition mounted as /boot, a 10 gig partition mounted as / (ie.e root), and a 1-2gig /swap partition, and then the rest is mounted as /home. Can come in very handy later on, if you reinstall, you just format and install to /boot and /root (if needed, sometimes you can just reinstall /boot and leave the rest as unformatted and untouched to solve problems ;)). This means that your home partition stays in tact, including your files and documents when you ugarde to a new distro, e.g. when 8.1 0 comes out.

hope that gives you something to think about ;)

---

### Post by hawse1978 on 2008-05-11
I was under the impression that Raid 1 was mirroring, and that the whole point was that if one disk failed, the other would still be usable and another disk could be dropped in and would be re-mirrored. I thought it was raid 0 that combines both disks and one fail means all data lost. Either way, it seems that XP is using disk 1, and Ubuntu is just using disk 2. From memory, the mobo jumpers are set to Raid 1 by default, but there is some onboard driver config required to actually implement it (which I was unable to figure out and set).

I will post the XP screenshot for you before this time tomorrow. It's 1:40am here in Sydney and I have to work tomorrow :-(
What is the equivalent of Disk Management in Ubuntu? 

Cheers,
Mike

---

### Post by shifty_powers on 2008-05-11
heh, don't blame you buddy.

bugger, you're right about raid 1 >.< heh, been a while since i read about it ...

in that case if you used two 320 gig disks, then the 320 gig that xp is reporting is precisely right. raid 1 will halve the capacity of the two drives as you are effectively creating an automatic backup of one disk onto the other, if that makes sense.

tbh, it seems that your raid array is working perfectly and you have nothing to worry about.

post that screen shot and i'll tell you for sure ;)

---

### Post by hawse1978 on 2008-05-12
EDIT: Changed in-line image to link

<fx:sheepishgrin>Oops...looks like you were right, shifty! It appears that now the second disk is partitioned and has data, it is now visible in XP! But I swear it didn't show up when I first logged into XP. Honest! :-)</fx:sheepishgrin>

Also, logging into XP did not affect my Ubuntu partition even though the RAID_SEL jumpers were set as RAID1. I reckon this is because of the BIOS settings (in my next post) that set the IDE configuration to [STANDARD IDE]. I'm sure I tried setting this to Raid1, but the Ubuntu live CD would not load with that setting. Either logical disk errors, or error reading CD. i forget which. 

Apologies if I misled anybody with this. Here is the screenshot anyway:
[http://www.kociak.com/ubuntu/disk-management.png]("http://www.kociak.com/ubuntu/disk-management.png")

Note that XP is on disk 0, and Ubuntu is on disk 1, hence the unrecognised partitions. Also, the C: drive on the XP disk is currently the only one formatted. Not sure what I will do with the remaining 200gb on there yet!

Also... I stated in a previous post that lsusb was hanging, and I blamed this on Hardy. Well, as part of this reboot, I removed my troublesome TV card, and lsusb now works. Something fishy going on there! (Apologies to Hardy ;-))

---

### Post by hawse1978 on 2008-05-12
As promised, here are the BIOS settings for my config:

[MAIN]
PRIMARY IDE MASTER [DVD RW]
PRIMARY IDE SLAVE [NOT DETECTED]
THIRD IDE MASTER [NOT HDD SERIAL HERE]
THIRD IDE SLAVE [NOT DETECTED]
FOURTH IDE MASTER [NOT DETECTED]
FOURTH IDE SLAVE [HDD SERIAL HERE]

IDE CONFIGURATION
> CONFIGURE SATA AS [STANDARD IDE]
> ONBOARD IDE OPERATE MODE [ENHANCED MODE]
> ENHANCED MODE SUPPORT ON [S-ATA]

[ADVANCED]
ONBOARD DEVICES CONFIGURATION
> JMICRON SATA/PATA [ENABLED] <--- This can probably be disabled since the boot message states no drives detected
> JMICRON CONTROLLER MODE [BASIC]
> JMICRON SATA/RAID BOOTROM [ENABLED]

Everything else is currently set to factory default.

Hope this helps somebody :-)

---

### Post by shifty_powers on 2008-05-12
right, well for a start you most certainly do NOT have raid 1 configured and working.

as i stated, you have two 320gig hard drives, (with an actual capacity of approx 300 gig, don't ask ;)).

Now, if you were using raid 1 properly, you would have 300+300/2 which is of course 300 gig. Raid 1 will create two exact copies on both drives, meaning you lose half of the capacity of the drives on the array, giving you an automatic backup system. So, in other words, disk management would only show ONE 300 gig drive.

The fact that it shows TWO drives, with different partitions etc... means that raid 1 is not enabled properly.

Tbh, first i have to question why you need raid one. If you are bothered about hard drive failure, but a 750 gig hd and an external enclosure, and use something such as clonezilla to create disk images of the two drives.

secondly, if you REALLY want to use raid, I would highly recommend that you get hold of a separate hardware raid controller. Most raid controllers on motherboards really are not that good, and as you have found, are just a pain in the ***...

[http://www.ebuyer.com/product/124378](http://www.ebuyer.com/product/124378) is ideal, but is £116 approx. there are cheaper but be careful.

Sorry, but i have never used that motherboard and i will not be much use in getting raid working on it. Anyways, as outlined above, i think it is a waste of time ;)

hope that this gives you something to think about ;)

---

### Post by hawse1978 on 2008-05-12
I hear what you are saying. I decided that I don't need all the OS stuff to be Raid 1 protected. As long as I have all my media and settings files backed up (of which there is quite a lot) I will be sorted. So I have invested in a D-Link DNS 323 NAS box with 2x750gb drives which *are* currently in Raid 1. :-) 

As a friend pointed out, Raid 1 is not a great backup strategy, so all the stuff that I *really* don't want to lose will be backed up to CD/DVD.

---

### Post by shifty_powers on 2008-05-12
tbh, thats probably a good choice ;)

the nas box will handle the raid completely transparently to your pc, and just takes all of the headache out of it.

and tbh, you are better off having a backup solution like that, which is removed from the actual pc itself.

Well your problem has been solved one way or another ;)

---

### Post by hawse1978 on 2008-05-12
Yeah. I'm much happier with this solution. 

Cheers for all your help.
Mike

---

### Post by shifty_powers on 2008-05-12
no problem.

tbh the forums and the community around ubuntu is one of the bog reasons why imoved over to linux and stayed with ubuntu ;)

---

### Post by osviweb on 2008-11-22
Guys I have this same motherboard I cannot manage to dual boot on my two sata hd. I have windows on sata1 master in bios(whole disk) and Ubuntu on sata2 slave in bios (first partition).
I've tried hours to install and configure grub on sata1 and also on sata2.
I've tried super grub disk (easy live swap) and many other attempts to get this motherboard dual boot windows and linux.

I don't know about raid solutions and my two hd are separated and both contain important data.

Can you please tell me how to configure bios and system to dual boot on this moterhboard?
thanks:confused:

---

### Post by hawse1978 on 2008-11-23
Hi osviweb

If you use the BIOS settings I specified in post 16 of this thread, you should be most of the way there. I'm not in front of my home PC at the moment so I can't conform which motherboard ports my HDDs are plugged into, but frpom memory I used the two that are side-by-side beneath about 1/4 up the board assuming that the CPU is at the top (hope this makes sense). I found that the onboard SATA port selection is key, since the two orange(?) ports are for the ASUS EZ-RAID which wouldn't work for me.

The BIOS settings specified in post 16 of this thread are pretty important - they were the only settings that I found to work and believe me, I tried them all! 

AFAIK you should only be installing GRUB onto your master drive i.e. Windows

Just for your info, when I built mine, I installed windows clean onto drive 1 and Ubuntu clean onto drive two which installed and configured grub on the windows drive as part of the installation. As such I have not actually installed/configured grub as a separate activity after the fact.

Hope this helps. If you are still struggling after configuring the BIOS as specified, post again to this thread and I will see what I can do you help you out.

Good luck,
Mike

---

### Post by osviweb on 2008-11-23
thanks for the reply
I'll try but at first look setting up sata as ide is a BIG lose of speed of disk I think.
I've just bought a fast disk (raptor) and I'd like not to lose its performances...

---

