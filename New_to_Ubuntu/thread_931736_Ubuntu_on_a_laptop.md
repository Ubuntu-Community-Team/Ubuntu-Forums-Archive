---
title: "Ubuntu on a laptop"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by swearr on 2008-09-27
Hello,


I installed Ubuntu on my old laptop a long time ago. Now I'm planning on converting the laptop to a CarPC and I need to install Windows XP.

So about a week ago I tried to install XP, but the installation program that activates as you insert the CD, analyzed the computer setup and concluded that there's no harddrive, or no available space, something like that. As the BIOS shows there is a HDD, Ubuntu is working without any problems and I've had XP installed on this laptop before, I assume Ubuntu is somehow blocking the XP install?

The laptop is a couple year old 15.1" Hewlett-Packard G3000. Not sure what Ubuntu version, but it's less than a year old.

Any suggestions on how to fix this? I need XP installed ASAP and I'd rather not open up the laptop and switch the harddrive.




Cheers :)

---

### Post by shifty_powers on 2008-09-27
get hold of the [gparted livecd](http://gparted.sourceforge.net/livecd.php) format the hard drive as ntfs and then install windows :D

---

### Post by swearr on 2008-09-27
> **shifty_powers said:**
> get hold of the [gparted livecd](http://gparted.sourceforge.net/livecd.php) format the hard drive as ntfs and then install windows :D
I just tried that. First I formated to FAT32 which should also work, but it didn't. Then I removed the partitions altogether so there's only unallocated space, and still it doesn't work.

Now when I start the laptop there's a black screen with the following texts:

> GRUB Loading stage1.5.


GRUB loading, please wait...
Error 22

Shouldn't the linux bootloader be gone after I formated?


Oh, and this is what the Windows installer says ...

> Setup did not find any hard disk drives installed in your computer.

Make sure any hard disk drives are powered on and properly connected to your computer, and that any disk-related hardware configuration is correct. This may involve runing a manufacturer -supplied diagnostic or setup program.

Setup cannot continue. To quit Setup, press F3.

I am currently running a harddisk diagnostic that I found in the BIOS. Estimated time is 57 minutes so I'll have some results then.


Anyone else have some suggestions on how to proceed?

---

### Post by k3lt01 on 2008-09-27
Do you have a floppy drive on the latop? If yes go to bootdisk.com and download the Windows 98 and use that to format your drive.

If not make a bootable USB stick and put the Windows 98 bootdisk files on that.

BTW your first post indicates your confused as to what's happening,he clearer you can be the easier it is to help.

---

### Post by swearr on 2008-09-27
> **k3lt01 said:**
> Do you have a floppy drive on the latop? If yes go to bootdisk.com and download the Windows 98 and use that to format your drive.

If not make a bootable USB stick and put the Windows 98 bootdisk files on that.

BTW your first post indicates your confused as to what's happening,he clearer you can be the easier it is to help.
Thanks I'll try that with the USB stick after the diagnostic has run it's course. I ain't got no floppy, that stuff is ancient.

Of course I'm a bit confused, that's why I'm asking for help, duh ;) I updated my second post, there's some more info on what's going on there.

---

### Post by lswb on 2008-09-27
Are you using a full install windows XP CD? If it is a windows XP upgrade CD it will be looking for a previous version of windows on the hard drive.

---

### Post by swearr on 2008-09-27
> **lswb said:**
> Are you using a full install windows XP CD? If it is a windows XP upgrade CD it will be looking for a previous version of windows on the hard drive.
It's a full install CD, I've used it dozens of times before.

---

### Post by shifty_powers on 2008-09-27
ok, next option is to go nuclear on your hard drive :D

go to [here](http://www.dban.org/) download, burn, boot and use dban's nuke boot disc. this is designed to obliterate any traces of any data ever, and i mean ever, from your hard drive.

then try windows :D (wouldn't even bother using gparted.)

it's actually bugging me becuase i had EXACTLY the same problem about a month back and for the life of me can't remember how i solved it...

edit: oh and it will probably take at least 2 hours, depending on the wipe algorithm you use and the speed of the hd. some combinations can take the best part of a day :D

---

### Post by swearr on 2008-09-27
A quick run-up of the current situation:

- Laptop harddisk formated, partitions removed, with gparted Live CD. Previous install was Ubuntu.
- GRUB bootloader from Ubuntu still on harddisk.
- Windows installation CD will not recognize the harddisk, perhaps because of GRUB? Or maybe the CD is f'ed.
- Tried Repair on the Windows CD and it said the same thing.
- Ran the 'Primary Hard Disk Self Test' diagnostic on the laptop BIOS, passed all tests. Harddisk is working.


Possible solutions:

#1 Change bootloader to a Windows friendly one. But HOW? No floppy available.
#2 Try another Windows XP installation CD.
#3 Switch harddisk, I have a spare unused 80GB laptop HDD.


Any other suggestions on solutions? Any tips on the mentioned solutions, particularly #1 (how do I make a USB flash drive bootable??) ?

---

### Post by swearr on 2008-09-27
> **shifty_powers said:**
> ok, next option is to go nuclear on your hard drive :D

go to [here](http://www.dban.org/) download, burn, boot and use dban's nuke boot disc. this is designed to obliterate any traces of any data ever, and i mean ever, from your hard drive.

then try windows :D (wouldn't even bother using gparted.)

it's actually bugging me becuase i had EXACTLY the same problem about a month back and for the life of me can't remember how i solved it...

edit: oh and it will probably take at least 2 hours, depending on the wipe algorithm you use and the speed of the hd. some combinations can take the best part of a day :D
Ok I will try that. Luckly it's night over here so I'll put it on now and when I wake up I'll see what has happened ^_^

---

### Post by alecjw on 2008-09-27
I expect the windows cd aint got any drivers for your hard drive...

---

### Post by swearr on 2008-09-27
> **alecjw said:**
> I expect the windows cd aint got any drivers for your hard drive...
Could be a possibility. 

Although when I bought the laptop, Windows XP was installed. And now I'm trying to install Windows XP with Service Pack 2. 
It doesn't really make much sense to me that the previous XP supported the harddisk, then after that Ubuntu supported it (but not my Wireless LAN hardware), and now XP Service Pack 2 doesn't support a 2-3 year old generic Fujitsu IDE ATA harddisk.

---

### Post by shifty_powers on 2008-09-27
no sorry, but that was a bit of a red herring. the hard drive access will be completely transparent to windows, no drivers will be involved. it is plugged directly into the motherboard and there will be no issues with drivers as it will be handled by the chipset, by the southbridge iirc, (heh probably find out it is the northbridge but nevermind :D)

the only thing that may be worth trying is popping into the bios and doing the ole restore defaults...

---

### Post by misswham on 2008-09-27
use the dban.  i used it all the time.  it wipes the harddrive totally clean.  it is free just put it in the search engine then download it and burn it as an iso.  then it will normally take about 4 hrs to wipe my harddrive clean.  it takes longer if the harddrive is big.  i usually run it overnight.  once it completes then you can insert the windows cd and it will recognize the harddrive as new.

---

### Post by misswham on 2008-09-27
also as far as drivers go to your manufactures website and download the drivers.  i have my drivers saved on my external harddrive.

---

### Post by swearr on 2008-09-28
I used Darik's Boot and Nuke overnight to wipe my harddisk, took about 4 hours according to the log, now the GRUB bootloader is gone and the whole disk is completely clean. I also reset the BIOS values to default as shifty_powers suggested. 

However, I still get that same message from the XP installer, "*Setup did not find any hard disk drives installed in your computer*". I even tried another Windows XP CD, this time with the "brand new" Service Pack 3, but it gave me the same answer.

This sh1t is f'ed. Probably gonna try the harddisk swap next, unless anyone has some further suggestions? Also concidering contacting Hewlett-Packard to see if their OEM Windows XP had any drivers that normal Windows XP installs don't have, like to detect the harddisk.

Anyway, thanks for all your help so far, I appreciate it! :)

---

### Post by Sef on 2008-09-28
> This sh1t is f'ed. Probably gonna try the harddisk swap next, unless anyone has some further suggestions? Also concidering contacting Hewlett-Packard to see if their OEM Windows XP had any drivers that normal Windows XP installs don't have, like to detect the harddisk.


Likely something got wiped out that is needed for the install.

---

### Post by swearr on 2008-09-28
VICTORY!!!! I tried a pirated version of Windows XP Professional "Ultimate Edition" and it detected the harddisk. Installing XP as I'm writing this! Glory times, glory times. Wooohooo!!! Up yours legal Windows.

Now I just hope it'll work, because I've had problems with this version in the past :P

---

### Post by zipperback on 2008-09-28
> **swearr said:**
> I installed Ubuntu on my old laptop a long time ago. Now I'm planning on converting the laptop to a CarPC and I need to install Windows XP.

Why do you need Windows to do what you want to accomplish? Perhaps you could explain in detail what you want to do?



> **swearr said:**
>  I assume Ubuntu is somehow blocking the XP install?

Ubuntu shouldn't prevent you from installing XP. 

> **swearr said:**
> 
Any suggestions on how to fix this? I need XP installed ASAP and I'd rather not open up the laptop and switch the harddrive.


Ubuntu won't prevent you from installing Windows. Perhaps it's a partitioning issue.

Could you please tell us a little about how you've got the hard drive partitioned.





Cheers :)[/QUOTE]

---

### Post by zipperback on 2008-09-28
> **swearr said:**
> VICTORY!!!! I tried a pirated version of Windows XP Professional "Ultimate Edition" and it detected the harddisk. Installing XP as I'm writing this! Glory times, glory times. Wooohooo!!! Up yours legal Windows.

Now I just hope it'll work, because I've had problems with this version in the past :P

Software piracy is illegal and as such, it shouldn't be encouraged on this website.

- zipperback
:popcorn:

---

### Post by LaRoza on 2008-09-28
Closed. Keep it legal on this forum.

---

