---
title: "A few problems, triple boot, recovery partition etc."
date: 2012-01-25
forum: New to Ubuntu
---

### Post by Resplendent Raven on 2012-01-25
Hello all,

I have been using Ubuntu (9.04) for about 2,5 years now.
I want to get a new Linux OS, not quite sure which one yet, but i tried 11.10 and i get the dim screen bug with that, so i'm thinking about 10.04, Mint or perhaps Kubuntu.
Anyway i still want to keep Ubuntu 9.04 cause i got it working quite to my liking, so basically what i want to do is setup a triple boot system.
Now the problem is that when i started with Ubuntu i just wanted to try it out not sure if i would like it, but i basically love everything about the opensource concept and Ubuntu (even the name/concept itself).
But i only used 18GB at the time, and didn't setup a home partition.
The other part of the problem is that i still want to keep Vista but it got infected once and i basically want to shrink the Vista partition and move about 40GB to the extended Ubuntu partition, but Vista isn't letting me do that, as i understand it it's because it places the MFT at the end of it's partition.
So i was thinking of just shrinking the volume with Gparted and then using my recovery partition, to reinstall Vista on the now smaller partition.

My HDD looks like this:
Sda1 is the recovery partition, Sda2 is the Vista partition, Sda3 is a Data partition and Sda4/5/6 are Ubuntu 9.04

So i have a few questions about this:

1. If i shrink Vista and possibly destroy the MFT, will i still be able to boot the other partitions and more importantly use the (Acer) eRecovery partition? (Is there only one central MFT or does every partition have it's own MFT)

2. Is there someone who has ever used the Acer eRecovery partition?
I am not sure if i will wipe my whole HDD or just the Vista partition, also will i be able to use the eRecovery partition again? (i searched on the internet but couldn't really find a clear answer to this)
Although a video that i watched on Youtube seems to suggest it will only clear the specific partition, i just found a faq which would seem to suggest this is the case - [http://support.acer.com/acerpanam/desktop/0000/Acer/PowerFe/PowerFefaq4.shtml](http://support.acer.com/acerpanam/desktop/0000/Acer/PowerFe/PowerFefaq4.shtml)
(not sure how compatible that faq is though since my partition is 13GB and they talk about it being 2GB)
I however find another possible problem with my idea in the faq and also in the help files 
> **Q**: Can I change the space reserved for the D: drive and allocate it for the C: drive.
**A**: No. ACER does not ship software to change partition structure. 
 The partition structure is also fixed during the CD recovery process and cannot be changed.And the help file on Vista contains a line like this > Acer eRecovery Management needs a specific hdd partitionstructure to function. If the system detects that the hdd doesn't use this structure, the Acer eRecovery Management function will be disabledI wonder if that means that i can't shrink the Vista volume, also since i already created an extended Ubuntu partition i wonder if it will still work.
The fact that the faq says the partition structure is fixed during install, do they mean fixed as in unchangeable or fixed as in 'created anew'.
I did also create extra backup dvd's when i first installed the system, but my dvdplayer has become glitchy, fails most of the time and also tends to scratch my dvds, so using that isn't really an option.

3. My last question should be the most simple one to answer, if i create a new logical partition with a new OS, should i also create a new swap partition or just enlarge my current one (it's only about 800mb)?
I would also like to create a Home partition, but i am not sure if this will conflict with the home folder in my current 9.04 root partition? 

Well my "3" questions are actually quite alot :-\"
I hope some of the more experienced posters here will be able to help me on this

PS here is a video showing the Acer recovery partition and how it specifically defines how it will only reset/reinstall the (vista) partition - [http://www.youtube.com/watch?v=pmVT0Z9r6_Q](http://www.youtube.com/watch?v=pmVT0Z9r6_Q)

---

### Post by Resplendent Raven on 2012-01-26
Also not sure how this would affect my GRUB.
Perhaps i should use a program like Clonezilla to copy the recovery partition and the rest of my hdd?
I would appreciate some feedback on how to continue, even if you don't have clear answers to my questions above, i would still like to hear if my plans sound reasonable or foolish, and if i perhaps should try something else...
All i know now is that the overall uncertainty isn't really productive and i would love to start doing something to work towards my goal.

---

### Post by Miljet on 2012-01-26
1. Not sure how to answer this as I have no idea what you are referring to as MFT.

2. Have no idea. I don't have an Acer. I did read the link you posted and you are right, it is rather confusing.

3. You only need one swap partition. All Linux installs can and will use the same swap partition. The swap partition can be any size you choose. If you hibernate your computer, the swap needs to be at least as big as your installed RAM because during hibernation the entire contents of RAM is written to the swap partition.
A /home partition for one operating system will have no effect on the /home directory that is included in the partition of another operating system. I do not recommend sharing a separate /home partition between different operating systems. Each operating system is likely to have different programs, or different versions of the same programs, installed. That could lead to conflicts in the configuration files.

A suggestion: If you would open a terminal and enter ```
sudo fdisk -lu 
``` and copy the results here, we would be able to see what you have and offer better answers to your questions.

---

### Post by Resplendent Raven on 2012-01-26
> Schijf /dev/sda: 320.0 GB, 320072933376 bytes
255 koppen, 63 sectoren/spoor, 38913 cilinders, totaal 625142448 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x50a5b170

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1            2048    27265023    13631488   27  [onbekend]
/dev/sda2   *    27265024   326201343   149468160    7  HPFS/NTFS
/dev/sda3       326201344   587759607   130779132    7  HPFS/NTFS
/dev/sda4       587770216   625137344    18683564+   5  Uitgebreid
/dev/sda5       587770218   623482649    17856216   83  Linux
/dev/sda6       623482713   625137344      827316   82  Linux wisselgeheugen
It's in dutch, don't know how to change the language of the output, anyway i guess you will still be able to get the needed information from this, and else i can translate if needed (wisselgeheugen is swapmemory for example).

MFT is the [Master File Table]("http://en.wikipedia.org/wiki/Master_File_Table#Internals"), i have read some links about how hard it can be to shrink Vista and it appears that Vista places (parts of) the MFT at the end of the partition, even if there are many Gigs available in between.
Moving the MFT seems to involve switching stuff of in Vista and even deleting important system files, downloading certain defrag programs, and even then i have seen mixed reactions about how succesful the process is.
That's why i'd rather just use the recovery partition, since Vista being infected once would benefit from that anyway.

---

### Post by Mark Phelps on 2012-01-27
> 1. If i shrink Vista and possibly destroy the MFT, will i still be able to boot the other partitions and more importantly use the (Acer) eRecovery partition? (Is there only one central MFT or does every partition have it's own MFT)
It won't destroy the MFT -- as long as -- you shrink it using the Vista Disk Management Utility.  Using GParted or the Ubuntu installer (i.e., slider) to shrink it risks filesystem damage.

> 2. Is there someone who has ever used the Acer eRecovery partition?
I am not sure if i will wipe my whole HDD or just the Vista partition, also will i be able to use the eRecovery partition again? 
Haven't used the ACER recovery process but have used HP's -- and in those cases, the entire hard drive was reformatted and rewritten.

One catch in all of this is, if you shrink the OS partition and then fill the new space with another filesystem, the recovery program can get confused by the other filesystem and refuse to work -- thus defeating the whole idea of having a recovery partition.

A better solution (for restoring) is to do the following:
1) Shrink the Vista partition using the Vista Disk Management utility
2) Boot into Vista a couple of times to let the filesystem make any needed adjustments
3) Download and install the FREE version of Macrium Reflect (MR).
4) Use MR to image off your Vista install to an external drive
5) Use the MR function to create a bootable Linux CD

NOW, you have a way to restore your Vista install that does not need the Recovery partition or the ACER recovery tool.  And, you can erase your Recovery partition and reuse the space.

---

### Post by Resplendent Raven on 2012-01-27
> It won't destroy the MFT -- as long as -- you shrink it using the Vista Disk Management Utility. Using GParted or the Ubuntu installer (i.e., slider) to shrink it risks filesystem damage.I am aware of this, but the problem is that i can't shrink it using the Vista Disk Management Utility. It gives exactly 0 bytes available to shrink even though i have over 40GB of free space. Reading links about this has shown that in almost all cases this is caused by the MFT blocking the end of the partition.
This is why i am thinking about the 'solution' proposed in my 1st post.

> Haven't used the ACER recovery process but have used HP's -- and in those cases, the entire hard drive was reformatted and rewritten.Pretty sure this isn't want the ACER eRecovery process does.
This is from the faq :

> **Q**: Will the backup include the contents in the C: and D: drive.
**A**: No, the backup is only performed on the C: drive.
**Q**: Is the D: drive overwritten when reloading the system with the HDD images or burned backup CDs or Recovery Media. 
**A**: No only the C: drive is written to when reloading the HDD.
> One catch in all of this is, if you shrink the OS partition and then fill the new space with another filesystem, the recovery program can get confused by the other filesystem and refuse to work -- thus defeating the whole idea of having a recovery partition.Yeah that is what i am afraid of too and one of the main reasons i have decided to share this problem.
I have read a thread here about people accidentally using the eRecovery module and losing access to their Ubuntu partition, i am not sure about this but i reckon they must have somehow taken this hdd space from their original windows partition.
Else i can't explain their accounts in context with the statements given in the Acer faq above.

This is why i am wondering if i perhaps should clone my hdd and recovery partition before, but i have never done such a thing before and am not sure if this would keep the recovery function intact (and all other important system functions).

Macrium Reflect is windows based i take?, i rather have a clone program that i could use using a (Linux) Live USB, in case all else goes wrong.
Someone has mentioned Redo-backup; if cloning is worthwhile then i will clone the recovery partition beforehand, only have to sort out which program to use, Clonezilla looks a little complex by what i have seen thusfar.

I am not bothered by the Vista recovery partition itself and would like to keep it, perhaps one day when i or rather my gf finds no use for Vista anymore i will delete it

@ Miljet

> A /home partition for one operating system will have no effect on the /home directory that is included in the partition of another operating system. I do not recommend sharing a separate /home partition between different operating systems. Each operating system is likely to have different programs, or different versions of the same programs, installed. That could lead to conflicts in the configuration files.So one of the main reasons for having a home partition is to keep your files safe when upgrading the OS ??

---

### Post by Miljet on 2012-01-27
> So one of the main reasons for having a home partition is to keep your files safe when upgrading the OS ??
Yes, when doing a clean install to repair or upgrade, the partition containing the OS normally gets reformatted. Having your personal files in your /home in a separate partition keeps them intact.

---

### Post by Resplendent Raven on 2012-01-28
@ Mark Phelps 

Why do you recommend Macrium Reflect specifically over Clonezilla, Redobackup etc. ?
I'm thinking about cloning the recovery partition, Vista and my Ubuntu partition, and perhaps even the whole hdd image too (with Clonezilla).
If i do this first and then try to shrink and recover Vista, i should be able to return everything back to normal if it all fails, right?
What i would do is shrink Vista (with Gparted) and leave the free space untouched, test if Vista runs and if not recover, that way the freed space should still be available, and even when restoring the clonezilla image would fail, i should be able to resize the partition so that it would fit.
That's my current plan and i think in theory it should work, but i welcome all to point out it's flaws.

@ Miljet

If i would do a new install instead of upgrading, would i have to manually select that home partition and uncheck format? or how would that work exactly?

---

### Post by Miljet on 2012-01-28
The partition that holds your /home should not be affected unless you select it. Normally, the only partition that is reformatted is the one you are installing the operating system to. And you can even elect to not format that if you wish. That way all your installed programs and settings will be preserved.

---

### Post by Resplendent Raven on 2012-02-02
[B]UPDATE


[/B]I have been defragging and backing up my hdd with PerfectDisk 12.5 & CloneZilla for the last couple of days.
You can only use PerfectDisk 12.5 free for 10 days, but the program is a really good defragment tool, with it i managed to change the 0byte shrink size of my Vista partition to 16GB->30GB+ and eventually beyond my desired 50GB.
Having freed up all the needed space and made multiple backups to be safe, my girlfriend still wanted me to restore Vista to a pristine state.
So with still a little bit of anxiety left i selected the Vista recovery option from the GRUB loader.
Here again i encountered the ambiguous wording by Acer that it would return my system to factory settings but also that it would (only) clear the selected ACER (Vista) partition, 
Well i went ahead and it succesfully restored my Vista to factory settings as claimed, and after the initial setting up i could see that my DATA partition indeed was untouched as the Faq claimed.
I should add that instead of shrinking Vista first i decided it would be safer to try it after the recovery, so that is the next step i will be taking.
My GRUB loader got destroyed by the recovery process, but since i have Ubu10.04 on my external hdd with GRUB access to my intern hdd i was able to boot into my 9.04 too.
I also booted into my recovery partition again to check if it was still active, but after booting into the partition the factory restore option was greyed out, so it seems that the functionality is single use only (i have cloned the recovery partition too, so perhaps i'll try to restore it later on).

When i'm finished moving my space and installed my 3rd OS i will update this thread again and mark it as solved. 

Do i btw need to restore my GRUB first or will my new Ubuntu install detect all other bootable partitions ?

---

### Post by Resplendent Raven on 2012-02-03
So with the recovery performed i shrank the Vista partition without any problems.
However merging the freed space with the adjacent data partition somehow wasn't possible for the Vista partition tools so i downloaded  Minitool's Partition Wizard and with that merged the free space without any problems, after that i performed 2 defrags on the data partition and shrank it with the Vista tools again. 
Now i merged the free space to my extended partition using GParted so i was finally ready for installing the new Linux OS, i decided it would be Ubuntu 11.10 afterall.
For some reason on my first 2 attempts my Live usb was very slow and created several errors while trying to install, so i performed a low level format and tried again which seemed to help alot (i have been trying several distro's using Unetbootin and the Live USB creator, and guess this has to do with it somehow)
As hoped Ubuntu 11.10 rebuilt a working GRUB with all my bootable partitions on it, the screen dimming was there as feared but managed to solve it by using this method -[http://askubuntu.com/questions/79983/screen-brightness-resets-to-minimum-after-every-reboot](http://askubuntu.com/questions/79983/screen-brightness-resets-to-minimum-after-every-reboot) .

Well it seemed my original scheme had worked quite well with some minor adjustments here and there.
But as mentioned in the post before i would try to check if the recovery function was still available when i had a new GRUB, so i did as intended and the option was still greyed out, no real problem for me since i have made a redundant amount of backups by now.
However upon rebooting i was disgruntled by the following message: 
"error: no such partition.
grub rescue>"
Having booted into the recovery partition multiple times by then i really hadn't thought that would happen although i had read about it here - [http://ubuntuforums.org/showthread.php?t=1836303](http://ubuntuforums.org/showthread.php?t=1836303)
I booted my Ubuntu 11.10 LiveUSB again and saw that the newly made logical partitions assigned to 11.10 had all been deleted, so seemingly by only booting into the recovery partition it somehow aggressively looks for the sectors (?) assigned to the original Acer/Vista partition and probably when it isn't in the NTFS format anymore it just deletes the filesystem on it to make it accessible (or something like that), because i also assigned 10 extra GB from the original Vista partition to my data partition and couldn't discover any damage there.
Luckily for me Ubuntu 11.10 had just been installed and i could just reinstall and it took me only about a half hour to restore it to the way i had set it up just before.
But let this be a clear warning to all others who have Acers with similar setups.
I now know by experience you can pretty much do with the Data partition what you want and recover after, but when you use the Vista partition you can't recover (not even boot the recovery partition!) without losing all (probably non-ntfs) Linux partitions.
Needless to say i went looking for a way to delete the recovery loader from the GRUB menu straight away and i suggest all others who used their Acer partition for Ubuntu would do the same.

Hope this information can be of use for someone and think my experience has atleast brought to light the intricacies of the ambiguous wording of the Acer eRecovery function.
The process itself was quite straightforward and most time is lost by backing up, defragging and the recovery process itself.

---

