---
title: "Dual boot"
date: 2013-09-27
forum: New to Ubuntu
---

### Post by JuanLuna on 2013-09-27
Hi, i just install ubuntu 12.04 (dual boot) & i found some file on my drive D: (Backup).

[IMG]http://i1238.photobucket.com/albums/ff500/NickelSulfate/Newbiequestion.png[/IMG]

Files:
* Boot
* Recovery
* $ RECYCLE.BIN
* Recycler
* System Volume Information
* AUTOEXEC.BAT
* Boot.ini
* Boot.BAK
* Bootmgr
* BOOTNXT
* BOOTSECT.BAK
* CONFIG.SYS
* IO.SYS
* MSDOS.SYS
* NTDETECT.COM
* ntldr
* win7.ld
* YJSUQ

Q: is it safe to delete those file without messing my Other OS?

Thanks

---

### Post by Rob Sayer on 2013-09-27
A: I don't think so.

---

### Post by mansonfan78 on 2013-09-27
I wouldn't recommend it.  I'm assuming the other OS is Windows 7.  It created that partition as a backup for restore purposes.  You technically could delete it, but if anything happened to Windows and you needed to restore you'd be s.o.l.  So, unless you really need the hard drive space, I'd leave it alone.

---

### Post by UltimateCat on 2013-09-27
Congrats on your fresh install of Ubuntu!

If you don't have the Microsoft Windows CD's to recover your OS 'deleting those files' would not be a wise practice!

---

### Post by JuanLuna on 2013-09-28
> **Rob Sayer said:**
> A: I don't think so.

> **mansonfan78 said:**
> I wouldn't recommend it.  I'm assuming the other OS is Windows 7.  It created that partition as a backup for restore purposes.  You technically could delete it, but if anything happened to Windows and you needed to restore you'd be s.o.l.  So, unless you really need the hard drive space, I'd leave it alone.

> **UltimateCat said:**
> Congrats on your fresh install of Ubuntu!

If you don't have the Microsoft Windows CD's to recover your OS 'deleting those files' would not be a wise practice!

Thank you guys for your reply, i have another Q: if its ok. Can i still boot on my Other OS even if i delete those file? what i mean is, i never use the backup feature on that OS - its useless anyway, cause when your PC is infected with unwanted programs the backup "thingy" is 80% @ risk of being infected too. Maybe its just an OS critical update backup or something like that. Can anyone confirm please :)

Thank You,


(reason: its kinda annoying that every time i open my Drive D:[Backup file Drive] i see or accidentally click that alien file)

---

### Post by sandyd on 2013-09-28
> **fKktmQG said:**
> Thank you guys for your reply, i have another Q: if its ok. Can i still boot on my Other OS even if i delete those file? what i mean is, i never use the backup feature on that OS - its useless anyway, cause when your PC is infected with unwanted programs the backup "thingy" is 80% @ risk of being infected too. Maybe its just an OS critical update backup or something like that. Can anyone confirm please :)

Thank You,


(reason: its kinda annoying that every time i open my Drive D:[Backup file Drive] i see or accidentally click that alien file)

Short Answer: Yes.
Long Answer:
If you delete the partition, you will never be able to install windows. Again. Today, most OEMs are not happy with handing out OEM Windows 7 DVDs, and dont include one with the computer. If you have one, then thats fine, if not, see below.

IF you dont have an OEM Windows 7 DVD, create recovery discs, which I advise you to do _before_ deleting the partition...

After you create the recovery discs, you can delete the partition safely and still have a way to reinstall windows cleanly.
Dont remember, but I think that it supports creating the recovery discs on USB, depending on your manufacturer.

For example, HP.. [http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01867124](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01867124)

Btw - noticed that your username is part of a side effect of SSO, if you want to change it, feel free to post in -> [http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

---

### Post by JuanLuna on 2013-09-28
> **sandyd said:**
> Short Answer: Yes.
Long Answer:
If you delete the partition, you will never be able to install windows. Again. Today, most OEMs are not happy with handing out OEM Windows 7 DVDs, and dont include one with the computer. If you have one, then thats fine, if not, see below.

IF you dont have an OEM Windows 7 DVD, create recovery discs, which I advise you to do _before_ deleting the partition...

After you create the recovery discs, you can delete the partition safely and still have a way to reinstall windows cleanly.
Dont remember, but I think that it supports creating the recovery discs on USB, depending on your manufacturer.

For example, HP.. [http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01867124](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01867124)


Thank you 

> **sandyd said:**
> Btw - noticed that your username is part of a side effect of SSO, if you want to change it, feel free to post in -> [http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

oh i see, i thought i can only edit my username when i reach 10 post. thanks again mod sandyd

---

### Post by coffeecat on 2013-09-28
> **fKktmQG said:**
> 
(reason: its kinda annoying that every time i open my Drive D:[Backup file Drive] i see or accidentally click that alien file)

@fKktmQG, another thing to remember is that Windows and Linux use different methods to make files and folders hidden. What you are seeing in Ubuntu are the files that are hidden in Windows. It's best to get into the habit of ignoring such files. I mentally blank out such things as $RECYCLE.BIN when accessing a NTFS partition from Ubuntu.

Conversely, Windows will show you things that Linux hides with a preceding period in the filename. For instance, if you were to delete files from that partition (I don't suggest you do, though), Ubuntu would make a folder called .Trash_1000 which is more or less equivalent to Windows' $RECYCLE.BIN. You have to press ctrl-H to see it in Ubuntu's file manager, but Windows will show it as a normal folder.

---

### Post by JuanLuna on 2013-09-28
Thanks for all the help guys. two thumbs up + salute

---

