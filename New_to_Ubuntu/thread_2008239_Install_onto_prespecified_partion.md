---
title: "Install onto prespecified partion"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by den160593 on 2012-06-22
Hi,

I've created a seperate partion for Ubuntu, and I was wondering how can I ensure that Ubuntu installs itself only on that partition?

I have the CD and tried clicking "help me with install" and what it did was extract to some place (not sure where). Now when booting I get the option boot into Ubuntu or Windows (however, I'm fairly sure ubuntu isn't installed, as I didn't run any installation or anything, I just followed the initial prompt after running the "Help" cd file, and then I cancelled whatever it was (it displayed some error, so I restarted - which was probably a stupid thing...).

How can I get rid of whatever the "Help me install" via wubi did, and then properly install Ubuntu onto the specific partition i've already created? 

I've looked for guides, but can't find anything :(

Thanks so much for your help!

**EDIT: I've managed to get rid of the wubi inside windows, so I no longer have the option to boot into either ubuntu or windows, however I'm still stuck on install all of Ubuntu only onto that premade partition. Thanks again  for help!**

---

### Post by chamber on 2012-06-22
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Follow the advice for Installing alongside windows.

---

### Post by oldfred on 2012-06-22
If it is unallocated space then you use install along side Windows. But if you have created a partition then you want to use Something Else and choose that partition as the location to install. You then also have to specify format as ext4 and / (root) as partition. You also should have another partition for swap. Either the same size as RAM if you may hibernate or 2GB if you have lots of RAM (4GB or more) as you may not use swap much at all.

---

### Post by den160593 on 2012-06-22
Hi, thanks for responses!

I had a look at the link, but it doesn't tell how to do it onto a specific partition.

So I have an unallocated space (I set up a 40gig partition via windows). So to install into this can I use:

1) Install Ubuntu side-by-side with Windows 7
2) Use advanced partitioning tool
3) Select the 40gig partition. Click on Add (or is it Change?). Then make it 38gig size primary, format as Ext4 and / as partition.
4) Use 2gig, set it as primary and use it as 'swap area'?

Is that all? Do I need a /boot

Thanks!!

---

### Post by oldfred on 2012-06-22
Most desktops do not need /boot nor any other system partitions separate. That is more for servers with RAID or LVM and not always required then. Some very old BIOS only boot from first 137GB and those may need a separate /boot or all of / (root) inside the 137GB and then separate /home or data partition(s) for the rest of the drive.

Install screens have not changed hardly at all.
Install 11.04- side by side auto install
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 


Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by den160593 on 2012-06-23
Thanks for response!

Just to confirm, as I'm not building a server, I can just set the one partition as "/" and set it to Ext4. No need for swap (I have 4gig ram) and no need for a /home as I'm not fussed about having a seperate personal directory and no need for /boot?

Thanks!

---

### Post by oldfred on 2012-06-24
That will work, some suggest a minimal swap but others say not required. It depends on whether you load lots of apps at once or just a few as your normal work routine.

---

### Post by den160593 on 2012-06-24
Hi, thanks again for your help!

I installed it onto that partition with no /swap and no /boot 

It said that the installation was a success, however when booting I have no option to boot into Ubuntu, how can I do this? The partition onto which ubuntu is installed is now hidden from windows

---

### Post by black veils on 2012-06-24
try this [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

scroll down to "2nd option: install boot repair in ubuntu"

use your ubuntu live cd/usb (try ubuntu) and install boot-repair.

---

### Post by oldfred on 2012-06-24
Boot-Report solves many issues.

You may just need to run this from Ubuntu.

sudo update-grub

Windows will not see the Linux formated partitions, Ubuntu will let you read and write from NTFS partitions. But it usually is best to set the Windows system partition as read-only to prevent accidental damage. Ubuntu's NTFS driver shows all files & folders where Windows hides  many to prevent problems. 

If you want you can create a shared NTFS partition for any data you may want to share. I have all photos in a shared NTFS partition and use Picasa in both XP and Ubuntu. I also have both Firefox & Thunderbird profiles in the shared so they have all the same data. But I now do not use XP hardly at all.

---

### Post by den160593 on 2012-06-25
Boot repair worked, thanks!!!

---

