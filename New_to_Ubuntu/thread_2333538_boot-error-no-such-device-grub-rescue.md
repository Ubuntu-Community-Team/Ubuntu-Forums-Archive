---
title: "/boot-error-no-such-device-grub-rescue"
date: 2016-08-10
forum: New to Ubuntu
---

### Post by hareendran-c-nair on 2016-08-10
I am having issue while booting up. I have dual boot with windows 10 and ubuntu. It was working all this way and all of a sudden boom; the only thing i did was updating windows 10
I did the initial googling and did try method given by this thread
[http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue](http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue)

but still I am having issues. pasting the pastebin 
[http://paste2.org/Wny3BZEe](http://paste2.org/Wny3BZEe)

right now i have booted in using a live usb could someone please help me out?

---

### Post by oldfred on 2016-08-11
Windows 10 likes to not include a logical Linux partition in updates.
Use testdisk or parted rescue to restore missing partition.
You show large gap in space in extended partition.
```

/dev/sda4   223,877,118 1,465,147,391 1,241,270,274   5 Extended
/dev/sda5 1,452,675,072 1,465,147,391 12,472,320 82 Linux swap / Solaris 

```

 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 

These all further discuss either using testdisk or parted rescue.
 Used parted rescue
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)
backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT.txt
So you know sectors:
sudo parted /dev/sda unit s print 
   [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

