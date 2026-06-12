---
title: "Install xubuntu, new partition, shrink win 7 most as possible"
date: 2014-09-30
forum: New to Ubuntu
---

### Post by christoph5 on 2014-09-30
hi i want to instal xubuntu and keep my windows 7 but i dont really want to use it a lot any more and would like to shrink the C: partition mutch as possible almost maybe just 5 gb or somthng can be used, i also have a Vista bootloader partition it shows on the xubuntu install, but not in "my computer" and it is on 10 gb, that is something id lke to delete forever if possible?

my harddrive is about 300 GB and this laptop is new to me and the WIndows 7 was resently instaled over Windows Vista, not by me, the xubuntu installation comes to partitoning and is showing i have 2 partitions a Win 7 and Vista bootloaders partitions, i would like to create a big as possible New partioion for xubuntu with most as poisible space as possible,
how do i do it? i have tried on my own but not know exactly what to choose in options, it gave me just an error

---

### Post by oldfred on 2014-09-30
Windows normally only has all its boot files in the one NTFS partition with the boot flag. Do not delete Vista until you know if or have copied Windows 7's boot files into the Windows 7 install. And move boot flag to the Windows 7 NTFS partition. Windows 7 often has two partitions one is just boot, but with Vista it may just have boot files in the Vista partition.
Windows wants 30% free space to work, and at 10% free you just about cannot run defrag as it has no working room.
So you need to houseclean a lot, defrag a couple of times, then shrink but leave about 30% free inside NTFS partition.

With Windows 7 better to shrink using Windows tools & reboot immediately to run chkdsk and repair itself to its new size. But do not create partitions with Windows, use gparted for all Linux partition changes.

 Resize Vista partition, similar for 7
If problems, try disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don&#8217;t forget to turn them on back later.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
shrink the primary partition from the Windows MMC or Disk Management.
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)
You can also try downloading and installing the FREE version of Partition Wizard in Win7. It may allow you to safely shrink the Win7 OS partition more than does MS.

You can make a full backup of Windows also, and may want a repair CD or flash drive in case you need to repair it.
      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Then you can use gparted to resize Linux  partitions. If dual booting you may want a shared NTFS data partition. But if rarely using Windows you can use separate /home or data partition(s) that are Linux formatted.

---

### Post by christoph5 on 2014-09-30
hey are you telling me to do all the stuff step by step??? because i have started from your first link given:
i started doing stuff on the link [http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
and after the 2nd step on there i have deleted alot of stuff and maybe regreting now,i did [http://www.howtogeek.com/howto/windows-vista/disable-system-restore-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/disable-system-restore-in-windows-vista/) and espessially that im regreting, without knowing how, can this bad?

What do i doo now.......

---

### Post by Michael_McKenney on 2014-09-30
Backup everything before you do anything.  My method was unplug by Windows drive and install to another drive.  You can break Windows when shrinking it.  So backup your data first to a few places off the computer.

---

### Post by christoph5 on 2014-09-30
> **oldfred said:**
> 
 Resize Vista partition, similar for 7
**If problems**, try disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don&#8217;t forget to turn them on back later.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)


i mean,because i dident read this clearly before i started and acctualy thought u meant i shoud do the whole thing?
and because im already confused at step 3 and cant find things, so what should i do from here? 
i mean i dont acctualy need to format almost the entire windows 7 drive if not nesseserry if i will be left with 30% of my 300 GB anyway?

---

### Post by oldfred on 2014-09-30
I think the very first step in the howtogeek.com link was backup. Did you do that first?

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
> I would also suggest that if you are trying to [configure a dual-boot]("http://www.howtogeek.com/howto/windows-vista/install-windows-xp-on-your-pre-installed-windows-vista-computer/")  system, your best bet is to backup all your data, and setup a fresh new  dual boot system, remembering to install the oldest OS first. (XP  before Vista, and Linux last)


And I gave links to backup solutions in case you were not familiar. 

What did you delete. Normal housecleaning should not delete anything vital. And turning off  hibernation and some of the other settings can just be turned on again. 

If you did delete something vital stop using system as you may be overwriting deleted data.

---

### Post by christoph5 on 2014-09-30
no i dident, i dont need backup as i said this is a fresh install of windows 7, what would i backup?
i did things too fast, i deleted alot of files around 20 gb, including was windows.old

i am now at step 3: Disable the pagefileand i dont know how to do it! 

dont understand why i acctualy had to
> _Now simply click the radio button to disable System Protection. (Note again that this is probably a bad idea)._

*from [http://www.howtogeek.com/howto/windows-vista/disable-system-restore-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/disable-system-restore-in-windows-vista/)*
i choose 0% and something wierd happened
¨why should i continue doing these wierd steps, when i am going to stay left with 30% of my 300 gb harddrive anyway?

---

### Post by oldfred on 2014-09-30
If you can shrink it enough then you do not have to do anything.

It is in many cases you cannot shink it by very much leaving much more than 30% unused space inside the NTFS partition. 

And if a new install, it often is easier to create the size NTFS partition you want in advance with the boot flag and install to that. Then no issues at all.

---

