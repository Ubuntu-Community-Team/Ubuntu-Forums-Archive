---
title: "Grub cant see my old windows 7 partition"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by dako541 on 2013-02-01
okay, i am an idiot.  Let me get that out now.  Seems my install of ubuntu made my boot load  of windows impossible...

i had a 2 partition c:  /  d:  windows pc.  these is a funny tiny recovery partition too.  C was system, D was data, but i installed win7 full os on it, so my old boot loader let me select it to boot.  C: and D: are actually the same 650GB hd, partitioned by windows.

and then i formatted ubuntu on C, and assigned grub on the harddrive device.  Ubuntu works fine, but grub doesnt see D:, thus i cant boot windows D:.  I can mount D: from ubuntu (now on C ) .  Grub can see the windows recovery partition, but that just loads a blank screen and restarts.

how do i get grub to see D: windows?  and or is there a way from within C: ubuntu to restart on D: (which has win7 os and it can mount).

Thanks, much love

---

### Post by lindsay7 on 2013-02-01
Try Boot-Repair,  here is the site and information.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by dako541 on 2013-02-02
> **lindsay7 said:**
> Try Boot-Repair,  here is the site and information.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

went there, installed it, ran it.  It complained that i had a /dev/sda3 far from the beginning of the drive and bois might not see it(!).  It sent me to gParted, telling me to make a /boot partition, then (i think) run Boot Repair again to link /boot to my wayward sda3.  

gParted 'help' for 'boot' actually told me to run grub from command line and search for /boot/grub/stage1 or /grub/stage1.  i have neither.

Is this creating of a /boot what i really want to do?  seems i might break something else.  I dont see how to do it from gParted if i'm supposed to.  please advise.

---

### Post by Bashing-om on 2013-02-02
dako541; Hi !

Try this simpler approach:
Boot into ubuntu; ctl+alt+t for a terminal: input terminal code:
```
sudo update-grub
``` I expect that windows' bootloader will be picked up and chainloaded to ubuntu's grub menu. This method only works if;
a) The disk that ubuntu is installed on is set as the 1st boot priority in bios,
b) grub is installed onto the MBR of the disk that ubuntu is installed onto.[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by oldfred on 2013-02-02
If none of the above suggestions have worked, run the BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

    
Why do you think you had Windows in d:? Windows is always c: and d: is another partition usually data. Only if you had two installs might d: have Windows but Windows always installs all boot files into the boot partition (usually c:). So even if you have an install in d: its boot files were in c:. If otherwise a full install you may be able to repair with a Windows repairCD.

---

### Post by dako541 on 2013-02-03
okay the link is... [http://paste.debian.net/231490/](http://paste.debian.net/231490/)
seems to be a cluster error on D (dev/sda3 ntfs) now, sigh. (gParted reports)
Is there a ubuntu tool to fix ntfs cluster errors on other partitions?!
is that why grub wont list it?  fix it and it will let me boot???
(win7 wont let me reformat on C sda2 cuz it is not ntfs, it is not ubuntu ext4)

im thinking of mounting D, moving all the data i can to ubuntu (sda4), and having my 
win7 oem boot disc reformat D (it will cuz it is ntfs).  That would suck, cuz windows 
needs a lot of drivers reinstalled.

(i'm also flirting with the idea of using gParted to format C (sda2 currently ext4 for ubuntu) back to ntfs, then using win7 boot to format it back to win.  Not sure if win7 will let me format C, though.  It would also wipe grub, would have to redo that and hope it finds both C win7 and sda4 ubuntu)

---

### Post by dako541 on 2013-02-03
> **oldfred said:**
> 
Why do you think you had Windows in d:? Windows is always c: and d: is another partition usually data. Only if you had two installs might d: have Windows but Windows always installs all boot files into the boot partition (usually c:). So even if you have an install in d: its boot files were in c:. If otherwise a full install you may be able to repair with a Windows repairCD.
oh, i'm an idiot.  Ubuntu format asked for a 'swap' partition, so i said C (!).  It trashed what was my win7 boot system partition, so i installed a second ubuntu on C (sda2).  Historically, my D (sda3) was also a win7 boot for emergencies.

---

### Post by Bashing-om on 2013-02-03
dako541; I feel for you.

Frustration and a state of aggravation often lead to errors. Been there too, not think'n to clear.

All hope may not be lost, many have had success in recovering files with "test disk".
On that note I have also had good results in recovering a "bad" disk using the "dd" command to zero out the drive (using one on this system going on two years now). 

Formatting: recommendations are to use window's tools for windows, and linux tools for ubuntu situations. In my opinion, GParted formatting a usb drive or "data" partition is fine, but windows can be real picky; suggest you use windows to set up for (re)installing windows.
As an aside - What would you loose if you left windows behind ?

[INDENT]not much help now, but still here
 
[/INDENT]

---

### Post by dako541 on 2013-02-03
> **Bashing-om said:**
> dako541; I feel for you.

Frustration and a state of aggravation often lead to errors. Been there too, not think'n to clear.

All hope may not be lost, many have had success in recovering files with "test disk".
On that note I have also had good results in recovering a "bad" disk using the "dd" command to zero out the drive (using one on this system going on two years now). 

Formatting: recommendations are to use window's tools for windows, and linux tools for ubuntu situations. In my opinion, GParted formatting a usb drive or "data" partition is fine, but windows can be real picky; suggest you use windows to set up for (re)installing windows.
As an aside - What would you loose if you left windows behind ?

[INDENT]not much help now, but still here
 
[/INDENT]
thanks...

uh, i'm a newbie.. what is 'test disk'?  i tried from commandline, and it didnt do anything.  I need to test an alt parttion.  What also is dd?  wasnt sure i wanted to try that without knowing...

well, i cant install windows to use their tools cuz i need a ntfs partion to install windows onto.  so i need gParted to format the C partion back to ntfs.  however, i have a gut feeling that is a bad idea.

as for what will i lose without windows?  Well, i'm new, so i'm slowly replacing... so far, i'll miss all the fancy dlls in paint.net (i do a lot of alpha blending of .png) (open to alt suggestions).  I liked Real Player in windows to rip movies (uh, backup streaming movies ive paid for), and i see it for ubuntu but it looks scary to install.  maybe there is a better alt in ubuntu.  looks like firefox does it normally if you expand your cache...

---

### Post by LostFarmer on 2013-02-03
Have you made any partition changes after you posted the 'bootinf' at post #6 ?
If not, it looks like you are using the  grub.cfg on sda5 , and it lists: 
**Windows Recovery Environment (loader) (on /dev/sda3),** 
that should be the win OS not recovery, have you tried it ?


sda5/ect/fstab-- shows that there was a swap but fdisk does 
not show one, that will cause a problem with linux on sda5.


I suspect  "Bashing-om" is talking about 'testdisk' not 'test disk' 
but not sure.

---

### Post by Bashing-om on 2013-02-03
dako541;

"Test disk" is an application one has to burn to disk from the net. Google "test disk" for info or search this forum for users testimony.

Before getting real hot and bothered, I suggest you give test disk (or similar ones) a try.

Once you have recovered your files and want to (re)write that disk if "disk utility" reports bad sectors, we can proceed with the powerfully - destructive command "dd".


And yeah I recon ya need to get further acclimated to ubuntu before you make the switch permanently. - I ditched windows about 8 years ago, I have never looked back, but I do not require the use of the high end applications made for windows either .

Do your home work on "test disk" and get back with us soon as you are ready.
[INDENT][INDENT]my 2 pounds worth
 
[/INDENT][/INDENT]

---

### Post by oldfred on 2013-02-03
Your sda3 is labeled data, but looks like it has a full set of boot files. Does it also have a full install? Or is it just have boot files for the other install?

Boot flag should be on sda3 as only Windows uses boot flag. Then you may be able to run chkdsk on sda3 to make repairs.

---

### Post by Bashing-om on 2013-02-04
dako541;

Your attention is (re)invited to the above post, In the event you must resort to data recovery:
Cheesemill's most excellent advise:
[http://ubuntuforums.org/showthread.php?t=2112112](http://ubuntuforums.org/showthread.php?t=2112112) post #7

And Mark Phelps most excellent advise:
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
[INDENT][INDENT]hang'n in there 

[/INDENT][/INDENT]

---

### Post by dako541 on 2013-02-04
> **LostFarmer said:**
> Have you made any partition changes after you posted the 'bootinf' at post #6 ?
If not, it looks like you are using the  grub.cfg on sda5 , and it lists: 
**Windows Recovery Environment (loader) (on /dev/sda3),** 
that should be the win OS not recovery, have you tried it ?

sda5/ect/fstab-- shows that there was a swap but fdisk does 
not show one, that will cause a problem with linux on sda5.

not changed anything yet.

yeah, i can run that Win Recovery, but with the oem win7 disc, it just aborts when it sees a problem.

how do i fix the mentioned fstab problem?

---

### Post by dako541 on 2013-02-05
> **LostFarmer said:**
> Have you made any partition changes after you posted the 'bootinf' at post #6 ?
If not, it looks like you are using the  grub.cfg on sda5 , and it lists: 
**Windows Recovery Environment (loader) (on /dev/sda3),** 
that should be the win OS not recovery, have you tried it ?


sda5/ect/fstab-- shows that there was a swap but fdisk does 
not show one, that will cause a problem with linux on sda5.


no changes made yet.

how do i fix noted fstab issue?

---

### Post by LostFarmer on 2013-02-05
to edit file if you are booted into sda5: from a terminal
```
gksu gedit /etc/fstab
``` and put a # in front of the line " **#** UUID=94f0c0a0-df56-4738-b5f6-59c6a7d9c008 none            swap    sw              0       0"  then select save.

Are you going to keep both linux installs ?

---

### Post by dako541 on 2013-02-05
> **oldfred said:**
> Your sda3 is labeled data, but looks like it has a full set of boot files. Does it also have a full install? Or is it just have boot files for the other install?

Boot flag should be on sda3 as only Windows uses boot flag. Then you may be able to run chkdsk on sda3 to make repairs.

sda3 is a full install of win7

i cant run chkdsk cuz i cant boot any win7 except oem win7 boot / install disk, which is very limited.

maybe i have to download a win7 boot disk with chkdsk.  Anyone know a link?  Ah, but that wont work cuz i must download from ubuntu, so the formatting of a win7 disk is unlikely from ubuntu.

---

### Post by dako541 on 2013-02-05
> **Bashing-om said:**
> dako541;

"Test disk" is an application one has to burn to disk from the net. Google "test disk" for info or search this forum for users testimony.

Before getting real hot and bothered, I suggest you give test disk (or similar ones) a try.

Once you have recovered your files and want to (re)write that disk if "disk utility" reports bad sectors, we can proceed with the powerfully - destructive command "dd".


And yeah I recon ya need to get further acclimated to ubuntu before you make the switch permanently. - I ditched windows about 8 years ago, I have never looked back, but I do not require the use of the high end applications made for windows either .

Do your home work on "test disk" and get back with us soon as you are ready.
[INDENT][INDENT]my 2 pounds worth
 
[/INDENT][/INDENT]
okay, getting up to speed on this...
installed testdisk
command line sudo testdisk, picked drive (with all my partitions)
led me to a menu...
 [Intel  ] Intel/PC partition
 [EFI GPT] EFI GPT partition map (Mac i386, some x86_64...)
>[Humax  ] Humax partition table
 [Mac    ] Apple partition map
 [None   ] Non partitioned media
 [Sun    ] Sun Solaris partition
 [XBox   ] XBox partition
 [Return ] Return to disk selection

and i ran away in fear ;)

i read your two links... some debate if i can fix my sda ntfs, which is what i want to do.  Not ready for Philips download of MS trial boot repair.  Keep in mind i can mount my D: sda3 and pull any data i want from ubuntu.  

what do i want to do in above menu to get to my sda3 ntfs?

---

### Post by dako541 on 2013-02-05
> **LostFarmer said:**
> to edit file if you are booted into sda5: from a terminal
```
gksu gedit /etc/fstab
``` and put a # in front of the line " **#** UUID=94f0c0a0-df56-4738-b5f6-59c6a7d9c008 none            swap    sw              0       0"  then select save.

Are you going to keep both linux installs ?

yes, for now.  though as said, i'm flirting with idea of using gparted to format c: sda2 back to ntfs so my win7 eom boot / format disk will allow me to format C: sda2 back to win7 (giving me chkdsk).  Of course, the win7 install will screw up my grub, and it will go back to whatever bios win7 uses, possibly hiding my current sda4/5 ubuntu workspace.  any advice here?

as for the fstab change... i'm gonna wait on this till my other issues are resolved.  I am currently using sda4 or sda5 as ubuntu workspace (i dont know which :)  it looks like sda5 from used space).  I dont understand, however, why gparted makes sda5 look like it is inside of sda4.

---

### Post by oldfred on 2013-02-05
Your sda5 is inside sda4.

With MBR(msdos) partitioning you can only have 4 primary partitions. They created that with the first hard disk for a PC back in the 1980's and soon realized more partitions may be needed. So one primary can become the extended partition which is just a container for many logical partitions.
All primary partitions are numbered sda1 thru sda4. Any one can be the extended, but only one. And all logical partitions start at sda5 and go up from that.
       MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

            MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by LostFarmer on 2013-02-05
If you can mount the Win partition , you can just copy what you want with linux.  You can test for some errors on the partition with:

"testdisk"-- select 'Intel/PC partition' --next menu select- 'Advance'-- hi-ligh the win partition and at bottom select 'boot'.  Does it say "Boot Sector" OK ?

at bottom just select 'quit' till you are out of testdisk.

testdisk does not write anything to the hdd till it asks and you say yes.

 If win 7 boot files was put onto a different partition that you later deleted, that will be a major problem as far as I know. (have XP and a new laptop with win8)  If you have a fast Internet , you can down load win7 ISO and burn it ti a dvd with linux.  If you have a DVD read/write drive.

[http://www.sevenforums.com/tutorials/3413-repair-install.html](http://www.sevenforums.com/tutorials/3413-repair-install.html)
[https://windowssecrets.com/top-story/win7s-no-reformat-nondestructive-reinstall/](https://windowssecrets.com/top-story/win7s-no-reformat-nondestructive-reinstall/)
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)

You might just need a 'boot repair' in link 3.
you may need the WIN Key, read  links and understand them first.

 > Of course, the win7 install will screw up my grub, and it will go back  to whatever bios win7 uses, possibly hiding my current sda4/5 ubuntu  workspace.  any advice here? Yes it will over write grub , but I am not the best to advice.

---

### Post by oldfred on 2013-02-06
Since you have or know how to add Boot-Repair to a liveCD/DVD or flash drive then that is the easiest way to reinstall boot loaders.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

---

