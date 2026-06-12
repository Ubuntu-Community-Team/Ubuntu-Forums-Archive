---
title: "Help Please Not booting."
date: 2019-01-22
forum: New to Ubuntu
---

### Post by deanoandrew on 2019-01-22
Hi , all i have used Boot Repair from a live USB and get the following output :

[http://paste.ubuntu.com/p/F9dWhqMNSf/](http://paste.ubuntu.com/p/F9dWhqMNSf/)


I have an 80gb drive, with just Ubuntu 18.04.1 Installed ( No Windows ) . I also have a 2TB Storage drive. 

Everything was working fine, no hardware changes or software installs ( other than updates ) and suddenly it would not boot up saying "Error auto sensing secondary slave hard disk drive" 

Bios shows the hard drives and everything looks okay there, i have checked the connections and can feel/hear the drives powering up.  

I am okay with re-installing ubuntu to the 80gb drive, but i was running QBTorrent and although i know it saves the media to the storage drive I am not sure where it saves the Torrent info to and therefore would like to be able to at least view the 80gb drive to copy that data over before wiping it or replacing the drive. 

Any ideas ? I am just a monkey see , monkey do user so can follow step by step instructions but dont really know what i am doing :) 
Any help is greatly appreciated.

---

### Post by oldfred on 2019-01-22
Report shows USB flash drive as sdc, but no mention of either sda or sdb drives?

From live installer and Disks app, in upper right corner is Smart Status. What does that say about drives.
Are both drives internal?

---

### Post by deanoandrew on 2019-01-22
Thanks for the response..
They show in Disks, but the SMART Data & Self Tests option is greyed out and not accessible
i can see the drives and the partitions but it says partition type unknown and contents unknown ..

---

### Post by deanoandrew on 2019-01-22
the 80gb is /dev/sda1  and the 2tb is /dev/loop0 (read only)

---

### Post by oldfred on 2019-01-22
The loop0 is typically what you see if you use dd to install the live installer to a flash drive.
Did you create a flash drive and use sdb. That would overwrite the first two GB of the drive effectively erasing it.

What does this show. If drive is gpt there is a backup partition table at end of drive, so may be recoverable. But if the 35 year old MBR, may be very difficult to restore data.

sudo gdisk -l /dev/sda
sudo gdisk -l /dev/sdb

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)
Screenshots of several of the recovery tools
[URL="http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/"]http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/

      [/URL]
 Testdisk Instructions, new versions use sectors, old ones were CHS
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 
    

I have used Photorec. 
I had smaller drive and it took all night to run. I had to buy another drive of same size (or larger) to have place to write recovered data to.
And it only recovers files by type, or just extension, not file name. If photos you can then use meta-data to name them.
       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) 
    [URL="http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/"]
[/URL]

---

### Post by deanoandrew on 2019-01-23
Okay , thanks very much. i will have a read through the links

---

