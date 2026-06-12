---
title: "will someone rid me of this troublesome software"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by kevin mcavinchey on 2012-05-20
I bought ubuntu 10.04.1 in pc world with book. Installed with dual boot option in dell xps with windows 7. It worked well for a few eeks and the hung when i chose it thereafter. I tried to reinstall but it hangs after delete a little way into install.I cant delete I cant reinstall deadend. I would now settle for getting rid of it and forget about linux . Anyone help?
cheers kevin

---

### Post by Lisiano on 2012-05-20
I don't know about disks that come in PC World, but you can download the latest 12.04 iso from [ubuntu.com](ubuntu.com), it's possible their disk is either faulty or was modified.

It might be your particular hardware not being friendly enough, we would be glad to help you with making Ubuntu run on it if you wish to give Ubuntu and Linux in general another chance.

If you really want to get rid of Ubuntu, you can just delete the partition containing it.

---

### Post by holiday on 2012-05-20
There may be a problem with your local disk. Try a live CD and run a disk check. 

When you re-install, do you re-partition? You could try that if you haven't. You could follow Lisiano's advice - delete the partition, and then install to a new clean partition.

---

### Post by wilee-nilee on 2012-05-20
Boot a XP install disc and follow this link for putting the MS bootloader in the mbr, you can then remove the Ubuntu with a live cd of ubuntu or any partitioner basically, gparted has a live cd download.

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

If you don't have a XP disc we can slip a bootloader in called lilo from a ubuntu install or live cd this wil boot XP straight in so you can remove the ubuntu setup. 

Let us know what you want to do. :)

---

### Post by HiImTye on 2012-05-20
to get rid of linux, just boot from the install disc of your OS of choice and delete and/or repurpose the linux partition. for instructions on how to do so I suggest you look at your OS of choice's help files/manual

---

### Post by anewguy on 2012-05-20
Since the OP has a dual-boot system, they CAN'T just delete the ubuntu partition - doing so would cause the system not to boot until the MBR is restored.  

There are many ways of deleting ubuntu, if that's what you decide to do.  My suggestion:

[LIST]
[*]boot into Windows
[*]download (from downloads.com) a program called "mbrfix" and unpack it
[*]read the html help files for how to use it (it's really simple).  This will reset the master boot record so that only Windows will boot, and remove any references for grub (if you didn't - the grub loader would look for your ubuntu partition for the information it needs, not find it, and you wouldn't be able to boot your PC
[/LIST]

That takes care of the MBR and any potential problems.

NOW it's safe to delete the ubuntu partition:

[LIST]
[*]boot off an ubuntu livecd
[*]run the disk utility and just delete the ubuntu partition
[/LIST]

Don't just delete the ubuntu partition without resetting the mbr first or you'll just be in for a series of headaches you can easily avoid.

Dave ;)

---

### Post by wilee-nilee on 2012-05-20
> **anewguy said:**
> Since the OP has a dual-boot system, they CAN'T just delete the ubuntu partition - doing so would cause the system not to boot until the MBR is restored.  

There are many ways of deleting ubuntu, if that's what you decide to do.  My suggestion:

[LIST]
[*]boot into Windows
[*]download (from downloads.com) a program called "mbrfix" and unpack it
[*]read the html help files for how to use it (it's really simple).  This will reset the master boot record so that only Windows will boot, and remove any references for grub (if you didn't - the grub loader would look for your ubuntu partition for the information it needs, not find it, and you wouldn't be able to boot your PC
[/LIST]

That takes care of the MBR and any potential problems.

NOW it's safe to delete the ubuntu partition:

[LIST]
[*]boot off an ubuntu livecd
[*]run the disk utility and just delete the ubuntu partition
[/LIST]

Don't just delete the ubuntu partition without resetting the mbr first or you'll just be in for a series of headaches you can easily avoid.

Dave ;)

Did you read the whole thread?

---

### Post by Lisiano on 2012-05-20
> **anewguy said:**
> Since the OP has a dual-boot system, they CAN'T just delete the ubuntu partition - doing so would cause the system not to boot until the MBR is restored.
Ah, completely forgot about MBR. It's also possible to fix it from a Windows 7 installation/recovery DVD. From there open a command prompt (Repair PC -> Command Prompt or Shift+F10) then run this
```
bootrec /fixmbr
```
No need for 3rd party software.

---

### Post by anewguy on 2012-05-21
> **wilee-nilee said:**
> Did you read the whole thread?

Yes I did.  To me, anyway, mbrfix running simply in Windows is easier that booting a Windows cd/dvd so you can do it there because NOW the mbr is messed up.  Even the post right before mine said to simply delete the partition - no mention of resetting the mbr.

If you look at your post, you recommended an XP disc.  The OP stated they are dual-booting Windows 7 and ubuntu.  I doubt Windows 7 is going to like XP messing with the MBR. 

I stand by my post - mbrfix is simple, can be done BEFORE you mess things up, and works for all versions of Windows.  If you're one of the many, many people with a newer (and for that matter, not even that new any more), your system was delivered WITHOUT a Windows disc.  Mbrfix allows you to do it with no OS disk.

Read my post - I DID read the thread, and to be honest I just disagreed with your approach of using the XP, or for that matter, ANY Windows OS disk.  Most users aren't familiar with what is required.  Most users do know how to download a file and execute it.  And, to repeat, there was a post way AFTER yours, just before mine, saying to simply delete the partition - with no mention (perhaps they don't have knowledge) of the MBR.

---

### Post by anewguy on 2012-05-21
> **Lisiano said:**
> Ah, completely forgot about MBR. It's also possible to fix it from a Windows 7 installation/recovery DVD. From there open a command prompt (Repair PC -> Command Prompt or Shift+F10) then run this
```
bootrec /fixmbr
```
No need for 3rd party software.

Hi friend!  As I noted in my reply to willie-nillie, there are a lot of users out there that don't know squat about booting an OS cd/dvd and running the commands.  Most users do know how to click "download" and to execute a program.  A lot of the new PC's don't come with an OS disk, so the user wouldn't have a way to do it.  That's why I have recommended in the past and still recommend mbrfix.  No OS cd/dvd needed - for most users no special knowledge needed either as a lot of the users out there are single-disk systems - like you'd buy at the store, which makes mbrfix very easy.

Hope things are going great with you!!

your friend,
Dave ;)

---

### Post by Mark Phelps on 2012-05-21
> **kevin mcavinchey said:**
> Anyone help?
cheers kevin

If you can get into Win7, another approach is to use EasyBCD, which you can download from the NeoSmart Technologies site.

Install that, run it, click on the BCD Backup/Repair button, then under BCD Management Options, click Re-Create/Repair boot files.

Once that is done, reboot into Win7, then use the Disk Management utility to remove the Linux partition(s) and replace them with NTFS partitions.

---

### Post by Lisiano on 2012-05-21
> **anewguy said:**
> Hi friend!  As I noted in my reply to willie-nillie, there are a lot of users out there that don't know squat about booting an OS cd/dvd and running the commands.  Most users do know how to click "download" and to execute a program.  A lot of the new PC's don't come with an OS disk, so the user wouldn't have a way to do it.  That's why I have recommended in the past and still recommend mbrfix.  No OS cd/dvd needed - for most users no special knowledge needed either as a lot of the users out there are single-disk systems - like you'd buy at the store, which makes mbrfix very easy.

Hope things are going great with you!!

your friend,
Dave ;)
Ola mein friend, I assumed since the OP was able to boot from an Ubuntu CD he would know how to boot of another CD/DVD. Also most laptops come with just a recovery disk which still gives access to a cmd from Shift+F10 (I think), not all but most do. Though you are right on the part of not having a recovery disk, a 3rd party tool would make more sense in those conditions.

Either way I'm fine and managed to convert 2 good friends over to Ubuntu. Hope you are doing well too.

---

### Post by anewguy on 2012-05-21
> **Mark Phelps said:**
> If you can get into Win7, another approach is to use EasyBCD, which you can download from the NeoSmart Technologies site.

Install that, run it, click on the BCD Backup/Repair button, then under BCD Management Options, click Re-Create/Repair boot files.

Once that is done, reboot into Win7, then use the Disk Management utility to remove the Linux partition(s) and replace them with NTFS partitions.
That's a nice, simple, no-OS disk option - elegant, Mark!

Thanks - hope you're doing ok as well!

dave ;)

---

