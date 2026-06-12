---
title: "Boots into initramfs"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by awmitchell on 2012-02-04
Hi everyone,

I'm a newbie here and don't yet know much about Linux but my son Alex (10) and I have been trying out Ubuntu and have run into a problem. I'm hoping one of you may be able to help.

Background:
- Did first Ubuntu install (64-bit) about a month ago. Its on a older HP workstation (XW4600) which already had a fresh install of XP it
- Choose the option to do Ubuntu install to keep Windows and install Ubuntu and gave Ubuntu about half the disk
- I'm pretty sure the installed version is 11.10
- We've installed Java and have been using the workstation as a local minecraft server
- Most recently we had just got a start up script working to run the minecraft server when the machine boots

Problem:
- We have been using the powerbutton to force shut down because I was too lazy to shut it down properly and that had been working fine until yesterday.
- The machine now boots into initramfs

Diagnostics:
- When I boot using recovery mode the errors relate to being unable to find or mount partitions
- I've got the original LiveCD up now and (based on what I saw in another messaqe in the forum) I ran "sudo fdisk -l"
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd42ad42a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   481946936   240973437    7  HPFS/NTFS/exFAT
/dev/sda2       955771110   976751999    10490445    7  HPFS/NTFS/exFAT
/dev/sda3       481947646   955770879   236911617    5  Extended
/dev/sda5       947417088   955770879     4176896   82  Linux swap / Solaris
/dev/sda6       481947648   939061247   228556800   83  Linux
/dev/sda7       939063296   947400703     4168704   82  Linux swap / Solaris

Partition table entries are not in disk order
- Then I ran fsck on all the partitions
> ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux 2.19.1
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1
ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck from util-linux 2.19.1
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda2
ubuntu@ubuntu:~$ sudo fsck /dev/sda3
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3
Could this be a zero-length partition?
ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck from util-linux 2.19.1
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda5
ubuntu@ubuntu:~$ sudo fsck /dev/sda6
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda6
Could this be a zero-length partition?
ubuntu@ubuntu:~$ sudo fsck /dev/sda7
fsck from util-linux 2.19.1
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda7
- I noted that all the fsck commands got a response quickly but there was a delay of maybe 30 seconds for /dev/sda6

Now I'm totally lost as to next step. I know I can do a reinstall but I want to keep the minecraft data if I can. Is there any hope?

Any advice will be appreciated.

Thanks in advance,

Andrew.

---

### Post by ikt on 2012-02-05
> **awmitchell said:**
> I know I can do a reinstall but I want to keep the minecraft data if I can. Is there any hope?

Assuming the minecraft data is just files you should be able to boot up a live usb and just copy and paste the files onto your usb drive then reinstall ubuntu like normal.

---

### Post by awmitchell on 2012-02-05
> **ikt said:**
> Assuming the minecraft data is just files you should be able to boot up a live usb and just copy and paste the files onto your usb drive then reinstall ubuntu like normal.

Thanks ikt,

It's the game world save file which I really want to recover if I can. It's the result of many hours of creativity from myself and my two kids.

If there's a further avenue of investigation / resolution I could follow that would be great. If there's no hope then I'll go ahead and reinstall.

Thanks,
Andrew.

---

### Post by ikt on 2012-02-06
> **awmitchell said:**
> Thanks ikt,

It's the game world save file which I really want to recover if I can. It's the result of many hours of creativity from myself and my two kids.


Yeah I understand, unfortunately I have no experience with minecraft, worst case scenario you've hit upon 2 big important IT lessons, backing up and not turning linux off at the power switch. :)

There appears to be some help just googling around for some of the error messages you got

[http://ubuntuforums.org/showthread.php?t=1245536](http://ubuntuforums.org/showthread.php?t=1245536)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)

And a backup script:

[http://www.minecraftforum.net/topic/53351-linux-backup-and-minecraft-server-restart-script-for-cron/](http://www.minecraftforum.net/topic/53351-linux-backup-and-minecraft-server-restart-script-for-cron/)

From what I can see it should be recoverable, just depends on how much googling and time you've got compared to the data that's saved. 

Good luck. :)

---

### Post by awmitchell on 2012-02-07
Thanks again ikt. I've looked at those links and I think the cyberciti link looks particularly useful. I will work through that and see if I can find a solution. Thanks also for the backup script - it will come in handy.

Cheers! :-)

---

### Post by Miljet on 2012-02-07
Try booting your live CD and open GParted. Select (Highlight) the partition where Ubuntu is installed. It looks like that is sda6 on your computer. Then select "Check" or "Check Partition." After it runs, close GParted and reboot the computer.

And start shutting the computer down properly.

---

### Post by awmitchell on 2012-02-07
Thanks. I'll try that tonight Miljet. I'll let you know how I go.

And yes, I will stop taking the lazy shutdown option and do it properly from now on.

---

### Post by awmitchell on 2012-02-13
Hey everyone,

I just wanted to let you all know that the problem has been solved and the system is working again. The link ikt provided to
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
was really useful and informative.

Thanks ikt! :-)

Andrew.

P.S. Next step is to set up a backup of the critical files.

---

