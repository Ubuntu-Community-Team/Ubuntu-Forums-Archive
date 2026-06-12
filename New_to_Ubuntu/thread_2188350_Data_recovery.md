---
title: "Data recovery"
date: 2013-11-16
forum: New to Ubuntu
---

### Post by arcafonk on 2013-11-16
Well, ahem, well...

I guess this is the rigth forum section to post.

Bad news first, I'm a Windows guy. And I have a problem. Just don't laugh at me yet.

Let's simplify my problems by saying my data HDD crashed, and I think Ubuntu could be a solution to recover my data.

I've got :
- 2 old HDD : the C:/ with Win7 on it and 4.67 Go left (over 69.something), and another one that I can detect but can't read.
- 2 brand new and shiny HDD, not formated yet.

Now I'm not really sure what to do. I'm imagining I would try to :
1 - Format one new HDD and install Ubuntu on it. (question a : how ? Do you know a simple way to do this ? I allready installed Ubuntu on a few computer but never on an unformated disk before : what format should I use, etc ?).
2 - Plug the second disk, format it in FAT32 (i think win7 still can read fat32)
3 - Save the data from the corrupted disk to the FAT32 disk via Ubuntu since the files can't be read via Windows.
4 - Format the ubuntu disk in NTFS, install windows 7 back
5 - copy the FAT32 disk on the NTFS
6 - format the FAT32 in NTFS
7 - show to my little little nephem how much seconds could fly the damaged disk when throwed by the windows. Try to aim the 2nd floor grumpy guy with the same shot.

Now you can laugh at me :)

Well, do you think I'm trying something really easy or difficult ? Do you know some links about this or something ? Am I trying something stupid ?

welp :)

---

### Post by rburkartjo on 2013-11-16
arc try this download redo backup burn iso to disk. then boot from disk and see if you can access any of your files. 

[http://www.addictivetips.com/windows-tips/redo-backup-recovery-live-cd-that-recovers-your-hard-drive/](http://www.addictivetips.com/windows-tips/redo-backup-recovery-live-cd-that-recovers-your-hard-drive/)

---

### Post by coffeecat on 2013-11-16
@arcafonk, you don't have to install Ubuntu to a hard drive to run it. You can burn the Ubuntu ISO to a DVD, boot the DVD up and run a live Ubuntu session. It'll be a tad sluggish but you can use it to recover files. Also, don't bother with FAT32. NTFS read-write is reliable in Ubuntu.

The ISO that rburkartjo recommends looks to be excellent with several useful utilities, but if it's just file copy you want, Ubuntu will work for that just fine. Here's a useful wiki page on getting the ISO burnt to DVD:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by arcafonk on 2013-11-16
Thank you guys, I'll let you know how much time the HDD flied :)

---

### Post by heir4c on 2013-11-16
You can also make a Ubuntu Live USB with Unetbootin (for Windows): [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by arcafonk on 2013-11-17
That's the solution I will use. I'm installing a 13.10 on a USB Key that I will keep preciously as "the key to use when a drive crash" with the links you provided on How-to's.
"I'm-confident-I'm-confident-I'm-confident-I'm-confident" is my mantra rigth now :)

---

### Post by arcafonk on 2013-11-19
Ok, so the answer is 13sec 86, missed the old man :)

Well, I had a strange thing that made me detect the drive in Win7 so I could copy the files on the new disk before making the old fly away.

I tried to install ubuntu on a usb key but it never booted (the bios is USB boot #1), that's strange. Anyway my problem is solved. i'll keep the key anyway :)

Thanks guys anyway for the very quick answer, I'm sure it would have worked.

---

