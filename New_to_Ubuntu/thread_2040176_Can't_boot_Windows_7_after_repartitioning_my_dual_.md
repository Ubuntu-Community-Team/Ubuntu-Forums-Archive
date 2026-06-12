---
title: "Can't boot Windows 7 after repartitioning my dual boot"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by Kollstag on 2012-08-10
I have a dual boot set up right now with Ubuntu 12.04 and Windows 7. I booted into a live, loaded up GParted, and had to futz around with partition sizes, which had already been established, as I'm trying to back up and move some stuff around. Now, having completed the movement and resizing of partitions, Windows 7 displayed Error: 0cx0000225, missing device, or something along those lines. I booted back into the live, and ran boot-repair, having had issues with boot managers before, and after looking around previous forum posts prior to this incident, and boot-repair has for the most part, solved my problems. However, at this particular juncture, that is no longer the case. Looking on other forum posts, it looks like I might have an issue with my partition tables, and if that is the case, how might I go about fixing as much? The other possible cause was that I just need to run a Windows 7 system repair, which unfortunately, I do not have access to currently. Any help and insights you can provide into this matter would be greatly appreciated. Thanks in advance.

---

### Post by ajgreeny on 2012-08-10
Oh dear!

I don't like the sound of your comment[COLOR=Red] "I booted into a live, loaded up GParted, and had to futz around with  partition sizes, which had already been established, as I'm trying to  back up and move some stuff around."[/COLOR]  I suspect this is the reason for your problems.

It is always better, in my opinion, to carry out any partition edits or changes for windows OS using the disk management utility that is in windows itself.  You may be able to get windows to boot again by running chkdisk, or whatever it's called, but how you do that when you can't boot to the OS, I am afraid I haven't a clue.

Can you get to safe mode by pressing F8, if I remember correctly, and do everything needed from the processes of booting, rather than the full OS.

---

### Post by Kollstag on 2012-08-10
I cannot currently access safe mode unfortunately.

---

### Post by oldfred on 2012-08-10
Windows partition boot sector has to have the correct partition start & size info in it that is the same as the partition table. Some have been able to make a change to Windows, but then reboot & it runs chkdsk to repair itself. But many have issues, so it is always best to use Windows tools to resize Windows partitions, but not create new partitions as it may convert to dynamic partitions.

Also it is best to have a repairCD or liveCD or the current version of every operating system you have installed.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

If you know someone else with a Windows system with the same 32 oor 64 bit version, you can create a repairCD from that system. We used to have a link to a free site for the repairCD, but the now charge $10  if you cannot get one any other way.

May be best to post link to your BootInfo report from the Boot-Repair - Other Options.

---

### Post by Kollstag on 2012-08-10
The repair disk seems to be working, thanks so much!

---

