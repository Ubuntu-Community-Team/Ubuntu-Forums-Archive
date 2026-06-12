---
title: "resize partition problem"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by johnsg on 2011-10-05
Hi,
I'm relatively new to Ubuntu...used on an old Dell before it died. I'm trying to install 11.04 on a brand new Lenovo x120e. Everything worked fine when running from the USB so I went ahead to install alongside Windows 7. 

Problem came at the resize partitions step...nothing happened for over an hour. A few times the "Connect to wireless" dialog came up (which I had already connected to). I know the wireless works because I'm using it on this computer.  

I thought this might be the problem, so I plugged in the ethernet jack. Then something happened as the Install window closed and a long list of text appeared, ending with 

[ 3186.639813] panic occurred, switching back to text console

Now the computer is completely frozen and I'm not sure what to do...

Thanks much for any help.

---

### Post by Quackers on 2011-10-05
Welcome to UF :-)
Have you tried to reboot without the flash drive since the kernel panic? What happens?

---

### Post by johnsg on 2011-10-05
When I reboot, there was a message that one of the disks needs to be checked for consistency, and then CHKDSK ran. After that, Windows started normally.

Looking at this page [https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)
it seems that maybe I need to reduce the Windows partition within Windows, and then try installing Ubuntu?

---

### Post by Quackers on 2011-10-05
Definitely, in my experience.
It's quite lucky that the chkdsk seems to have corrected everything.

Later versions of Windows frequently baulk when their partitions are altered by anything other than Windows Disk Management console. 

It is highly recommended that you defragment the C: drive first, at least once.

You can then shrink the C: drive in Windows Disk Management. It only takes a few seconds. The resulting "unallocated space" can then be used by Ubuntu.

---

### Post by Mark Phelps on 2011-10-05
Word of advice in advance ... if you decide to go dual-boot (with Ubuntu in its own partition) and your PC is running Vista or Win7, do NOT use the Ubuntu installer, or any Linux utility, to shrink the Windows OS partition to make room for Ubuntu.  Vista and Win7 OS partitions are especially touchy and shrinking them with Linux utilities can lead to filesystem corruption -- rendering them unbootable.

Instead, use the Windows Disk Management utility to do the shrinkage -- but leave the new unallocated space blank.

Also, if you're running Win7, use the Backup feature to create and burn a Win7 Repair CD.  That will come in very handy later should you need to repair your Win7 boot loader.

---

### Post by johnsg on 2011-10-05
Thanks to all for the advice. Using Disk Manager to defrag and shrink the partition within Windows 7, restarting, and then installing ubuntu worked perfectly.

---

### Post by Mark Phelps on 2011-10-05
Good to hear ... so please mark this thread as SOLVED.  thanks

---

### Post by Quackers on 2011-10-05
Niiiiiiiice  :-)

---

