---
title: "HOWTO: Windows 2000 GRUB FIX / TRICK"
date: 2005-02-18
forum: Outdated Tutorials &amp; Tips
---

### Post by wallijonn on 2005-02-18
Problem: After installing Ubuntu, GRUB will not load Windows 2000 or WXP. 

Error message:
[quote=morphodone]
[COLOR=Blue]Booting 'Windows NT/2000/XP'

root (hd2,0)
Filesystem type unknown, partition type 0x7
Savedefault
makeacitve
chainloader +1[/COLOR]
[/QUOTE]

If you can access another W2KP machine you can:

1] Login as Administrator
2] [COLOR=Blue]Tools -> Folder Options -> View -> show hidden files & folders, Apply[/COLOR]
3] [COLOR=Red]Copy C:\ (root) NTDETECT.COM, ntldr -> A:[/COLOR]
4] open a CMD window ([COLOR=Blue]Start -> Run ->[/COLOR] [COLOR=Red]cmd[/COLOR])
5] [COLOR=Red]attrib a:*.* -h -s[/COLOR]

(Or you can 
[COLOR=Red]attrib ntdetect.com -h -s -r[/COLOR]
[COLOR=Red]attrib ntldr -h -s -r[/COLOR]
then copy to A:  )

Walk the floppy over to your PC

6] Boot with W2KP CD, [COLOR=Red]Repair[/COLOR], [COLOR=Blue]Command Console[/COLOR] (insert Admin password)
7] [COLOR=Red]cd ..[/COLOR]
8] [COLOR=Red]Copy a:\*.* C:\*.* [/COLOR]
9] [COLOR=Red]exit[/COLOR] the [COLOR=DarkGreen]Command Console prompt[/COLOR] (which will cause an automatic reboot)
10] Remove floppy & CD

Grub should now boot into W2KP.

11] Login into Administrator Account
12] [COLOR=Blue]Start -> Run ->[/COLOR] [COLOR=Red]cmd[/COLOR]
13] [COLOR=Red]attrib DETECT.COM +s[/COLOR]
14] [COLOR=Red]attrib ntldr +s[/COLOR]
15] exit command (cmd) prompt window
16] Open C:\, Right click those two files, properties, set hidden, apply (1 at a time)

(Or you can 
[COLOR=Red]attrib ntdetect.com +h +s +r[/COLOR]
[COLOR=Red]attrib ntldr +h +s +r[/COLOR]
after copying from A:, and before rebooting).

While I have not tested this trick on WXP, it did work for me on W2KP.

Maybe we should start suggesting that people copy [COLOR=Blue]NTDETECT.COM[/COLOR] & [COLOR=Blue]ntldr[/COLOR] to floppy (using the above method) _before_ starting the Ubuntu install...

If you do not have access to another W2KP machine you will have to format a floppy and use Ubuntu to copy the files from the W2KP install CD to the floppy.

I believe the WXP files are in C:\windows\system32\config\system\

btw, the LiveCD will read a NTFS hd (at least a PATA drive).

-------------------------------------------------------------------------

This has been posted as a HOWTO in the hope that others may be able to narrow the GRUB problem even further. I would like to know if the afforementioned files need to be put in the root for WXP or if they can be copied to their 'correct' directory.

.

---

### Post by dewey on 2005-02-19
I had the same problem, but went about solving it very differently.

I went into my bios, and looked up my IDE settings, ang changed it from "Auto" to "LBA", setting it to "Large" also works aswell.

---

### Post by wallijonn on 2005-02-21
Setting the BIOS to Large or LBA from Auto doesn't always work.

I replicated the above error quite by accident - I installed W2KP then Ubuntu, only to find out that W2KP wouldn't start. I did not change anything in the BIOS. All I did was copy those two files and everything worked fine.

---

### Post by thestarman on 2005-03-01
> **wallijonn]Problem: After installing Ubuntu, GRUB will not load Windows 2000 or WXP. ....
While I have not tested this trick on WXP, it did work for me on W2KP.
....
If you do not have access to another W2KP machine you will have to format a floppy and use Ubuntu to copy the files from the W2KP install CD to the floppy.[/QUOTE]
   In your "W2KP" terms above, what does the 'P' stand for?  I know only of W2K.  said:**
> I believe the WXP files are in C:\windows\system32\config\system\ 
   I couldn't even find such a directory on the XP install I looked at... there was, however, a "C:\windows\system32\config\system" **file** of 3.4+MB in size!  And again, no **ntdetect.com** nor **ntldr** files were found on this system.
> This has been posted as a HOWTO in the hope that others may be able to narrow the GRUB problem even further. I would like to know if the afforementioned files need to be put in the root for WXP or if they can be copied to their 'correct' directory.
   I'll help others if I can, but I believe we need more data to go on!  When such a problem occurs (Windows not booting after installing Ubuntu), there could be many reasons, sometimes as easy as just COLD rebooting (just to be sure) a system, so the BIOS has a chance to see the new data in the Partition Table.
   Very often, people don't share enough info, keep back info that they think can't possibly have anything to do with a problem, yet it very much does!  For example, one guy deleted an old Win 98 partition at the beginning of his drive and then proceeded to install Linux in it... when he tried to boot up Windows XP that was in his second partition, it wouldn't work.  Why?  BECAUSE ALL Windows NT/2k/xp/2003 OSs REQUIRE YOU TO HAVE A MICROSOFT TYPE (FAT16/FAT32/NTFS) PARTITION as the very first partition of your first hard drive!!!  They stupidly overwrite the Boot sector there with their own boot code, so it's impossible to run any of these OSs with a Linux OS in that partition... well, unless you fool it into thinking a 2nd HDD is really the first one, but even then you must have an MS-type partition first on that drive.

   All that to say: I'm not exactly sure why your Win 2000 OS wouldn't boot up the first time you tried until after copying those files!  It may not be because you did so!  On a Win 2000 OS, they should have already been there!!  What SP version did you have? What SP version of the files did you use to copy to it?  These details can be really important in figuring out things... though we may never know exactly what your problem was at this later date.  What's in the very first partition of your first HDD?  What was in the MBR sector before you installed Ubuntu?  Did you install GRUB to the MBR?  All data such as this must be known to figure out this problem!

(( RE: "dewey"'s comment about resetting the BIOS from 'AUTO' to 'LBA' or possibly 'LARGE' is more often associated with a Linux install that messes up your Partition Table parameters! ((If you have a Windows FAT32 partition that needs to be resized, do not use any utils from Linux CDs unless you're absolutely sure they will work with the OS(s)/BIOS/HDD/Partition Table you have!  Many new Linux users from about July 2004 to present lost the ability to access their Windows partitions after installing Linux distros such as SuSE, RedHat Fedora, Mandrake, etc. etc. that newer kernels which showed up around then. It appears that they all used parted to resize those partitions; and not only did parted use 16 instead of 255 heads in the PT, but resized the Windows partitions so they didn't end/begin on a cylinder boundary... Windows don't like that.  OK, enought of that... ))
   Anyway, seems like an OK thing to try using the 'LBA' setting first; I'm a bit leary about using the 'LARGE' setting... if you do, and it doesn't work, don't forget to set it back to 'AUTO'.
   There's a setting inside of GRUB itself though which forces GRUB to use 'LBA32,' but most often that's only a problem if it can't find its own files in the Linux partition. ))


Daniel (aka, The Starman).

---

### Post by tranceConscious on 2005-03-14
In winxp all you have to do to fix this problem is to boot from the cd, use the recovery console, login to your windows installation and then use
fixmbr and fixboot, but that fux up grub though.

Now What about grub not wanting to load my windows installation?
hoary is on a different hd, my primary master, grub is configured fine but it won't boot into windows?!!!?!!?

---

### Post by CrashTECH on 2005-04-13
[QUOTE=tranceConscious]In winxp all you have to do to fix this problem is to boot from the cd, use the recovery console, login to your windows installation and then use
fixmbr and fixboot, but that fux up grub though.

Now What about grub not wanting to load my windows installation?
hoary is on a different hd, my primary master, grub is configured fine but it won't boot into windows?!!!?!!?[/QUOTE]
 I have a similar (but different problem) I had installed Hoary and everything worked fine. Well, I went through the guide for people who were new to Ubuntu and downloaded the 686 via apt-get which installed fine (great) I installed some more packages (apache, xmms, etc) rebooted to get back into my windows XP, and it was not in grub at all. However there was an entry for 686/686 recovery, 386/386 recovery, and memtest... 'Other' was listed, but when I went to hit it, there was nothing there... I looked in the menu.lst and windows was not listed.

Now if I fixmbr/fixboot to get windows back, how on earth do I get Ubuntu back without fuxin up windows again? (Or having to reinstall ubuntu, re-download the 686 and have the same problem over again?). I have not been able to boot Knoppix becuase it doesnt like the cd rom in my notebook for whatever reason... it thinks it needs to find a SCSI cd rom, and it can't find one, so it crys and locks up.

---

### Post by grameshg on 2005-04-22
[QUOTE=wallijonn]Problem: After installing Ubuntu, GRUB will not load Windows 2000 or WXP. 

Error message:


If you can access another W2KP machine you can:

1] Login as Administrator
2] [COLOR=Blue]Tools -> Folder Options -> View -> show hidden files & folders, Apply[/COLOR]
3] [COLOR=Red]Copy C:\ (root) NTDETECT.COM, ntldr -> A:[/COLOR]
4] open a CMD window ([COLOR=Blue]Start -> Run ->[/COLOR] [COLOR=Red]cmd[/COLOR])
5] [COLOR=Red]attrib a:*.* -h -s[/COLOR]

(Or you can 
[COLOR=Red]attrib ntdetect.com -h -s -r[/COLOR]
[COLOR=Red]attrib ntldr -h -s -r[/COLOR]
then copy to A:  )

Walk the floppy over to your PC

6] Boot with W2KP CD, [COLOR=Red]Repair[/COLOR], [COLOR=Blue]Command Console[/COLOR] (insert Admin password)
7] [COLOR=Red]cd ..[/COLOR]
8] [COLOR=Red]Copy a:\*.* C:\*.* [/COLOR]
9] [COLOR=Red]exit[/COLOR] the [COLOR=DarkGreen]Command Console prompt[/COLOR] (which will cause an automatic reboot)
10] Remove floppy & CD

Grub should now boot into W2KP.

11] Login into Administrator Account
12] [COLOR=Blue]Start -> Run ->[/COLOR] [COLOR=Red]cmd[/COLOR]
13] [COLOR=Red]attrib DETECT.COM +s[/COLOR]
14] [COLOR=Red]attrib ntldr +s[/COLOR]
15] exit command (cmd) prompt window
16] Open C:\, Right click those two files, properties, set hidden, apply (1 at a time)

(Or you can 
[COLOR=Red]attrib ntdetect.com +h +s +r[/COLOR]
[COLOR=Red]attrib ntldr +h +s +r[/COLOR]
after copying from A:, and before rebooting).

While I have not tested this trick on WXP, it did work for me on W2KP.

Maybe we should start suggesting that people copy [COLOR=Blue]NTDETECT.COM[/COLOR] & [COLOR=Blue]ntldr[/COLOR] to floppy (using the above method) _before_ starting the Ubuntu install...

If you do not have access to another W2KP machine you will have to format a floppy and use Ubuntu to copy the files from the W2KP install CD to the floppy.

I believe the WXP files are in C:\windows\system32\config\system\

btw, the LiveCD will read a NTFS hd (at least a PATA drive).

-------------------------------------------------------------------------

This has been posted as a HOWTO in the hope that others may be able to narrow the GRUB problem even further. I would like to know if the afforementioned files need to be put in the root for WXP or if they can be copied to their 'correct' directory.

.[/QUOTE]
 Hi

I read this from Gentoo forum but i believe it should work for all grub boot loader in general.
Also this is applicable if and only if the windows O/S resides in a separate HD.

Edit your grub.menu file like this ( this will work for all Windows OS)
title=Windows 2000 Pro
map (hd0) (hd1) # Tell the first hard drive to pretend to be the second
map (hd1) (hd0) # Tell the second hard drive to pretend to be the first
root (hd1,0) # Tell GRUB Windows is on /dev/hdb1 (No pretending here)
rootnoverify (hd1,0) # GRUB won't attempt to mount the Windows drive
makeactive # Sets the partition to active
chainloader +1 # Tells GRUB to load the Windows bootloader when done

I am able to boot both the OS with no problems. Hope it works for everyone.

---

