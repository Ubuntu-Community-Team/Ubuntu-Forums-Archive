---
title: "Dual booting Ubuntu-can I retrieve data saved with Windows 10?"
date: 2016-10-12
forum: New to Ubuntu
---

### Post by Ben_Cook on 2016-10-12
If I put Ubuntu on my Windows 10 machine, will I be able to get my files saved in Windows 10?  Here's what happened - I purchased a computer for my wife last year from EasyHome.  And I mean I purchased it outright, I DID NOT lease it; I have the receipt.  After the last Windows 10 update, it warned us about being locked out (TriLock defender, a program they use to lock out unpaying customers).  Basically, this program doesn't play nice with the latest update.  Now it is completely locked.  However, we can still get into the BIOS and I should be able to dual boot Ubuntu.  We need our files, as I run my own business, and all our stuff is on that computer, along with personal pictures.

        Now, I can take it back to EasyHome and he said he'd fix it.  I worked for EasyHome for two years a while back, and while I trust this guy, the company is completely untrustworthy when it comes to saving people's personal data.  If I can get Ubuntu onto the computer, will I be able to access these files?  I just need to get them saved first and foremost, then worry about fixing the computer (I've tried convincing my wife to just go with Ubuntu, but it is a no-go[-([-(:D:D).  As always, any help or suggestions are appreciated!

EDIT: when I say he'd fix it, it involves installing Windows 8, uninstalling the program, then upgrading once again to windows 10

---

### Post by yancek on 2016-10-12
I don't know what "EasyHome" is and am not familiar with bit locker, some windows program?

So your question, can you access windows files/folders from Ubuntu would be a yes.  If the data is encrypted or you can't overcome bitlocker, that's a different question.  On Ubuntu you need to have ntfs-3g software installed which is simple to do and you can then access and read/write to an ntfs partition 

I'm not really clear about what you want.  Are you wanting to install Ubuntu on this computer to access and save your windows data?  You should be able to do that with an Ubuntu Live DVD or flash drive.  Fixing it by re-installing windows 8 and updating to 10 will overwrite all your data so you need to get it off before that is done.  Reading your post over, I see that's your intention.

---

### Post by Ben_Cook on 2016-10-12
Thank you that answered my question.  On a side note, easyhome is primarily a lease-to-own company.  Basically people pay (usually WAY too much) weekly for something (in this case, a laptop) to eventually own that item.  If they don't make their payment on something electronic, it locks them out of their device using a hidden program (TriLock defender).  Anyway, thank you so much for your help!

---

### Post by oldfred on 2016-10-12
Another issue with Windows 8 or later is its use of fast start up which really is always on hibernation.
The Linux NTFS driver will not normally mount NTFS partitions which are hibernated to prevent damage.

You may be able to manually mount in read only mode. But as mentioned if encrypted then there will be no way to get to the info. Only your backups of your own data then would be a way to recover data.

       Force mount, read only (ro) where sda3 is example as c: drive, change to your main partition for Windows:
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o ro /dev/sda3 /media/windows

---

### Post by Impavidus on 2016-10-12
Installing Ubuntu to dual boot won't be easy. You first have to shrink your Windows partition, wich works best if you boot Windows. But if you boot a live disk, you should be able to mount the Windows partition (at least read-only) and copy everything to a backup disk.

---

### Post by Ben_Cook on 2016-10-12
Thank you for the replies.  What about just running Ubuntu from a flash drive? Maybe I could use a second flash drive, or SD card, to put data on...if I could access the files?  I don't know, I'm not too experienced with this.  I've installed Ubuntu before, but only on older machines, and I have very very little experience with partitions.

EDIT-maybe that's what live disk means impavidus?

---

### Post by Impavidus on 2016-10-13
Yes, a live disk is a usb drive (or a dvd, but we prefer usb nowadays) with a bootable Linux system. It's usually the same thing you use to install Linux. Create a live disk, insert it into your computer and boot. You should be able to access your files. Then use a second usb drive to store the backups.

---

### Post by mastablasta on 2016-10-13
live disk loads whole system into RAM, so everything is lost on reboot. Except what you do on hard disk (saving, copying etc.). there is a persistence option which iwll retain some installs such as drivers and such. i wouldnt' recoment it for every day constant use, but in cases like yours they do come in handy. please note the oldfred's comment regarding hybernation.

your issuse seems interesting. while the company certainly owns the hardware in case of leasing, they do not own your personal data. in your case you also own the hardware as i understand it. i would go with all that when requesting (demanding) a retreival of data from them. ofcourse your privacy laws might be different than ours. i hope they didn't encrypt the data and that you will be able to retreive it.

in any case good luck. the win 10 is not that bad (aside from it constantly reporting to MS - can be turned off with 3rd party program). 

after you save the data, please do join the "backup religion" ;)

Windows options: 
Areca
Duplicati
rdiff-backup


a couple of freeware options:
**Easeus Todo Backup Free**
Comodo backup
...

---

### Post by Ben_Cook on 2016-10-14
Thanks for the responses!  I actually replied yesterday but I must have  forgotten to click the 'post' button :oops: Anyway, I do own the  computer and have the receipt.  My issue is not making them do it;  they've said they will fix it, and I've been in touch with them.  The  issue is trust.  I worked for them for over 2 years and things get sent  away, not fixed, and sent back....so basically you're without your  computer for 4-6 weeks and still have the same problem. 
      If I  can get the info that I need using Ubuntu, that will be step one.  If my  wife chooses to actually install Ubuntu alongside Windows 10, that will  be another issue we'll have to deal with when/if the time comes.  I'm  hoping if we did manage to do that, we might be able to remove the  program causing these issues altogether.  I've been told this program  might be in a hidden partition, but I really don't know and feel like  I'm talking way above my skill/knowledge level:eek:. 
    Anyway, really really appreciate the help and I'll be doing this today,  so I'll update later on. And I am aware of the hibernation/fast startup  thing(thanks to oldfred), so I'm going to try and deal with that first.  Thanks again!

---

### Post by oldfred on 2016-10-14
Back when I only ran XP over 10 years ago, I converted to Firefox, Thunderbird, (then) OpenOffice, and we used Picasa.
So when I install Ubuntu my wife was still running all the same applications, so not as big of a change.

---

### Post by Geoffrey_Arndt on 2016-10-14
Yes, I'm with OldFred . . same scenario.   It's really too bad you can't convince the wife, as letting the installer take over the "whole disk" and wipe away Windows (after you've off-loaded your data) is MUCH easier than various dual-boot/Win10 set-ups, and more stable in the long run.   About a 1 hour or less job, versus a "weeks" without the PC?   That's just a total "non-starter" for me (e.g., not worthy of 5 minutes of thought).

---

### Post by Ben_Cook on 2016-10-14
I can appreciate that, but there's an issue....she plays games on Steam and the Sims 4, and I know it's possible to do some workarounds, but they are a bit of a hassle.  At least they were, last time I tried.

Edit-She said she'd give it a try rather than be without her computer for weeks=d>.  The biggest thing we need it for is billing customers, and that should be an easy transition given she's already using Libre office on Windows. The business stuff is already done.  She was able to boot her computer into safe mode and it was giving her about 60 seconds to use it before she was locked out.  So she was able to quickly save our business stuff, which was all in one place(it finished literally about 1 second before the computer restarted...it was like a spy movie:popcorn:)  So that's the real important stuff. Just wondering about the photos though - there is 10 years of pics and  we'd be looking at many times the amount of space our largest flash  drive has.  Would we have to do it piece by piece if we were to actually install Ubuntu?  Or would we be able to transfer them over during installation?

---

### Post by Geoffrey_Arndt on 2016-10-15
Good points Ben, but the issues are manageable.   For example, your photos (as well as other data) - - - no rule says you have to copy & paste all files in one fell-swoop.    Using a Live CD/DVD, just copy a portion and then transfer that portion to the other system or storage device.    Plus, prices for larger (64-128 GiB) usb-sticks (especially usb_v2) are very low now.   You should be able to pick one up via Amazon or the local big-box media retailer for about the the same price as a #1 combo at McDonalds.  

Just as another FYI - there is a great Linux rescue CD that you can get called "Parted Magic" . . . the download iso costs $9.00 (the dev. has put a lot of work/time into it).    But well worth it as it is (in my opinion), the best functioning Live Linux I've tried yet - - loads everything into ram (fast) and has most of the common rescue apps needed (recover, erase, fast-file manager, etc.).

[https://partedmagic.com/](https://partedmagic.com/)

---

