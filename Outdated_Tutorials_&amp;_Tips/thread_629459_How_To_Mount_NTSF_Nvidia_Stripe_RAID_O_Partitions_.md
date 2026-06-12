---
title: "How To Mount NTSF Nvidia Stripe RAID O Partitions In Ubuntu Linux"
date: 2007-12-02
forum: Outdated Tutorials &amp; Tips
---

### Post by aikiwolfie on 2007-12-02
Disclaimer: These are the commands I used. They may or may not work for you. If you kill or damage your PC you are to blame. You follow this tutorial at your own discretion. 

[list=1]
[*]**What You Need**
[list]
[*]dmraid. The Linux tool for accessing fakeRaid arrays like nividia stripe.


[*]NTFS Configuration Tool. Gives you the NTFS-3g driver needed for full read/write access to NTFS partitions.


[*]A mount point for your NTFS partition.


[*]Root access to the system.
[/list]


[*]**Install dmraid**
[list]
[*]System > Administration > Synaptic Package Manager.


[*]Do a search for "dmraid". There should be only one result. The package title will be "dmraid".


[*]Select dmraid for installation and click "Apply".


[*]Close Synaptic when finished. dmraid is now installed.
[/list]


[*]**Install NTFS Configuration Tool**
[list]
[*]Applications > Add/Remove...


[*]Do a search for "NTFS Configuration Tool". There should only be one result called "NTFS Configuration Tool".


[*]Select this for installation and click "Apply".


[*]Close when finished. NTFS Configuration Tool is now installed.
[/list]


[*]**Create A Mount Point For Your NTFS Partition.**
[list]
[*]Open a terminal window.
Applications > Accessories > Terminal


[*]Enter the following command.
[FONT="System"]*sudo mkdir /media/ntfs*[/FONT]


[*]Enter your root password if/when prompted.


[*]Your mount point has now been created.
[/list]


[*]**Enable Your RAID Setup.**
[list]
[*]In the terminal window enter the following command.
*[FONT="System"]sudo dmraid -ay[/FONT]*


[*]If nothing seems to happen it's worked. If the arrays are already active you'll get output something like this.

[I][FONT="System"]RAID set "nvidia_ehiaffhc" already active
RAID set "nvidia_caacdjfa" already active
RAID set "nvidia_ehiaffhc1" already active
RAID set "nvidia_ehiaffhc2" already active
RAID set "nvidia_ehiaffhc3" already active
RAID set "nvidia_caacdjfa1" already active
[/FONT][/I]
This is normal and nothing to worry about. Anything else and you should stop and reconsider going any further. Note I have two raid 0 arrays. One with three partitions and one with one partition. Hence the output list.
[/list]


[*]**Figure Out Where Your NTFS Partition Is**
[list]
[*]If nothing happened in the previous step enter the command again.
*[FONT="System"]sudo dmraid -ay[/FONT]*


[*]This will give you output similar to the following.

[I][FONT="System"]RAID set "nvidia_ehiaffhc" already active
RAID set "nvidia_caacdjfa" already active
RAID set "nvidia_ehiaffhc1" already active
RAID set "nvidia_ehiaffhc2" already active
RAID set "nvidia_ehiaffhc3" already active
RAID set "nvidia_caacdjfa1" already active[/FONT][/I]


[*]As I have two raid 0 arrays, one with three partitions and one with 1 partiton I get 6 entries in the list.


[list]
[*]The top two entries are the stripe arrays (so far as I can figure out). Feel free to ignore these. You can only mount individual partitions.


[*]The next three entries are partitions on the first array. If your faced with something like this, a little trial and error will be needed to determine which partition is the NTFS partition.

This should not harm your system or the disc. But be careful. If you're not sure get a better opinion.


[*]The last entry is the partition on the second array. This is the one I will use since I know it is definitely an NTFS partition. I know this because I have two raid 0 arrays. The second array contains only one partition which is NTFS.
[/list]


[*]We can test this theory with the following command. Note this command will mount the NTFS partition as "read only". So we shouldn't harm it. Use this command for your trial and error search if you need to.
[FONT="System"]*sudo mount /dev/mapper/nvidia_caacdjfa1 /media/ntfs/ -t ntfs -o nls-utf8,umask=0222*[/FONT]


[*]If the mount attempt has worked an icon for "ntfs" should appear on the desktop and in the Places menu. Click on these to view to contents of ntfs and verify it's the correct partition.


[*]Next unmount the partition with the following command.
*[FONT="System"]sudo umount /media/ntfs[/FONT]*


[*]If thiss has worked the ntfs icons will now be removed from the desktop and the Places menu.
[/list]


[*]**Create a shell script to mount the partition.**
[list]
[*]Right Click on the desktop > Create Document > Empty File.


[*]Give the document a name. I used mount_ntfs. Do not use spaces.


[*]Open the document you've just created. Double left click.


[*]Now enter the following line.
[FONT="System"]*sudo mount /dev/mapper/nvidia_caacdjfa1 /media/ntfs/ -t ntfs-3g -o rw,uid=1000,gid=100,umask=0022*[/FONT]


[*]Save and close.


[*]Now give the script run permissions.


[list]
[*]From the desktop right click on the script file > select properties.
This will bring up the script files properties.


[*]Click Permissions > Execute > Close.


[*]Now test the file. Double left click and select "Run In Terminal" when prompted. If it has worked an icon for ntfs will be on the desktop and in the Places menu. Click on these to verify they work.
[/list]
[/list]


[*]**Create a shell script to unmount the NTFS partition.**
[list]
[*]Create shell script as before. Substitute the command for the following.
*[FONT="System"]sudo umount /media/ntfs[/FONT]*
[/list]
[/list]

---

### Post by Wayno-san on 2007-12-14
Thanks for the excellent guide.  I have a question... when, during boot-up, is dmraid actually called?  I have a RAID0 (set2) stripe composed of HD SATA3&4 with two other drives (non-RAID) on SATA1&2 (set1).  I added a NTFS partition on the RAID0 stripe to my fstab file and it mounts it fine, however I noticed that the first RAID set (SATA1&2) is also turning on and preventing the mounting of partitions on drives SATA1 & 2 (since they are already "in-use" by dmraid).  I don't know if that makes sense but the gist of it is, is that I need to make sure that dmraid only activates set2 on boot-up or I cannot mount any partitions located on SATA 1 & SATA 2 drives.  Suggestions?

---

### Post by Xtremist on 2008-02-02
great post.

how can u make this mount automatically ? 

I mean, let's say you install ubuntu on a flash usb, you carry it and plug into a friends computer, how can u make it automatically mount ntfs volumes at start? (even automatically detect file type, ntfs fat32 etc)

thanx

---

### Post by djbon2112 on 2008-02-18
HELP! I followed your guide with my SATA RAID, but this is what I get:

```
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "isw_digcfadfge_Warsaw RAID" already active

ubuntu@ubuntu:~$ sudo mount '/dev/mapper/isw_digcfadfge_Warsaw RAID'  /media/ntfs/ -t ntfs -o nls-utf8,umask=0222
NTFS signature is missing.
Failed to mount '/dev/mapper/isw_digcfadfge_Warsaw RAID': Invalid argument
The device '/dev/mapper/isw_digcfadfge_Warsaw RAID' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

It shows up in Computer, but double clicking gives me this:

```
Cannot mount volume.

Unable to mount the volume.

$MFT has invalid magic. Failed to load $MFT: Input/outpt error Failed to mount '/dev/sdd1': Input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware ... If you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper directory. Please see the 'dmraid' documentation for the details.
```

I've got no idea what this is talking about, and the "dmraid documentation" is not helping at all! I've been googling and googling and nothing seems to be helping! Anyone have any suggestions?

---

### Post by GamerX on 2008-03-02
Same problem here... Trying to mount ICH7R RAID 0 volume I get:

root@gamerx-desktop:/dev/mapper# dmraid -ay
ERROR: pdc: seeking device "/dev/sdb" to 18446744073709502976
ERROR: pdc: seeking device "/dev/sdb" to 18446744073709533696
ERROR: pdc: seeking device "/dev/sdb" to 18446744073709371904
ERROR: pdc: seeking device "/dev/sdb" to 18446744073709412864
ERROR: sil: seeking device "/dev/sdb" to 18446744073709354496
RAID set "isw_ehjfeedia_GMX 2 (Raid 0)" already active
root@gamerx-desktop:/dev/mapper# mount "/dev/mapper/isw_ehjfeedia_GMX 2 (Raid 0)" /HD -t ntfs -o nls-utf8,umask=0222
**NTFS signature is missing.**
Failed to mount '/dev/mapper/isw_ehjfeedia_GMX 2 (Raid 0)': Invalid argument
The device '/dev/mapper/isw_ehjfeedia_GMX 2 (Raid 0)' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

---

### Post by Spotta on 2008-03-04
Hi

i also wanted to try this, but i'm not so sure after reading the last 2 posts.
i have nvidia stripe with XP and vistax64 on. I tried to install ubuntu to it but it would not see it.
Funily enough I had problems with the install and downloaded a live cd of Knoppix - this could access all my NTFS partitions on the nvidia stripe fine (although it didn't see any non raid sata drives!)

i'm quite new to Linux so don't shout at me if this is a silly idea- but would it be possible to find out what allows access to nvidia stripe on knoppix and install it to ubuntu?

Spotta

---

### Post by jharkn on 2008-04-16
Cheers aikiwolfie, worked a treat!

---

### Post by jrnt30 on 2008-05-22
Excellent post.  I was a bit hesitant to try this on my own after doing some research.  

However the detailed step-by-step instructions that spelled out what was going on gave me that "warm fuzzy" and I gave it a shot.  Worked without a hitch with my RAID 1 setup.

Thanks again for the great contribution.

Justin N.
Chicago, IL

---

### Post by PhireBird on 2008-06-02
I noticed you used the 'mount' function. I did the same thing myself and it somehow kept coming with errors.
> **GamerX said:**
> Same problem here... Trying to mount ICH7R RAID 0 volume I get:

root@gamerx-desktop:/dev/mapper# dmraid -ay
ERROR: pdc: seeking device "/dev/sdb" to 18446744073709502976
ERROR: pdc: seeking device "/dev/sdb" to 18446744073709533696
ERROR: pdc: seeking device "/dev/sdb" to 18446744073709371904
ERROR: pdc: seeking device "/dev/sdb" to 18446744073709412864
ERROR: sil: seeking device "/dev/sdb" to 18446744073709354496
RAID set "isw_ehjfeedia_GMX 2 (Raid 0)" already active

root@gamerx-desktop:/dev/mapper# mount "/dev/mapper/isw_ehjfeedia_GMX 2 (Raid 0)" /HD -t ntfs -o nls-utf8,umask=0222
**NTFS signature is missing.**
Failed to mount '/dev/mapper/isw_ehjfeedia_GMX 2 (Raid 0)': Invalid argument
The device '/dev/mapper/isw_ehjfeedia_GMX 2 (Raid 0)' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

The way I did it for myself was in console:

ntfs-3g "/dev/mapper/isw_fbjafagbe_big1891" "/mnt/ntfs" -o rw,nls-utf8,umask=0222

The above command applied to the partition on my raid array (the array was called isw_fbjafagbe_big189, the partition on the array was just 1 appended to that). ISW was the name of the type of software raid, Intel. I Set it to read and write mode but if your worried always try read only.

Your dmraid -ay command only showed up one raid array, and not even the partition. maybe this /dev/sdb device is a faulty hard drive? If not i have the commands for read only and read/write written up for you to paste into your konsole:

Read Only (try first):
ntfs-3g "/dev/mapper/isw_ehjfeedia_GMX 2 (Raid 0)" "/HD" -o ,nls-utf8,umask=0222

Force Read Only
ntfs-3g "/dev/mapper/isw_ehjfeedia_GMX 2 (Raid 0)" "/HD" -o force,nls-utf8,umask=0222

Also note, you should double check the actual filenames in the /dev/mapper/ directoy, something like:
cd /dev/mapper/
ls
You might come up with the partition label for your raid, never know (would be as simple as "/dev/mapper/isw_ehjfeedia_GMX 2 (Raid 0)1" - your raid device label with a '1' suffix or another number denoting the partition)

Check the Mount Directoy
cd /HD

If the mount directory isn't available, remake it:
mkdir /HD

or relocate it:

mkdir /dev/HD    <<Ubuntu

OR

mkdir /mnt/HD    <<Slackware


Read/Write (try last):
ntfs-3g "/dev/mapper/isw_ehjfeedia_GMX 2 (Raid 0)" "/HD" -o rw,nls-utf8,umask=0222

Force Read/Write
ntfs-3g "/dev/mapper/isw_ehjfeedia_GMX 2 (Raid 0)" "/HD" -o rw,force,nls-utf8,umask=0222

Truly, I would only ever see a reason to use the "force" option on a "Read Only" ntfs device, and even less on a RAID NTFS device, as that command allows the mounting of a device which is scheduled for a check up by windows, hinting that there might be errors in the file system. If your sure about the force option for "read-write" then go ahead and use it, but try the standard one first to see if you do have any errors.
Hope it helps buddy, got my raid setup in 30 mins on a Copy2ram version of Slackware 2.6 (copied from usb>ram) with the dmraid driver downloaded + installed + configured on the fly (ntfs-3g pre-installed)

---

### Post by aikiwolfie on 2009-02-11
Wow! I didn't know anybody was reading this. Forgot to subscribe to my own thread. DOH! Anyway if anybody is still having problems let me know and I'll try and help. :)

---

### Post by keeperlink on 2009-03-07
I have a problem mounting NTFS on one of two Nvidia's RAID0s. I have two RAID arrays - one with two 750GB disks and one with three 750GB disks. NTFS on first RAID array was mounted correctly and I was able to read it using the very helpful instruction above. Second one (the one with 3 disks) have problem (though both arrays are working in Vista)

# dmraid -ay
ERROR: sil: only 1/4 metadata areas found on /dev/sde, picking...
/dev/sde: "sil" and "nvidia" formats discovered (using nvidia)!
ERROR: sil: only 1/4 metadata areas found on /dev/sdd, picking...
/dev/sdd: "sil" and "nvidia" formats discovered (using nvidia)!
ERROR: sil: only 1/4 metadata areas found on /dev/sdc, picking...
/dev/sdc: "sil" and "nvidia" formats discovered (using nvidia)!
RAID set "nvidia_cbeifded" already active
RAID set "nvidia_cbccbbdd" already active
RAID set "nvidia_cbccbbdd1" already active

# dmraid -r
ERROR: sil: only 1/4 metadata areas found on /dev/sde, picking...
/dev/sde: "sil" and "nvidia" formats discovered (using nvidia)!
ERROR: sil: only 1/4 metadata areas found on /dev/sdd, picking...
/dev/sdd: "sil" and "nvidia" formats discovered (using nvidia)!
ERROR: sil: only 1/4 metadata areas found on /dev/sdc, picking...
/dev/sdc: "sil" and "nvidia" formats discovered (using nvidia)!
/dev/sde: nvidia, "nvidia_cbeifded", stripe, ok, 1465149166 sectors, data@ 0
/dev/sdd: nvidia, "nvidia_cbeifded", stripe, ok, 1465149166 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_cbeifded", stripe, ok, 1465149166 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_cbccbbdd", stripe, ok, 1465149166 sectors, data@ 0
/dev/sda: nvidia, "nvidia_cbccbbdd", stripe, ok, 1465149166 sectors, data@ 0

Please help

Thank you

---

### Post by aikiwolfie on 2009-03-08
Try erasing the meta data with the -E switch. This worked for me after I had to rescue my raid partitions after a system board upgrade. Afterwards the raid array worked fine in both Windows XP and Ubuntu.

The command I used was:
```
sudo dmraid -rE [insert raid device eg: /dev/sdb]
```

---

### Post by keeperlink on 2009-03-09
> **aikiwolfie said:**
> Try erasing the meta data with the -E switch. This worked for me after I had to rescue my raid partitions after a system board upgrade. Afterwards the raid array worked fine in both Windows XP and Ubuntu.

The command I used was:
```
sudo dmraid -rE [insert raid device eg: /dev/sdb]
```

Thanks for the reply. I want to try that. But is it safe? I don't want to destroy array that is functional under Vista
How to reverse it in case of failure? 
As I understand I have to run following commands:
sudo dmraid -rE /dev/sdc
sudo dmraid -rE /dev/sdd
sudo dmraid -rE /dev/sde
Is it correct?
Than what should I do next? Repeat steps in the article? 
Sorry for so many questions. I'm new in Linux and RAID worlds. Thanks.

---

### Post by MattyDread on 2009-03-18
Hi, I'm trying this as I have data on a raid stripe I need to recover. When I try to enable the raid setup, I get this:

RAID set "nvidia_jbdffcde" was not activated

I'm using Ubuntu 8.10 and am very new to this. Any help would be much appreciated!

Cheers

---

### Post by giyad on 2009-11-09
> **aikiwolfie said:**
> Wow! I didn't know anybody was reading this. Forgot to subscribe to my own thread. DOH! Anyway if anybody is still having problems let me know and I'll try and help. :)

I'm not sure if you're still subscribed to this thread but I thought you could help me...  I've got a fresh install of Ubuntu 9.04 so I didn't have to install ntfs-3g, and I'm a noob to linux (this is my first install) so keep that in mind ;-)

Ok, so I have a RAID-0 set up via my motherboard (a Nvidia nForce 680i SLI).  Its formatted in Windows (NTFS and GPT partition), and has a lot of data on it.  Everything works great via windows, but I want to be able to share the items over my network when Ubuntu is running as well, so i don't lose anything by running Ubuntu instead of windows.

Anyway, to the problem.

When I run dmraid -ay, I am returned only one result, which is perfect so there isn't any guess and check.  The result is "nvidia_facfcied" and it says exactly what yours say, "already active". But when I run
```
sudo mount /dev/mapper/nvidia_facfcied /media/Z/ -t ntfs -o nls-utf8,umask=0222
```I get:

> NTFS signature is missing.
Failed to mount '/dev/mapper/nvidia_facfcied': Invalid argument
The device '/dev/mapper/nvidia_facfcied' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?What could the problem be?  You can follow my forum post [here]("http://ubuntuforums.org/showthread.php?p=8281203#post8281203") if you like instead... ** Its been SOLVED.**

THANKS!

---

