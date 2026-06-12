---
title: "[SOLVED] newbie qs"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by gvpj on 2008-05-31
problem summary - the install guides i read before installing was different from my experience... i go to grub prompt instead of login. after rebooting. please help. 

here are the details...
my pc - pentium 3, 512mb ram, 200 gb hdd.
i formatted the drive. ran the live cd. all was well and worked fine. then clicked install. did everything as illustrated in the installation guide posted on the ubuntu website. after installing it asked to remove cd and reboot. upon reboot, here is where it went different. the guide mentioned that it would come to a login screen, but in my case it went to a blank/black screen with "grub>". what do i do now? 

if i have missed out any info, please let me know as i am trying this for the 1st time.

---

### Post by tactx on 2008-05-31
The Grub screen is the boot loader that allows you to select an operating system if more than one is installed....if its comming ub blank and just sitting there...Id say you have a bad install. I had something similar happen to me when i burned a bad cd. the writer software reported a successful write but it wouldn't work. Turned out my burn setting were set for the wrong media... anyway...test your install cd by booting to it and run the disk integrity check....if it comletes..the cd is good. If not you may need to reburn it. Also...it would be smart to check the md5 hash to make sure it matches the one published here..[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by drs305 on 2008-05-31
> **tactx said:**
> Also...it would be smart to check the md5 hash to make sure it matches the one published here..[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

In linux, you check the md5 hash by running:
```
md5sum filename
```

Since this is your first attempt, you are probably using windows. To check the md5 hash of the downloaded .iso file, in windows explorer drag the .iso filename over md5sum.exe and it will display the number. You can download md5sum.exe from the link below.  Another way is to use digestIT. Both are explained on the OpenOffice site: [http://www.openoffice.org/dev_docs/using_md5sums.html](http://www.openoffice.org/dev_docs/using_md5sums.html)

As tactx suggested, it was probably a bad install. Verify the .iso is correct and try to install it again.

Welcome to ubuntu!

---

### Post by alzwded on 2008-05-31
Hm... if you say the livecd worked... then, try this:

Run the livecd again, go to your partition where you installed ubuntu (should be on your desktop, if not go to places / computer / hdax) go to the boot/grub folder and check your menu.lst file. If it's empty try adding this

```

timeout 10
default 0
title ubuntu
root (hd0,0)
kernel /boot/vmlinuz root=/dev/hda1 ro silent splash
initrd /boot/initrd.img
```

replace vmlinuz and initrd.img with vmlinuz-yourversion and initrd.img-yourversion respectively (the files are in the /boot folder)
if you're unsure post how/where you installed

---

### Post by gvpj on 2008-05-31
wow!! so many solutions so fast. thanks everyone. i am not at my ubuntu pc now. i cant wait to try all this, i will post my results as soon as i get home. 

please note that i dont have xp on that pc anymore. i wiped the drive clean before trying to install ubuntu. i had a recurring problem with xp "ntldr is missing" that brought my pc to a grinding halt every couple of weeks. tried every solution on the net but none worked. finally decided to try linux. ubuntu is my 1st stop.

---

### Post by ugm6hr on 2008-05-31
As suggested, the most likely culprit is a bad CD.

When you boot the LiveCD, select the "Check CD for errors" option.  It will take a while (even 20-30 mins).

Other possibility is a bad HD.

And start reading here.... [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by drs305 on 2008-05-31
Rather than edit this post, I will just link to the post I used to present the option of restoring grub from the LiveCD. I used [catlett's guide, post #26]("http://ubuntuforums.org/showthread.php?t=224351#26"). Note that this technique installs grub to the MBR and cause issues with dual booting. He has an explanation in the middle of post #1.

---

### Post by gvpj on 2008-05-31
dear all, i want to try each of your solutions now. here goes. i will post as i try each...

> **tactx said:**
> The Grub screen is the boot loader that allows you to select an operating system if more than one is installed....if its comming ub blank and just sitting there...Id say you have a bad install. I had something similar happen to me when i burned a bad cd. the writer software reported a successful write but it wouldn't work. Turned out my burn setting were set for the wrong media... anyway...test your install cd by booting to it and run the disk integrity check....if it comletes..the cd is good. If not you may need to reburn it. Also...it would be smart to check the md5 hash to make sure it matches the one published here..[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

tactx, 
i only have one os on the drive and that is ubuntu which i am trying to get to work. i formatted the drive clean before starting the install.
i rebooted with the livecd. that goes to the options screen to try out ubuntu etc. 
selected the option "check cd for defect". 
it completed the check so the disc is ok. 
btw my ubuntu livecd is burnt onto a dvd not a cd... that shouldnt be a problem right? please forgive me if that is a stupid question.
i also tested the md5 before burning the iso file onto the blank dvd. the file was ubuntu-8.04-desktop-i386.iso and the comparison result using winmd5sum software was ok. the m5d hash was 8895167a794c5d8dedcc312fc62f1f1f

---

### Post by gvpj on 2008-05-31
> **drs305 said:**
> In linux, you check the md5 hash by running:
```
md5sum filename
```

Since this is your first attempt, you are probably using windows. To check the md5 hash of the downloaded .iso file, in windows explorer drag the .iso filename over md5sum.exe and it will display the number. You can download md5sum.exe from the link below.  Another way is to use digestIT. Both are explained on the OpenOffice site: [http://www.openoffice.org/dev_docs/using_md5sums.html](http://www.openoffice.org/dev_docs/using_md5sums.html)

As tactx suggested, it was probably a bad install. Verify the .iso is correct and try to install it again.

Welcome to ubuntu!

drs305, 
i reinstalled, now i think i have done something worse. the message says... 
grub loading stage 2
(hd2,4)/boot/message: file not found.
then it goes into a blue screen for a few seconds and reboots. its an endless loop like that now

---

### Post by gvpj on 2008-05-31
> **alzwded said:**
> Hm... if you say the livecd worked... then, try this:

Run the livecd again, go to your partition where you installed ubuntu (should be on your desktop, if not go to places / computer / hdax) go to the boot/grub folder and check your menu.lst file. If it's empty try adding this

```

timeout 10
default 0
title ubuntu
root (hd0,0)
kernel /boot/vmlinuz root=/dev/hda1 ro silent splash
initrd /boot/initrd.img
```

replace vmlinuz and initrd.img with vmlinuz-yourversion and initrd.img-yourversion respectively (the files are in the /boot folder)
if you're unsure post how/where you installed


alzwded,
ran livecd version
on my desktop is only "examples" and "install"


i cannot see places / computer / hdax

i can see places / computer
from there i see the following...
3.7gb media
5.4gb media
10.5gb media 
176.3gb media
cdrw/dvdrw drive
floppy drive
filesystem

i dont recall making so many partitions. 
how do i find places / computer / hdax?

---

### Post by drs305 on 2008-05-31
> **gvpj said:**
> drs305, 
i reinstalled, now i think i have done something worse. the message says... 
grub loading stage 2
(hd2,4)/boot/message: file not found.
then it goes into a blue screen for a few seconds and reboots. its an endless loop like that now

Did you get that (hd2,4) from the commands I had you run? 
Do you know how many partitions you had on the disk you installed ubuntu on?
Have you run the instructions in post #7 ?
You might be getting the 'file not found' message because the system is looking at (hd2,4). That doesn't sound right. Does your computer have two hard drives or external drives that were hooked up during installation?

---

### Post by gvpj on 2008-05-31
> **drs305 said:**
> Note: I was in the compose window for quite a while and hadn't seen ugm6hr's entry. But if you want to give this a try anyway, it should only take a couple of minutes...

If you have the LiveCD and you want to try restoring grub without reinstalling the entire system, here is one of the easiest things to try. (You may even be able to do it from the grub prompt you are getting without the CD):

1. Run LiveCD and wait for it to finish loading. 
2. Open a terminal and type:
```
sudo grub
```
3. You should get the grub> prompt. The commands for the rest of the procedure will be typed at the grub prompt ( grub> )
```
find /boot/grub/stage1
```
Write down the results. It will probably look like (hd0,0), (hda0), (hda0,2) etc. Replace the **X**'s with the results.
4. ```
root (**X,X**)
``` 
Example: root (hda0,0)
5. ```
setup (**X,X**)
```
Example: setup (hda0,0). You will see it checking and may see some 'failed - not fatal' comments. 
6. When the >grub prompt returns:
```
quit
```
7. Reboot and see if it now works.

Good luck!

drs305,
my results for your step 3 was...
(hd0,0)
(hd0,4)
(hd0,6)

i didnt see any hda results as you described.
so what should i type in step 4? should i type root (0,0)?

---

### Post by gvpj on 2008-05-31
> **drs305 said:**
> Did you get that (hd2,4) from the commands I had you run? 
Do you know how many partitions you had on the disk you installed ubuntu on?
Have you run the instructions in post #7 ?
You might be getting the 'file not found' message because the system is looking at (hd2,4). That doesn't sound right. Does your computer have two hard drives or external drives that were hooked up during installation?

i have only one hdd. i just posted results for #7.

---

### Post by drs305 on 2008-05-31
> **gvpj said:**
> drs305,
my results for your step 3 was...
(hd0,0)
(hd0,4)
(hd0,6)

i didnt see any hda results as you described.
so what should i type in step 4? should i type root (0,0)?

Yes, if you did a normal, full install using your entire disk for the setup. Do you recall the partitions you made for ubuntu? 

In any case, it is most likely (hd0,0), so enter that in step 4. (and 5)  Sorry, the hda was a typo in the earlier post.

---

### Post by gvpj on 2008-05-31
> **drs305 said:**
> Yes, if you did a normal, full install using your entire disk for the setup. Do you recall the partitions you made for ubuntu? 

In any case, it is most likely (hd0,0), so enter that in step 4. (and 5)  Sorry, the hda was a typo in the earlier post.

i typed...
root (hd0,0)
setup (hd0,0)

then a whole string of lines came up. the last lines said... succeeded Done.

quit

restart. (removed cd)

its gone to that endless loop again with the (hd2,4) missing file message etc


should i format the drive and start again?

---

### Post by drs305 on 2008-05-31
> **gvpj said:**
> i typed...
root (hd0,0)
setup (hd0,0)

then a whole string of lines came up. the last lines said... succeeded Done.

quit

restart. (removed cd)

its gone to that endless loop again with the (hd2,4) missing file message etc


should i format the drive and start again?

You could try running it again with the other values but if that is what it takes there might be other issues - like partitions you don't really want, etc. 

I would recommend just reformatting. There is an additional step we could try. You restart the installation, but when you get to the partitioning you stop and tell it to install grub without doing any further installation. It should then reinstall a new grub menu that MAY solve this. We can try that if you want.

Setup should be (hd0)

---

### Post by gvpj on 2008-06-01
> **drs305 said:**
> You could try running it again with the other values but if that is what it takes there might be other issues - like partitions you don't really want, etc. 

I would recommend just reformatting. There is an additional step we could try. You restart the installation, but when you get to the partitioning you stop and tell it to install grub without doing any further installation. It should then reinstall a new grub menu that MAY solve this. We can try that if you want.

ok. do i reformat as fat32 or ntfs? i did a search and some said fat. my hdd was ntfs

---

### Post by cariboo on 2008-06-01
I think you're missing a step during installation. Seeing as your partitions are all screwed up why not reinstall and after it asks you to set your user information and the partitioner starts choose the first choice automatically use the whole hard drive, let it do its thing and continue on. Linux uses its own format by default it is ext3, so formatting the hard drive as either fat32 or ntfs is not going to do any good.

As for your problem with setting up grub properly you have make your changes in a chroot environment. The way to do that is to boot the liveCD, when its finished mount your hard drive and then chroot into your installed environment.

First in a terminal (the terminal can be found in Applications|Accessories) type:

```
sudo mount /dev/hdx /mnt
```

hit enter (note hdx is your hard drive if it an ide drive it should be hda1, if its an sata drive it should be sda1) then in the same terminal type:

```
chroot /mnt
```

after you are in the chroot environment you can make changes to grub. Remember after you have made changes to grub you have to run update-grub or none of your changes will work.

One other thing to keep in mind that for some reason grub subtracts one from what fdisk says eg: hda1 becomes hd0,0.

I just looked at your last message and it looks like grub is trying to boot off a third hard drive if you've got any eternal drives connected maybe disconnect them first before doing anything else.

Good luck

Jim

---

### Post by ugm6hr on 2008-06-01
> I think you're missing a step during installation. Seeing as your partitions are all screwed up why not reinstall and after it asks you to set your user information and the partitioner starts choose the first choice automatically use the whole hard drive, let it do its thing and continue on. Linux uses its own format by default it is ext3, so formatting the hard drive as either fat32 or ntfs is not going to do any good.

You only want Ubuntu? Yes?  Then this is reasonable.

However - beware if you have a recovery partition on the HD - it will be lost.

Some system manufacturers also put a diagnostics partition at the start of the HD too.

If you don't want any of this - just pick the Guided - use full HD option to install.  You should then be able to use the default settings.

---

### Post by gvpj on 2008-06-01
booted live cd

choose install ubuntu

step 1 - welcome & language english; 2 - timezone  +8gmt; 3 - keyboard usa

step 4 - here it differed slightly every time i tried
1st option was "guided - resize scsi1 (0,0,0), partition #7 (sda) and use freed space." 
there was a slider below with "new partition size: ubuntu 8.04 97% 159.3gb"
i have noticed that each time i tried reinstalling ubuntu, this has decreased... the 97% has progressively said a smaller size!
2nd option was "guided - use entire disk" 
"scsi1 (0,0,0) (sda) - 200gb ata st3200822a
3rd option "manual"

**i choose option2 "guided - use entire disk" this time round**

step 5 who are you? 
i filled all info for name, password, computername

??no step 6??

step 7 ready to install.
the main window had a summary of my details plus at the end it said...

the partition tables of the following devices are changed:
scsi1 (0,0,0) (sda)
the following partitions are going to be formatted:
partition #1 of scsi1 (0,0,0) (sda) as ext3
partition #5 of scsi1 (0,0,0) (sda) as swap

in advanced button, was option "install boot loader" was checked
"device for boot loader" was (hd0)
"participate in the usage survey" was unchecked
"http proxy" was blank

 clicked install
installing system took 20-30mins
screen went blank at abt 50% & 80% maybe a screensaver or something. came back on after moving mouse

install completed; restarted

dvd popped out, removed disc, closed tray, hit enter

pc booted up, and did normal checks as it would do always.

then on screen it said...

grub loading stage 1.5.
grub loading, please wait...
error 18

i have waited more than 5 mins and nothing happened. just blinking at the bottom after the line "error 18"
these messages never happened before in my 1st few attempts to install.
what do i do now? which of all your suggestions should i try next?

---

### Post by ugm6hr on 2008-06-01
If you have an old computer with a new (larger) HD, GRUB sometimes misbehaves.

You may need a separate /boot partition.

Or maybe a BIOS update?

---

### Post by drs305 on 2008-06-01
If you are trying to install Hardy and would have IM capability during the install, please send me a PM. I have some time today and we can go through the installation step by step if you'd like. Don't despair!

The Grub Error 18 message,as ugm6hr said, has to do with the size of your boot partition. IF grub is looking in the right place, you will probably have to repartition (and reinstall) your drive so that the boot drive is less than 500MB. If you know how to get into BIOS you may be able to change some settings there or perhaps download a new BIOS to avoid having to repartition.

In the meantime, if you can boot with the LiveCD and post the following so we can see what the new install did:
```
sudo fdisk -l
```

Update: we worked through this via PM and IM - reinstalled and made the first partition a /boot partition less than 500MB in ext2. The rest was formatted normally and was successful.

---

### Post by gvpj on 2008-06-03
everything solved!!!!! i'm in!!

thanks to everyone who helped... drs305 ugm6hr cariboo907 tactx alzwded... yr suggestions n info really helped me understand this new os. but most of all yr patience, with all my most basic questions.

i will post soon the solution that drs305 took me thru step by step (for more than 3hrs!) for others who might have the same issue.

tq. cheers!

---

### Post by gvpj on 2008-08-15
a bit late but as promised... heres the solution. this post is part of a pm sent by drs to me...

The grub error (error 18) you are now getting is logical. You have an older machine (Pentium 3) with a newer, large hard drive. Your computer's BIOS, created a long time ago, demands that the startup information be placed in the first 500MB of the drive. If it is anywhere else (which it may be), grub doesn't see it and reports it can't find it

Assuming you just have the one drive and don't have any usb drives hooked up during boot, the solutions, from easiest to more difficult:

1. Change your system's BIOS settings. Generally you get into BIOS during boot by hitting the DEL key, F1, or some other F# key during boot. There may be a setting in there you could change: Boot order, autodetect, etc.

2. Update your system BIOS. You would have to search for your computer manufacturer's web site to see if and how to do that.

3. Change jumper settings on the hard drive. If it's a sata II drive, changing to SATA 1 may help (but probably not).

4. Repartition and reinstall ubuntu recognizing the limitations. This is your most likely solution. 

Make sure you have copied any data you want to save to CD, flash drive, etc since all the data on this drive will be erased. I am also assuming this is the only drive on your computer and you don't have any other OS (windows) installed on it.

During setup, when you get to partitioning, you will HAVE to make 2 partitions. I would recommend 3 or 4.

1. BOOT. The first, and most important, is the boot partition. Make it 500MB (that's MB, not GB - i.e it's pretty small) or less and make it bootable. So the choices you would make for the first partition are: 500MB or less, "boot" (I think that is the selection) and bootable. I would format it in ext2 although I think ext3 is ok as well.

2. ROOT. The second partition is the root ( / ) partition. I would make that 10-15GB, ext3. If you don't want any other partitions (see below), the size would be the rest of the disk.

Those are the only two you HAVE to make, but most experienced many users prefer to have a separate HOME partition.

3. HOME The home partition can take up the rest of your disk (or 10-15GB, see below). Format it to ext3. The advantage of having a separate home partition is that if you have to reformat your system partition or decide to run two different types of ubuntu, you can keep all of your settings. If you don't have a separate home and have to reinstall, you would have to recreate all your settings from the scratch.

4. DATA. Many users keep one partition for HOME and another for all their data. If you want to do that, make HOME (10-15 GB) and leave the rest to this partition. Format in ext3.

In summary, 
BOOT: /boot , ext2, <500MB, flagged bootable. 
ROOT / , ext3, 15GB. 
HOME: /home , ext3, 15GB. 
DATA: ext3, rest of drive (+- 160GB).

---

### Post by gvpj on 2008-08-15
and this is the chat history during the install....

12:14 AM my pc is ready at step-4 of the install, asking about how to partition
 me: guided or manual
 Drs305:... manual
12:15 AM me: there are 3 lines appeared
  /dev/sda
  /dev/sda1 ext3 198500mb 3800mb
  /dev/sda5 swap 1546mb 0mb
 Drs305: highlight the /dev/sda at the top, then select New partition table, lower left.
 now you get the warning > continue
 me: ok  free space 200049mb
12:19 AM Drs305: double click on 'free space' and it will open create new partition
12:20 AM Drs305: primary, 500, beginning and let's use ext2, mount point /boot.
12:21 AM me: done
 Drs305: okay, highlight free space again and select new partition
12:24 AM Drs305: primary, 15000, beginning (since you have to select one), ext3, / ok
 me: mount point /....correct?
 Drs305: yes that's right
12:26 AM me: free space 184542mb
12:27 AM Drs305: ok good. next highlight free space, new partition, primary, 15000, beginning, ext3 /home
12:28 AM me: btw mine says ext3 journaling file system
12:29 AM free space 169539mb
 Drs305: yes that is correct. now we will do something a little different. you are allowed only 4 primary partitions. instead of using the fourth, we will make a logical partition instead. so select free space new partition logical
 Drs305: you have so far made and should see a /boot, a / , and a home. correct?
 me: yes

12:42 AM Drs305: make the logical partition: free space, new partition, logical, subtract about 2GB from the total for size, beginning, ext3 and for the mount point you can select the name. get to this point and before entering we will discuss it

12:44 AM Drs305: just to clarify, the size you type in should be about 2000 less than the total number
12:46 AM now - the name. this partition will be mounted with the name you select. you can change it at any time, but it would be easier it you put it in now. you can call it anything: data, myfiles, etc just pick a name without spaces or symbols and preferably 8 letters or less
 me: total left is 169539...so i key in 167539?
12:47 AM Drs305: yes, make it 167000 to make it easy. i will recap this partition once you tell me the name.
12:48 AM me: logical 167000 beginning ext3 blank
  no place for name
12:49 AM Drs305: I wasn't clear enough. is there a blank window for mount point
12:50 AM   me: yes
 Drs305: the name you select goes in the mount point window
12:51 AM me: ok...data
  do i need to type in /data or just data
 Drs305: so to recap, you should see logical, 167000, ext3, beginning , data
12:52 AM if that is correct, enter and we will make the final partition, the swap partition. you should see 2000 +- remaining
 me: /data or data
12:53 AM Drs305: good question. put in /data. make sure there isn't a /data in the selection box first
12:54 AM me: done
12:55 AM free 2541mb
  Drs305: for the swap: logical, whatever is left (2000-2500?), END, swap area. there won't be a mount point option (greyed out)
12:56 AM me: there is no choice for logical
12:57 AM the is a mount point
 Drs305: It may have greyed out when you chose swap
 me: ok
12:58 AM 2451 end swap area
  please confirm...no logical
 Drs305: that's good enough. it eliminated the choices because there aren't any more.
1:00 AM yes. we are done with partitioning. continue on to entering the rest of the installation options.  
1:01 AM me: done....i notice in step 4 of 7, "prepare partitions" window, 4th column heading says "format?". all partitions are checked in this column except for last partition
1:09 AM Drs305: yes, the swap won't have the ability to be checked since ubuntu controls that and you don't really have any control over that. Lets just verify your setup
  For mount points, you see:
1:10 AM me: /boot / /home /data blank
 Drs305: That all looks good. so Forward.
1:13 AM me: ok
1:14 AM step 7  advanced options..
 me: install boot loader checked
1:15 AM me: device...(hd0)
  rest blank
 Drs305: yes. You should continue ... if you dare :-)

 me: done...  it worked!!!!!!
2:27 AM me: i am downloading updates… 123 updates!
 Drs305: sounds right!

---

