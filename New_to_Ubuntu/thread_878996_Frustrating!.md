---
title: "Frustrating!"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by DJH10 on 2008-08-03
New here so hi all :)

Been a long time Windows user,XP,64XP&64bit Vista.Wanting to try something new and saw Ubuntu,looked nice so i installed it along side windows just to get a feel for it and after a few days trying it i felt like it was time to change.
So after d/l the cd,checking it for errors etc i decided to install Ubuntu!
After installing it i get "boot disc failure,insert system disc&press enter" even though i've set up all the boot up devices as 'hard drives' in the bios,it keeps trying to boot for the cd??


What have i done wrong??

---

### Post by 720iD on 2008-08-03
> **DJH10 said:**
> New here so hi all :)

Been a long time Windows user,XP,64XP&64bit Vista.Wanting to try something new and saw Ubuntu,looked nice so i installed it along side windows just to get a feel for it and after a few days trying it i felt like it was time to change.
So after d/l the cd,checking it for errors etc i decided to install Ubuntu!
After installing it i get "boot disc failure,insert system disc&press enter" even though i've set up all the boot up devices as 'hard drives' in the bios,it keeps trying to boot for the cd??


What have i done wrong??

you say you have "set all the boot up devices as hard drives" 
what do you mean by that?

---

### Post by DJH10 on 2008-08-03
1st boot device,2nd boot device etc but it still wants to boot from cd?

---

### Post by K2712 on 2008-08-03
Do you have multiple hard drives installed?  Can you boot from the live-cd?

---

### Post by jolx on 2008-08-03
it's sounding like the message windows gives when its been screwed up

are you sure that you dual booted properly?

---

### Post by DJH10 on 2008-08-03
> **K2712 said:**
> Do you have multiple hard drives installed?  Can you boot from the live-cd?

I have 3 h/d's installed,1 60gig IDE,the other 2 SATA.
I've intalled Ubuntu on the IDE one.Each time after restarting i get the same message so i stick the cd back in and the whole process of installing starts over again :confused:

---

### Post by bobnutfield on 2008-08-03
This message is telling that the first boot disk is not being recognized.  As previously mentioned, if you have multiple disks, did you rearrange any cables before you installed?  If not, run the live cd again, open a terminal and type:

> fdisk -l

This is to make sure your drives are bing recognized correctly.  Post this information back if you can,

---

### Post by jolx on 2008-08-03
and the hdd that grub is installed on needs to be booted from

---

### Post by DJH10 on 2008-08-03
> **bobnutfield said:**
> This message is telling that the first boot disk is not being recognized.  As previously mentioned, if you have multiple disks, did you rearrange any cables before you installed?  If not, run the live cd again, open a terminal and type:



This is to make sure your drives are bing recognized correctly.  Post this information back if you can,

Urmmm,what do you mean by "open up a terminal":oops:
Sorry but i'm very new to this! And no i haven't re-arranged any cables etc

---

### Post by jolx on 2008-08-03
boot into the live cd again then go to Applications -> Accessories -> Terminal

---

### Post by bobnutfield on 2008-08-03
Did you install from a live CD (a running desktop from a cd) or did you install directly from a cd?  If you installed directly from cd, then my suggestion is not a solution.  If you have access to a live cd (knoppix, ubuntu or any other version will work), this boots a cd to a running desktop.  A terminal is the famous command line and you can access it from the live cd desktop.  The command I mention in my previous post would issue a listing of the hard drives on your computer and how they are partitioned and formatted.

I can think of nothing that would happen during the install process of Ubuntu that would disable the recognition of the first boot disk.  I usually see this when someone changes drive order before installing.  This confuses the BIOS and fails to find the first boot disk.

---

### Post by DJH10 on 2008-08-03
Right i've typed in fdisk -l but it just returns with ubuntu@ubuntu:

What i have noticed is that my h/d's have been split like this for some reason:
2.2gb media
15.8gb media
37gb media
37.7gb media
40gb media and one named local disk?

The 2.2,15.8 and the 37.7 gb h/d's have all the same files on them,"bin,boot,cd rom,dev" etc :confused:

---

### Post by muteXe on 2008-08-03
maybe type in:
sudo fdisk -l

---

### Post by bobnutfield on 2008-08-03
Sorry, I should have asked you to type:

> sudo fdisk -l

See what that returns

---

### Post by DJH10 on 2008-08-03
Cheers for the help so far :)

Typed in sudo fdisk -l and it has returned with a lot of stuff regarding my h/d's
It's has listed the 3 h/d's i have,the 60 gb,the 80gb(split into 2) and the 37gb.
What do you need to know from the info this has listed?

---

### Post by bobnutfield on 2008-08-03
I may be able to help you, but I must leave the computer for about an hour.  If no one else chimes in before I return, I will be back.  I would need to know two things:

Which drive contains your first boot disk and where you told Ubuntu to install grub.

---

### Post by DJH10 on 2008-08-03
Cheers Bob,i've attached a screenshot of the info of the h/d's if thats any good to you?

---

### Post by Ed J on 2008-08-03
you should have a device listed that has an * under the boot column.
like this
/dev/sda1  *
Oh I just looked at the screenshot, you have it.  Is that the IDE drive?
It looks like your boot drive is not the drive with linux partition.

---

### Post by DJH10 on 2008-08-03
No,the IDE is the 60 gb one on which i want to install Ubuntu.

Back in 15mins

---

### Post by Ed J on 2008-08-03
you said "which i want to install Ubuntu"
I thought you installed it already

---

### Post by DJH10 on 2008-08-03
I have but i keep getting 'boot disc failure' every time i reboot after finishing the installation

---

### Post by bobnutfield on 2008-08-03
OK first things first.  During the installation of Ubuntu, where did you tell it to install Grub (the bootloader)?

Based on fdisk, I think you have the following setup:

Disk 1 (sda):     Windows XP
Disk 2 (sdb):     Storage for your Windows files
Disk 3 (sdc):     Your Ubuntu installtion.

The boot record for sda is not there or the disk has failed.  Is your first disk IDE?  I am assuming it is.  Post this information back

---

### Post by DJH10 on 2008-08-03
> **bobnutfield said:**
> OK first things first.  During the installation of Ubuntu, where did you tell it to install Grub (the bootloader)?

Based on fdisk, I think you have the following setup:

Disk 1 (sda):     Windows XP
Disk 2 (sdb):     Storage for your Windows files
Disk 3 (sdc):     Your Ubuntu installtion.

The boot record for sda is not there or the disk has failed.  Is your first disk IDE?  I am assuming it is.  Post this information back

It didn't ask me to install 'Grub' any where :confused:

With regards to the disks,disk 1 has nothing on it,not even windows,disk 2 has files i wanted to save,music etc and disc 3 should have Ubuntu on it!

I'm going to attempt to re-install again,i think im messing up where at the 'partition disc space' part.Which one should i choose?i've been choosing the 'guided,use entire disc' and using the 60gig hd(the IDE one) which is the third on the list.

---

### Post by bobnutfield on 2008-08-03
OK, I see your problem.  You have installed Ubuntu on a disk with no bootloader.  Your first boot disk is sda and if there is nothing on it, you will get the error you are getting.  

You must have a bootloader to boot any OS.  You can install Grub post installation if you want to rather than reinstalling.  But if you would rather reinstall, you WILL get prompted to install Grub to boot the system.  When you do, choose MBR, which is the first 512b of the first disk.  Grub will then set the system up to boot properly.

---

### Post by DJH10 on 2008-08-03
But i've never been asked to install 'Grub' at any time during the times i've tried to install Ubuntu :confused:

---

### Post by bobnutfield on 2008-08-03
Grub is th default bootloader used by Ubuntu.  You must look very carefully, but a standard install of Ubuntu will always offer to install Grub. I suspect that you have been missing it.  It is at the end of the process.  Look very carefully for it.

---

### Post by DJH10 on 2008-08-03
> **bobnutfield said:**
> Grub is th default bootloader used by Ubuntu.  You must look very carefully, but a standard install of Ubuntu will always offer to install Grub. I suspect that you have been missing it.  It is at the end of the process.  Look very carefully for it.

Well i'll keep  a close eye on it Bob,one more go before bed!!Thanks for all your help :)

---

### Post by bobnutfield on 2008-08-03
My pleasure to help.  Just remember to install Grub to the MBR of the first boot disk, which in you case is sda (the first disk on your system).  Do not install it to the same partition (the 60GB disk you are installing to) unless you set that disk to be the first boot disk in your BIOS.

---

### Post by DJH10 on 2008-08-03
Right,under the advanced options in 'ready to install' bit it has a box which says 'install boot loader' with a check box next to it and then a list of my hd's underneath.Is this the 'Grub' you mentioned Bob?
And the 60gig hd is the first boot disc aswell

Now im getting this error:
The ext3 file system creation in partition #1 of SCSI4 (0,0,0) (sdc) failed.

---

### Post by bobnutfield on 2008-08-03
Yes, that is it.  Your BIOS has /sda as the first boot disk, so install it to the MBR (Master Boot Record) of that disk.  Grub should take care of booting Ubuntu for you, no matter which disk you have it installed to.

---

### Post by DJH10 on 2008-08-03
No i meant the 60gighd is the 1st boot disc in my bios but its showing the 37gig as my 1st boot disc?This is all very confusing :confused:

---

### Post by bobnutfield on 2008-08-03
Whatever your BIOS shows at the first boot disk (doesn't matter which one that is), this is the disk that the BIOS is going to look for a bootloader on.  If you know which one that is, that is the one you will choose to install GRUB to.  Go into your BIOS before you install and just verify you are comfortable that you know which disk is going to booted first.

So, again, install Ubuntu to whereever you want to, but install Grub to the FIRST boot disk (MBR) as it is shown in your BIOS.

---

### Post by DJH10 on 2008-08-03
This is doing my head in :(
I've taken a screenshot which shows the grub installed on the 60gig HD along with Ubuntu but it still won't boot,i keep getting boot from cd?

It is also installed on the 37gig HD for some reason :confused:

---

### Post by Ed J on 2008-08-03
> **bobnutfield said:**
> Grub is th default bootloader used by Ubuntu.  You must look very carefully, but a standard install of Ubuntu will always offer to install Grub. I suspect that you have been missing it.  It is at the end of the process.  Look very carefully for it.

I've recently installed Hardy 8.04 on a number of PCs but I don't remember any prompts for grub location either.

---

### Post by DJH10 on 2008-08-04
Right don't know if this is progress but i've swapped the IDE cables around.Originally i had the HD cable in IDE slot 2,CD/DVD drives in IDE 1 on the mobo due to short cables etc.Did some jiggling about and now it starts to boot but i get an error 21 with message saying" selected disk does not exist"?
It then gives me 3 Ubuntu OS's to choose from,generic,memtest etc but whichever i choose it gives the above message.

---

### Post by unutbu on 2008-08-04
Right. I think you have made a lot of progress, though it may not look like it (yet) to you.

Please boot from the LiveCD, open a terminal, and 
post the output from

```
sudo fdisk -l
```

again. Since you swapped drives, the information will have changed a bit, and its helpful to know what things are called so we can give you the right commands.

---

### Post by DJH10 on 2008-08-04
OK thanks for the reply,i'm at work at present so will do what you say when i get home.
Once again many thanks for all the help 8)

---

### Post by DJH10 on 2008-08-04
Fixed it,hussar!!!

I unplugged both the SATA hd's and installed Ubuntu on the remaining IDE drive,worked like a charm :)

Then i plugged the SATA hd's back in after the install and just had to mount them.

We are now running Ubuntu,hussar!!

Now comes the hard part,learning a new system!!

---

