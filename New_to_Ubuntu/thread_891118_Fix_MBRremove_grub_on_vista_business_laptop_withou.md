---
title: "Fix MBR/remove grub on vista business laptop without destroying any data"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by computer_freak on 2008-08-15
As you have read in the title, I need to remove grub and/or fix my windows vista MBR.  I tried to install Linux to a portable USB harddrive, and it apparently installed grub to the vista HD.  This is a business laptop and I need to it be working very soon.  Can anyone help me restore or fix my MBR, or remove GRUB?
I get A grub error 21 when booting up..
Last time this happened to my desktop, and i had to get a new harddrive!  I can't have that happen! 
Also, I do not have access to a windows disc because the restore files are on the harddrive!  
Also, this is on a laptop if it helps.
Oh, and on another somewhat related note, I have another laptop that i need to the mbr on. I haven't installed linux on it though, so if someone with knowledge of the windows mbr sees this, I
'd really like it if they could help with that too. But the vista laptop is more importent.

---

### Post by gn2 on 2008-08-15
You can repair the MBR with a SuperGrub CD:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

If that doesn't get Vista to boot, try running "Startup Repair" from the Vista DVD or if you don't have one, you can download a Vista Recovery CD as an .iso from here:
[http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/](http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/)

---

### Post by kansasnoob on 2008-08-15
Go with this:

[http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/](http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/)

---

### Post by gn2 on 2008-08-15
> **kansasnoob said:**
> Go with this:

[http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/](http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/)

Snap! :D

---

### Post by computer_freak on 2008-08-15
You do know that that was what Gn2 had posted already? But also, thank you for helping. One question.  This won't delete any data from the hard drive, will it?  Oh, And one thing that is really confusing me.  How the heck did ubuntu put grub on a NTFS HD?!  unless it put it on a unallocated partion, i have no clue how it did it!

---

### Post by computer_freak on 2008-08-15
I see a problem here.  My vista install was 32 bit, not 64.  Am I thinking of x64 as 64 bit?  I just want to make sure this all goes well! :)

---

### Post by gn2 on 2008-08-15
> **computer_freak said:**
> You do know that that was what Gn2 had posted already? But also, thank you for helping. One question.  This won't delete any data from the hard drive, will it?  Oh, And one thing that is really confusing me.  How the heck did ubuntu put grub on a NTFS HD?!  unless it put it on a unallocated partion, i have no clue how it did it!

The default location for Grub is in the MBR on the main hard drive, if you want it installed somewhere else you have to tell the installer where to put it.

Using the Vista Recovery CD to run Startup Repair will not destroy any data, all it does is to fix the file(s?) Vista needs to use to boot.

I used it recently after re-sizing my Vista partition with Gparted caused it to be non-bootable, nothing was lost.

If you are in an yway concerned about potential data loss, use a Live CD and save the Vista partition(s) to an external drive beforehand.

Or physically remove the hard drive, put it in a USB enclosure and copy to another PC.

EDIT: The x86 version of the recovery CD is the 32-bit version.

---

### Post by mrsteveman1 on 2008-08-15
I was under the impression that by default grub is well behaved and leaves a standard partition selector in the 446byte MBR code section that just reads the active partition and jumps to the VBR code.

Anyway Vista is much better about fixing itself than XP was, especially if its just a simple boot code problem. That recovery CD should work well :D

---

### Post by computer_freak on 2008-08-15
OK, I am going to log out of bart pe( was trying to fix another laptops MBR errors with it, but couldn't) and in another win xp machine to try to download that recovery iso.  
thanks again!

---

### Post by Whatrymes on 2008-08-15
Hey:

 I do this all the time. Are you using Vista? The version doesn't matter. Download/install Easy BCD "http://neosmart.net/dl.php?id=1" Click "Manage Bootloader" and click "Reinstall Vista Bootloader."Then click Write MBR. This puts in a standard windows mbr. Delete Linux partitions.

---

### Post by gn2 on 2008-08-15
> **Whatrymes said:**
> Hey:

 I do this all the time. Are you using Vista? The version doesn't matter. Download/install Easy BCD "http://neosmart.net/dl.php?id=1" Click "Manage Bootloader" and click "Reinstall Vista Bootloader."Then click Write MBR. This puts in a standard windows mbr. Delete Linux partitions.

How do you install it on a Vista installation that will not boot?

---

### Post by cariboo on 2008-08-15
never mind

---

### Post by computer_freak on 2008-08-15
Update!!

I ran the tool, did the first one, and i got a clean bill of health the first time. No problems were detected. And it still gives me a grub loading error 21

---

### Post by gn2 on 2008-08-16
If you are getting a Grub error then the MBR has not been repaired.

Have you tried repairing it with a SuperGrub CD?

---

### Post by Whatrymes on 2008-08-16
You can boot into your Windows partition via Super Grub CD, Vista should still be fine, just the mbr is messed up. Or reinstall Ubuntu and GRUB will be repaired. Then you can boot into Vista.

---

### Post by computer_freak on 2008-08-18
OK, i am in super grub cd now. i have no clue what to do. I am going by the super grub wiki,and i got to the point where t says fix boot of windows under advance. please help! i am not sure if i should continue or do a different one!

---

### Post by gn2 on 2008-08-18
Yes, the fix boot of Windows is what you want to do.
This will overwrite and remove Grub.

---

### Post by computer_freak on 2008-08-18
uh oh.
I don't see windows in the list of OSs
just syslinux!!!!!!

Tell me i am doing something wrong, and i don't have to reinstall windows. The reinsall files were on that hard drive!
:(:cry:

---

### Post by caljohnsmith on 2008-08-18
Computer_freak, I believe what you want to do is boot up your Vista Recovery CD that you downloaded and do following in the recovery console:
```
bootrec /fixmbr
bootrec /fixboot

```
That will replace the MBR with the Vista boot loader.

EDIT: The Super Grub Disk restores a Windows MBR which will boot whichever partition is marked active (bootable) on the HDD; therefore you can use the Super Grub Disk to restore a Windows MBR for any Windows OS, including XP, Vista, or Windows 7.

---

### Post by computer_freak on 2008-08-18
Ah yes,
But, i do not have the cds. This HP laptop came with those file3s on the hard drive. i have a bartPE cd though, if we can use that.

---

### Post by computer_freak on 2008-08-18
OH, Nevermind. I misread your post. I'll try that when i get back from a dentist appt.

---

### Post by kansasnoob on 2008-08-18
> **kansasnoob said:**
> Go with this:

[http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/](http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/)

Sorry, I should have included the instructions:

[http://www.winvistatips.com/fix-mbr-a116.php](http://www.winvistatips.com/fix-mbr-a116.php)

Thanks Caljohnsmith!

---

### Post by computer_freak on 2008-08-18
Kanasasnoob, Thank you so much, and my thanks go to caljohn and GN2  also.  Kansas's first post was a bit confusing, but after those intructions, it worked perfectly.  Now i just have to run spinrite on that drive a get a new notebook hard drive.  Just found out:  I heard a grinding noise, and i got closer to the laptop, the diagnoses went from bad to worse. SMART indicates the drive is on its last legs- er, leg.  Did i mention a week ago i dropped diet coke on my other laptop and saw a shower of sparks( which was, both, destructive nad cool looking)? and my other laptop(i collect computers and install linux on them)  had a hard drive that was defective and the head tore off inside the case. and my desktop's PSU died a bit ago. Oh, computer woes! :D ;)  I think i might be cursed with something making all computers i use fail  very inconveniently.!:lolflag:

---

### Post by surfer57 on 2008-09-01
Thanks for the post, saved me from having to enter restore cmd prompt and typing in the code of which may or may not work....SUPER GRUB Rocks! gn2 Rocks - Your Kung Fu is strong!

---

