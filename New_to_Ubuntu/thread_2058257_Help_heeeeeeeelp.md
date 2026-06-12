---
title: "Help heeeeeeeelp"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by Vincent555 on 2012-09-15
Please help me! i downloaded ubuntu iso then burned it on a cd-r, rebooted my laptop using the live cd i had (i have windows installed on my computer by default btw) everything worked fine, I followed a tutorial in a website called linuxbsdos i think thats its name, I clicked on "something else" to make space for ubuntu, i had this window infront of me
dev/sda
dev/sda1 ntfs ...
dev/sda2 ntfs ~290000 MB
dev/sda3ntfs ..
dev/sda4 ntfs... 
 
so i clicked on the second one and changed the 290 GB into 180GB
 
it took a while, but then instead of "free space" popping out between those 4 patrions, this thingy appeared and it did not let me do anything "unusable ~110000GB" ... i searched everywhere on the internet for a quick fix but lost hope, i quit the installation process and then ubuntu's desktop appeared, shutted down and ejected the ubuntu burned disk. restarted the computer and something about hard disk check prompt/msdos-like window appeared, i let that cd do its thing, after it finished windows started normally and no files were deleted or anything, but there is one problem, i opened "computer managment " window and those 4 patitions appeared:
 
 
(C:) Simple Basic NTFS Healthy(boot, page file, crash dump, primary partition)
HP_RECOVERY(E:) Simple Basic NTFS Healthy (Primary partition)
HP_TOOLS(F:) Simple Basic FAT32 Healthy (primary partition)
System Simple Basic Fat32 Healthy(System, Active, Primary partition)
 
and below all this info , a picture with info about
disk 0
Basic
288.09GB
Online
 
with everything detailed about partitions, between them was 108.26GB Unallocated.:confused::confused::confused:
 
Now if i wanted to get everything back to normal, please give me the steps.
and if i wanted to install Ubuntu without deleting anything , is there a way? if not, please give me the exact steps without getting anything deleted on my C: hard disk partition
 
Please i need serious help!

---

### Post by Epodx64 on 2012-09-15
well I don't really know what you deleted / partitioned so im a bit confused in what direction to send you hypothetically you could install Ubuntu on the unallocated partition it seems like there wasn't anything on there but I really don't know. Did you shrink a partition to get to that amount of unallocated space or just delete something?  If you shrunk it it's probably ok to install over it but if you just picked a partition and deleted it I don't know.

---

### Post by steeldriver on 2012-09-15
Hi, please try to make your thread titles more descriptive in the future - it will help you get the best advice

I think your basic problem is that the disk already has 4 primary partitions

[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)

Also I would *not* recommend using the Ubuntu installer (or any other Linux-based tools) to modify existing Windows partitions - Windows 7 has a very easy disk management tool that lets you shrink partitions without damaging them

---

### Post by Jakin on 2012-09-15
A HDD, maybe not have more than 4 primary partitions. You already have 4 primary partitions, and then an unallocated space. This would be the reason it doesn't show up

You are gonna have to remove something in order to install Ubuntu.. I use HP machines alot, and HP_TOOLs partition is pretty useless. (its made automatically when upgrading the BIOS of the machine afterwhich serves no purpose that i have ever encountered) i removed mine after support for the computer ran out, and would not be recieving more updates- so the 4th primary partition was free to be used for linux.

How old is your machine?

---

### Post by Elfy on 2012-09-15
Please use descriptive titles - this is a support forum so unsurprisingly everyone starting a thread wants help. 
[http://ubuntuforums.org/showpost.php...11&postcount=1](http://ubuntuforums.org/showpost.php...11&postcount=1)

---

### Post by arsenic23 on 2012-09-15
Your Windows 7 install should have software someplace setup to burn recovery discs.  This software should be from your OEM, which I think you said was HP.  I recommend making sure you have burnt those discs before doing anything else.

Afterward you could get away with deleting that recovery partition, but be aware that if you do AND you loose those discs or damage them AND something happens to your Windows install that requires a format and reinstall you will have to get your laptop manufacturer to send you factory discs, normally at a cost of about $10-$25.

---

### Post by Vincent555 on 2012-09-15
> **Jakin said:**
> A HDD, maybe not have more than 4 primary partitions. You already have 4 primary partitions, and then an unallocated space. This would be the reason it doesn't show up

You are gonna have to remove something in order to install Ubuntu.. I use HP machines alot, and HP_TOOLs partition is pretty useless. (its made automatically when upgrading the BIOS of the machine afterwhich serves no purpose that i have ever encountered) i removed mine after support for the computer ran out, and would not be recieving more updates- so the 4th primary partition was free to be used for linux.

How old is your machine?
@jakin
 
soo uh should i delete hp tools partition? will it effect anything on my computer? (like data loss...)
 
here look at this:
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/Delete-HP-Tools-Partition/td-p/479927](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/Delete-HP-Tools-Partition/td-p/479927)
 
someone said do not delete hp tools or hp recovery for it will damage your computer and hp tools has the main bios in it. is he right?
 
please tell me what should i do
 
oh and if i want to backup that hp tools thingy to the c: partition, how do i do it? and what is the best and safest way to delete that HP_TOOLS partition? will right-clicking on it and choosing "delete volume" damage anything or is it completely safe?
 
ty

---

### Post by Jakin on 2012-09-15
Recovery you should never delete. You can do like Arsenic23 said, to gain that space. Then you would have the 4th primary as well- maybe seems safer to do this.

HP_Tools the link says for warranty info, as i had said i removed mine after the warranty was already over- you wont harm anything doing this (i never did anyway), it stores the BIOS update there TEMPORARILY to prepare its transplant to the bios chip- so i would make sure you have all BIOS update- then back up that partition (though i doubt you will ever need it again) and then delete it freeing another primary.

---

### Post by hypnot0ad on 2012-09-15
> **steeldriver said:**
> Hi, please try to make your thread titles more descriptive in the future - it will help you get the best advice

I think your basic problem is that the disk already has 4 primary partitions

[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)

Also I would *not* recommend using the Ubuntu installer (or any other Linux-based tools) to modify existing Windows partitions - Windows 7 has a very easy disk management tool that lets you shrink partitions without damaging them

:popcorn:

---

### Post by Vincent555 on 2012-09-15
> **Jakin said:**
> Recovery you should never delete. You can do like Arsenic23 said, to gain that space. Then you would have the 4th primary as well- maybe seems safer to do this.
 
HP_Tools the link says for warranty info, as i had said i removed mine after the warranty was already over- you wont harm anything doing this (i never did anyway), it stores the BIOS update there TEMPORARILY to prepare its transplant to the bios chip- so i would make sure you have all BIOS update- then back up that partition (though i doubt you will ever need it again) and then delete it freeing another primary.
 
hmm.. what do u mean (so i would make sure you have all BIOS update)? how should i delete it (this is the most important question, what is the safest way to delete the HP_TOOLS partition?)? so final decision, should i delete HP_TOOLS (btw it has that quick web mini operating system in it) or should i forget everything about linux? i downloaded linux just for the sake of learning programming and cause its free, doesn't swallow so much ram like that bitch windows, and that its open source (atleast that is what i heard). 
 
yes i know i know a lot of questions and reading sorry, but those are just cause im concered for any data loss or crash or ....etc . so please u have to be a pro and experienced...

---

### Post by Vincent555 on 2012-09-15
> **Epodx64 said:**
> well I don't really know what you deleted / partitioned so im a bit confused in what direction to send you hypothetically you could install Ubuntu on the unallocated partition it seems like there wasn't anything on there but I really don't know. Did you shrink a partition to get to that amount of unallocated space or just delete something? If you shrunk it it's probably ok to install over it but if you just picked a partition and deleted it I don't know.
 
I shrinked that sda2 partition so that i could get some free space to install linux. but instead of this "free space ..." appearing that unusable section partition appeared and i dont know what to do.

---

### Post by Jakin on 2012-09-15
[http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&docname=c00007682](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&docname=c00007682)

Explains about updating your HP bios to the newest (if there is any)

[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu) (this is what everyone else has linked of how to back up that partition)


Then from fdisk on windows7 just right click delete after you have done all that :)

---

### Post by Bartender on 2012-09-15
Vincent555, you need to stop whatever it is you're doing and take a few deep breaths.

You don't know what you're doing, you don't know what you did, you're feeling kinda panicky.  Perfect recipe for disaster.

Did you make recovery discs?  I thought that all PC's come with a recovery disc app but an HP Probook I bought a coupla years ago did not.  I had to give HP money, then they sent me discs.

If you don't have discs, and/or can't make them, then you need to just stop and come up with a plan.

As has been said, you can't have more than four primary partitions.  What you've done so far is balled things up by creating an unallocated chunk on your HDD that can't be used for anything.

Charging forward and deleting HP_TOOLS might get you out of the woods and might not.  

Flashing the BIOS???  That's about the last thing you want to do right now.  Flashing the BIOS can be very risky, and it wouldn't change the situation you've created one bit.

If you reinstall Windows from recovery discs you will almost certainly have fewer partitions, which would allow you to install Ubuntu.  I reinstalled Windows 7 to my Probook a few days ago.  There's just one big C: Drive instead of 4 primary partitions.  EDIT: I should mention that when I reinstalled Windows, then moved on to the HP "Accessories" disc, I only installed the drivers.  Did not install all the HP Support Center stuff.  Almost every time I started this laptop before the reinstall, HP Support Center would come up, say it needed to get super-special HP updates, then spend an hour doing whatever it was doing.  I never saw any improvement.  It runs better without all the HP bloatware.  I can always update drivers from the HP Support site directly.

---

### Post by Jakin on 2012-09-15
> **Bartender said:**
>  

Flashing the BIOS???  That's about the last thing you want to do right now.  Flashing the BIOS can be very risky, and it wouldn't change the situation you've created one bit.

Thats why i linked him/her to the site about flashing if needed, when i flashed my bios the HP support app, (with linux already on a partition) made a primary partition, and screwed up my whole partition table at reboot.
So IF he needs the bios, get it done before installing linux, and he wont run into this problem- i feel its much safer if the HP support site say he/she needs it- to get it done first.

---

### Post by Bartender on 2012-09-15
OK, well, either way it's clear that Vincent fired first and aimed later.  I'm just trying to get him to stop before he kills Windows and has no recovery discs.

Nobody should be messing with their partitions without a basic understanding of: 1) partitions in general, and 2) the partitions on their PC.  

I'll admit that my first forays into partitioning for Ubuntu were undertaken without 1) or 2). ;)

---

### Post by Jakin on 2012-09-15
I understand :) I was just trying to cover all bases, before saying get rid of that partition. I didn't mean to scare about the BIOS thing.

---

### Post by JKyleOKC on 2012-09-15
> **Vincent555 said:**
> I clicked on "something else" to make space for ubuntu, i had this window infront of me
dev/sda
dev/sda1 ntfs ...
dev/sda2 ntfs ~290000 MB
dev/sda3ntfs ..
dev/sda4 ntfs... 
 
so i clicked on the second one and changed the 290 GB into 180GBDidn't anyone else notice that he simply changed the size of the partition, using the install disk's partitioner, instead of having Windows shrink the partition properly? It's almost certain that this destroyed data on that partition, that cannot now be recovered easily.

Later messages seem to imply that the partition he reduced in size was the RECOVERY partition, which would mean that any attempt to recover from this error might well make the whole system unusable. The damage has already been done. At this point, even ordering a set of recovery disks from HP might not suffice to fix things. I did order such a set myself a couple of weeks ago and the cost was only $16 USD, a fair price for insurance against disaster even though I never expect to use them.

Depending on the specific model of HP machine involved, the four-partition limit may no longer apply. At least some recent HP systems use UEFI booting instead of the traditional MBR-bios method; if that was the case, those instructions from linuxbsdos weren't fully applicable! I followed them myself, and the results put me in a near-panic state for a time -- but eventually got things corrected. There's a thread at [http://ubuntuforums.org/showthread.php?t=2048457](http://ubuntuforums.org/showthread.php?t=2048457) telling all about it.

For the OP: don't do anything more to try to fix things at this point. Just enjoy the working Windows package, and if you can do so, create or buy that set of recovery DVDs. Hopefully the experts who helped me recover (Yannbuntu and OldFred) will join this thread and offer suggestions that may get your space back!

---

### Post by Vincent555 on 2012-09-15
> **Bartender said:**
> Vincent555, you need to stop whatever it is you're doing and take a few deep breaths.
 
You don't know what you're doing, you don't know what you did, you're feeling kinda panicky. Perfect recipe for disaster.
 
Did you make recovery discs? I thought that all PC's come with a recovery disc app but an HP Probook I bought a coupla years ago did not. I had to give HP money, then they sent me discs.
 
If you don't have discs, and/or can't make them, then you need to just stop and come up with a plan.
 
As has been said, you can't have more than four primary partitions. What you've done so far is balled things up by creating an unallocated chunk on your HDD that can't be used for anything.
 
Charging forward and deleting HP_TOOLS might get you out of the woods and might not. 
 
Flashing the BIOS??? That's about the last thing you want to do right now. Flashing the BIOS can be very risky, and it wouldn't change the situation you've created one bit.
 
If you reinstall Windows from recovery discs you will almost certainly have fewer partitions, which would allow you to install Ubuntu. I reinstalled Windows 7 to my Probook a few days ago. There's just one big C: Drive instead of 4 primary partitions. EDIT: I should mention that when I reinstalled Windows, then moved on to the HP "Accessories" disc, I only installed the drivers. Did not install all the HP Support Center stuff. Almost every time I started this laptop before the reinstall, HP Support Center would come up, say it needed to get super-special HP updates, then spend an hour doing whatever it was doing. I never saw any improvement. It runs better without all the HP bloatware. I can always update drivers from the HP Support site directly.
 
thx for the quick reply
I do have a probook, and i dont have discs and i cant use them! and i dont have any empty usbs at the moment DX !!!!!!!!  when u said "What you've done so far is balled things up by creating an unallocated chunk on your HDD that can't be used for anything." does that mean that i can not use this partition for anything at all, not even installing linux?! even if i want to extend back the sda2 (windows's c :  partition) , IT WONT WORK????? HOLY BALLS OF FIRE!! *sigh*
 
some say that i had a pro book once and deleted the hp_tools partition with no problems, while other say if u delete it, it will mess up your computer and u should say good bye to it :(  Please tell me should i delete HP_TOOLS partition or what?

---

### Post by Jakin on 2012-09-15
Firstly i want to say, is i never meant to scare you Vincent555. 

You have unallocated space, and so its blank, you can manipulate that space back into an existing primary partition, it isn't gone forever or something. 


We are all just saying that linux needs its own primary, and in order for this to happen, based off the info you gave in the OP, you will have to remove something. 

I personally have removed HP_TOOLS from 3 hp's (given they were not Pro books, i had no way of knowing this is what you had.. thats my fault for not asking). 
I had no issues doing this.. but i cannot account for what others have said about removing it :(

---

### Post by Bartender on 2012-09-15
*Please tell me should i delete HP_TOOLS partition or what?*

**NO**

As JKyle says; try to fix things.  Don't keep making them worse.  JKyle brings up a good point that I forgot about.  You laptop may be UEFI.  No, wait, JKyle, if it was UEFI wouldn't there be one of those UEFI boot partitions in the OP's screenshot?  I have very little experience with UEFI so can't say for sure.

What do you mean you don't have any discs and you can't use them??

So you're saying you have a Probook??  Which one?  No matter.  Here's a link to a discussion [about getting discs]("http://h30434.www3.hp.com/t5/Notebook-Recovery/Restore-HP-Probook-4520s-to-factory-settings/td-p/887223").  I called HP on the phone to get mine.  They weren't expensive.

You should get on the phone right now and order those discs.  Wait til they arrive before doing anything else.

Figure out whether your laptop is UEFI or plain old BIOS.  I think it's BIOS but not sure.

When I wrote "you can't do anything with that partition" I didn't mean it was lost forever.  I just meant that with four primary partitions (and assuming BIOS, not UEFI) you can't install Ubuntu to it.  The safest thing to do right now would be to leave it alone.  The next safest thing would be to use the Windows partitioner to put it back the way it was.

Buy the recovery discs.  While you're waiting for their arrival, research the situation.  It might be a good idea to sign up at the HP forums.  There are some knowledgeable folks who could probably give you very specific answers for your specific laptop, or at least that group of laptops.

---

### Post by Vincent555 on 2012-09-15
> **JKyleOKC said:**
> Didn't anyone else notice that he simply changed the size of the partition, using the install disk's partitioner, instead of having Windows shrink the partition properly? It's almost certain that this destroyed data on that partition, that cannot now be recovered easily.
 
Later messages seem to imply that the partition he reduced in size was the RECOVERY partition, which would mean that any attempt to recover from this error might well make the whole system unusable. The damage has already been done. At this point, even ordering a set of recovery disks from HP might not suffice to fix things. I did order such a set myself a couple of weeks ago and the cost was only $16 USD, a fair price for insurance against disaster even though I never expect to use them.
 
Depending on the specific model of HP machine involved, the four-partition limit may no longer apply. At least some recent HP systems use UEFI booting instead of the traditional MBR-bios method; if that was the case, those instructions from linuxbsdos weren't fully applicable! I followed them myself, and the results put me in a near-panic state for a time -- but eventually got things corrected. There's a thread at [http://ubuntuforums.org/showthread.php?t=2048457](http://ubuntuforums.org/showthread.php?t=2048457) telling all about it.
 
For the OP: don't do anything more to try to fix things at this point. Just enjoy the working Windows package, and if you can do so, create or buy that set of recovery DVDs. Hopefully the experts who helped me recover (Yannbuntu and OldFred) will join this thread and offer suggestions that may get your space back!
 
dude, i have reduced the size of that C : partition, not the recovery one, i never touched that one... 
is it possible to get windows and everything back to its original state? (u know, extend the c : partition back to its original size). cause this whole linux/hp arquments and tutorials and stuff are really just DXDXDX... F*** i just want to throw the laptop out of the window and lose all hope DX man i just wish i could install linux for my studying than that a**hole windows... he just likes to swallow ur whole ram for no reason (even though i have 6GB, i have alot of work to do). while linux is just easy to use, and doesnt take a big *** chunk from ur hdd and ram like windows :( btw i have HP probook 4530s
 
EDIT: i am gonna say it again, is it possible to get that unallocated space back to its original partition? if so, please tell me how or direct me with a link to help me with this problem. thx :)

---

### Post by Jakin on 2012-09-15
> **Vincent555 said:**
> EDIT: i am gonna say it again, is it possible to get that unallocated space back to its original partition? if so, please tell me how or direct me with a link to help me with this problem. thx :)


From fdisk in win7; Right Click on the C: partition and click "extend partition", and you should get back your original state.

---

### Post by arsenic23 on 2012-09-15
> **Vincent555 said:**
> EDIT: i am gonna say it again, is it possible to get that unallocated space back to its original partition? if so, please tell me how or direct me with a link to help me with this problem. thx :)

In Windows just go into the administration tools in the control panel.  From there you should be able to find Disk Management.  You can expand the partition back to its original size from there.   **BUT**, before messing with partitions again (or at all) you really really should burn your recovery discs.  If there isn't a program in the start menu for doing this then just boot into your recovery partition from the post menu when you first start up your computer and look for it there.

This all comes from Microsoft asking manufacturers to not include discs with new PCs anymore.  Someone thought it would cut back on piracy.

---

### Post by Vincent555 on 2012-09-15
> **Jakin said:**
> From fdisk in win7; Right Click on the C: partition and click "extend partition", and you should get back your original state.
 Please be more detailed, i did what u told me, then this (the attachment photo) popped out, now what?

---

### Post by Jakin on 2012-09-15
Next and then, on the following window prompt "finish".

---

### Post by JKyleOKC on 2012-09-15
> **Bartender said:**
> JKyle, if it was UEFI wouldn't there be one of those UEFI boot partitions in the OP's screenshot?  I have very little experience with UEFI so can't say for sure.My HP P2-1120 is UEFI and I never saw an UEFI boot partition in the screen shown by Vincent's screenshot. I only found out about UEFI a day or so later while quietly pulling out my hair trying to get Linux to boot.

Apparently the installer on the Live CD is supposed to detect which scheme is in use, and run the Live CD in that mode. Perhaps it's using the HDD size to make the determination. My HD is only 500 GB, which could be set up either way although multi-TB drives require gpt partitioning. However HP apparently is now using UEFI across the board to simplify things at their end. In any event, my Linux install was **non**-EFI while Win7 **was** EFI and that was the cause of my own problem!

There's a great explanation of the EFI problem at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) which includes methods for determining which is being used on any specific system...

---

### Post by Bartender on 2012-09-15
So, Vincent, you have a 4530S?  Mine is a 4520S.  I bought it as a 32-bit version.  When I ordered discs, HP sent me a 32-bit install disc *and* a 64-bit install disc.  
I put in an SSD and installed 64-bit.  Then I installed the drivers from the HP drivers disc.  There's just one big C: Drive now.  I'll betcha that if you were to buy the discs, then reinstall, you would only have one partition.  From there installing Ubuntu would be easy as pie.

---

### Post by Vincent555 on 2012-09-16
> **Bartender said:**
> So, Vincent, you have a 4530S? Mine is a 4520S. I bought it as a 32-bit version. When I ordered discs, HP sent me a 32-bit install disc *and* a 64-bit install disc. 
I put in an SSD and installed 64-bit. Then I installed the drivers from the HP drivers disc. There's just one big C: Drive now. I'll betcha that if you were to buy the discs, then reinstall, you would only have one partition. From there installing Ubuntu would be easy as pie.
 
I hope what ur saying is true man. i'll do just that in a computer shop and try installing linux on my hp :)
 
btw does Netbeans IDE  for java work on linux?
i saw just a version of windows and mac, but never saw one for linux :(
it is the easiest IDE to work with on java

---

### Post by Jakin on 2012-09-17
> **Vincent555 said:**
> I hope what ur saying is true man. i'll do just that in a computer shop and try installing linux on my hp :)
 
btw does Netbeans IDE  for java work on linux?
i saw just a version of windows and mac, but never saw one for linux :(
it is the easiest IDE to work with on java


Bartender is correct, you would end up with one large C: partition without the extras- and thus gain alot of free space. (I think its such nonsense how a retail setup has a SYSTEM partition (and others), just to boot into win7 partition- its like they are purposely filling the drive, to scare others from wanting to install another OS, like linux..)
I myself didn't immediantly suggest it, as you would be starting all over with win7.

As far as netbeans IDE, you will find it in the Ubuntu Software Centre :)

---

### Post by Bartender on 2012-09-17
Yeah, Jakin, I realize suggesting a reinstall from recovery discs is kinda like jumping out of a perfectly good airplane.  But if installing from the recovery discs creates a clear path to dual-boot, whereas the tortured mess that came with the laptop does not (and I share your suspicion that the manufacturers do this to discourage experimentation) then what the hey.

I'll go one step further.  Get the recovery discs, then create a GParted bootable CD.  Use the GParted LiveCD to wipe all data from the HDD, then create an NTFS primary parition out of the first half the drive.  Install W7 to that half.  Then install Ubuntu to the rest.  IMO this is much more straightforward than installing Windows to the whole drive, then trying to get it to move over.

The above is only applicable if your laptop is old-school BIOS!!  I don't know anything about installing to an EFI machine and don't want to give out bad advice.

---

