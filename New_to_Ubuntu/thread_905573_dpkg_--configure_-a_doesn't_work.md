---
title: "dpkg --configure -a doesn't work"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by lizhood on 2008-08-30
Synaptic is not working for me today for some reason, so I searched this forum and found that I should type "sudo dpkg --configure -a" in a terminal window.

This was what I got as a result:

[INDENT]Setting up libc6 (2.7-10ubuntu3) ...
lconvconfig: cannot generate output file: No space left on device

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: Writing of cache data failed: No space left on device
dpkg: subprocess post-installation script returned error exit status 1[/INDENT]

Can you help me? I'm using a 2goPC with edubuntu installed.

Thanks in advance - Liz :confused:

---

### Post by Bachstelze on 2008-08-30
> **lizhood said:**
> 
/sbin/ldconfig.real: Writing of cache data failed: **No space left on device**

You'll have to do some cleaning ;)

---

### Post by lizhood on 2008-08-30
I should have mentioned that I have 35.2GB space available on the disc.

Liz

---

### Post by drs305 on 2008-08-30
> **lizhood said:**
> I should have mentioned that I have 35.2GB space available on the disc.

Liz

There are reasons you may not have any space - one of the most common is large files residing in trash bins. That space isn't usable until the trash - ALL the trash in ALL the bins - is emptied. Another is having a very small /boot partition.

I've just written a tutorial in the Tips forum. You can access it via the link in my signature line or click on: [http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by lizhood on 2008-08-30
Thanks - I emptied the trash as you suggested, and rebooted the computer. I am still not able to run the dpkg configure successfully. I get the same error message as above. 

Any other suggestions?

Liz

---

### Post by drs305 on 2008-08-30
You can run the following command to check your disk space:
```
df -Th
```

If your trash isn't taking up the space you have some other files filling up your system. The command will show if the partitions are full or not.

---

### Post by lizhood on 2008-08-30
I tried that and got this message:

df: cannot read table of mounted file systems: No such file or directory 

Liz

---

### Post by drs305 on 2008-08-30
You file system must have become corrupted during the attempted install. Even a full disk shouldn't produce that message. My suggestion would be to boot back into recovery mode.

One of the options there is: dpkg - Repair broken packages. I believe it is actually designed more for major upgrades, but I would run that. These are the commands it will run. If you want to try to run them from your current session you can try, but precede the commands with "sudo". Here are the commands it will run. Read this entire post before running ALL these commands:

```

rm /var/lib/apt/lists/partial/* 
dpkg --configure -a 
apt-get update 
apt-get install -f 
*apt-get dist-upgrade*

```

You normally wouldn't run the last command. If you are running the latest version of edbuntu it won't hurt anything. But if you are running an earlier version (not hardy or it's equivalent) I would run the commands manually and NOT run the last one. It would upgrade you to hardy.

After you have selected the "dpkg" option of the recovery mode and it returns to the command prompt, you might consider selecting "root" and going to the command line. There you can run:
```

apt-get clean

```
which will remove downloaded packages from /var/cache/apt and perhaps free up some space.

Again, use "sudo" if not using the recovery mode.

---

### Post by lizhood on 2008-09-01
I tried all that, and it didn't work either - there is no /var/lib/apt/lists/partial/* directory.

Anything else to recommend?

Thanks for all your help!

---

### Post by xeth_delta on 2008-09-01
Please post the output of
```

sudo fdisk -l
df -h

```

---

### Post by Ryadt on 2008-09-01
If you got more than 1 kernel, try removing the ones you are not using.
You could look for them under linux-image in synaptic.

---

### Post by lizhood on 2008-09-01
> **xeth_delta said:**
> Please post the output of
```

sudo fdisk -l
df -h

```

fdisk: invalid option -- 1

Usage: fdisk [-b ssz] [ -u] DISK      Change Partition table
       fdisk -1 [-b ssz] [-u] DISK    List partition table(s)
       fdisk -s PARTITION             Give partition size(s) in blocks 
       fdisk -v                       Give fdisk version
Here DISK is something liks /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by xeth_delta on 2008-09-01
> **lizhood said:**
> fdisk: invalid option -- 1

Usage: fdisk [-b ssz] [ -u] DISK      Change Partition table
       fdisk -1 [-b ssz] [-u] DISK    List partition table(s)
       fdisk -s PARTITION             Give partition size(s) in blocks 
       fdisk -v                       Give fdisk version
Here DISK is something liks /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

It is "fdisk -l" with "l" as in "L", not one. Yeah, they look pretty close, though. :)

---

### Post by lizhood on 2008-09-01
Okay - duh!

Here it is:

Disk /dev/sda: 40.0 GB, 40000536576 bytes
255 heads, 63 sectors/track, 4863 cylinders
Unites = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6328acbl

Device Boot |   Start |   End  |   Blocks  | Id   | System
/dev/sda1   |      1  |    104 |   835348+ |  83  |  Linux
/dev/sda2   |     105 |    148 |   353430  |  83  |  Linux
/dev/sda3   |     149 |    198 |   401625  |  83  |  Linux
/dev/sda4   |     199 |   4863 |  37471612+|  83  |  Linux

I'm sorry I don't know how to make a table so that the columns line up properly - I've put | between the columns to help.

---

### Post by xeth_delta on 2008-09-01
> **lizhood said:**
> Okay - duh!

Here it is:

Disk /dev/sda: 40.0 GB, 40000536576 bytes
255 heads, 63 sectors/track, 4863 cylinders
Unites = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6328acbl

Device Boot |   Start |   End  |   Blocks  | Id   | System
/dev/sda1   |      1  |    104 |   835348+ |  83  |  Linux
/dev/sda2   |     105 |    148 |   353430  |  83  |  Linux
/dev/sda3   |     149 |    198 |   401625  |  83  |  Linux
/dev/sda4   |     199 |   4863 |  37471612+|  83  |  Linux

I'm sorry I don't know how to make a table so that the columns line up properly - I've put | between the columns to help.

You can put the output between code tags, in the posting page, just above, press the # button.

Ok, back on-topic. The partition table seems to be readable by fdisk. I am surprised df does not work.

We will need more information, just have patiencem it will get solved. Please post the output of
```
sudo mount
```
to check the mount points, and
```
parted /dev/sda print
```
for a more detailed view of the partition table.

---

### Post by lizhood on 2008-09-01
> **xeth_delta said:**
> You can put the output between code tags, in the posting page, just above, press the # button.

Ok, back on-topic. The partition table seems to be readable by fdisk. I am surprised df does not work.

We will need more information, just have patiencem it will get solved. Please post the output of
```
sudo mount
```
to check the mount points, and
```
parted /dev/sda print
```
for a more detailed view of the partition table.

"sudo mount" (minus the quotation marks, of course) brought up nothing.

"sudo mount parted /dev/sda/print" brought up usage and help information (which I will type out for you if you need it). At any rate, nothing useful happened.

Isn't this amusing?

Liz

---

### Post by xeth_delta on 2008-09-01
> **lizhood said:**
> "sudo mount" (minus the quotation marks, of course) brought up nothing.

"sudo mount parted /dev/sda/print" brought up usage and help information (which I will type out for you if you need it). At any rate, nothing useful happened.

Isn't this amusing?

Liz

mount and parted are to different commands, to be used separately. Just run each line at a time, don't mix them.

---

### Post by bumanie on 2008-09-01
You can copy and paste answeres into the text box and wrap them in their own box by highlighting the text and clicking on the little yellow box on the bar above between the 'insert image' and the '#' items. Also post the output of > df -h / You have 4 partitions, depending on how your system is set up it could be that / is full but there is room on other partitions. sudo fdisk -l is difficult to interpret as you have typed it rather than cutting and pasting the exact output.

---

### Post by lizhood on 2008-09-01
"sudo mount" has no output.

"sudo parted/dev/sda/print" brings up:

[INDENT]Error: Could not stat device /dev/sda/print - Not a directory[/INDENT]

"sudo def -h /" brings up:

[INDENT]df: Warning: cannot read table of mounted file systems: No such file or directory

Filesystem   Size | Used | Avail Use% | Mounted on
335M | 335M |  2.0 | 100% | /[/INDENT]

(By the way, I can't use the 2goPC to get on the Internet - another problem - so I'm using two computers today :( )

---

### Post by Lutin on 2008-09-01
I think xeth_delta was wanting you to run the command -

parted /dev/sda print    ----- Note space between **sda** and **print**

and not

parted /dev/sda/print


You should only have two back slash characters ("/") and not three as you seem to have.

The error regarding the lack of a "print" sub-directory is correct, as you are trying to get information on a directory that does not exist - ie the /print sub-directory.

---

### Post by xeth_delta on 2008-09-01
> **Lutin said:**
> I think xeth_delta was wanting you to run the command -

parted /dev/sda print    ----- Note space between **sda** and **print**

and not

parted /dev/sda/print


You should only have two back slash characters ("/") and not three as you seem to have.

The error regarding the lack of a "print" sub-directory is correct, as you are trying to get information on a directory that does not exist - ie the /print sub-directory.

exactly. Thanks for explaining that.

---

### Post by philinux on 2008-09-01
just run, no sudo needed.

```
df -h  /
```

---

### Post by lizhood on 2008-09-01
After I put in the correct command, here's what I get:

Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  |  Start  |  End   |  Size  |  Type   | File system |Flags
1       |  32.3kB |  855MB | 855MB  | primary | ext3
2       |  855MB  | 1217MB | 362MB  | primary | ext3
3       | 1217MB  | 1629MB | 411MB  | primary | ext3
4       | 1629MB  | 40.0GB | 38.4GB | primary | ext3

Information: Don't forget to update /etc/fstab, if necessary.

---

### Post by xeth_delta on 2008-09-01
> **lizhood said:**
> After I put in the correct command, here's what I get:

Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  |  Start  |  End   |  Size  |  Type   | File system |Flags
1       |  32.3kB |  855MB | 855MB  | primary | ext3
2       |  855MB  | 1217MB | 362MB  | primary | ext3
3       | 1217MB  | 1629MB | 411MB  | primary | ext3
4       | 1629MB  | 40.0GB | 38.4GB | primary | ext3

Information: Don't forget to update /etc/fstab, if necessary.

From this I can deduce that the partition table is actually ok. What was the last thing you did before this happened?

Please post the contents of /etc/fstab
You can open that file with:
```
sudo gedit /etc/fstab
```

Please be careful not to change anything in it, for now.

---

### Post by drs305 on 2008-09-01
Might as well jump back into this 'mess'... ;-)

You also said you got no results with "sudo mount". Try running:
```
sudo mount -a
```
which will try to mount any drives listed in fstab and then run this again:
```
mount
```

---

### Post by lizhood on 2008-09-01
I'm not sure what I did - I was trying to use Synaptic to load Thunderbird, but I may have inadvertently marked one or more other things to load. The system locked up; I rebooted. Then the machine told me to run dpkg --configure -a, and all my troubles began.

The output of "gedit /etc/fstab" is:

# This file was put in place by the classmate installer
unionfs / unionfs rw 0 0
UUID+980889dd-14fc-raf5-bf45-2dbb60378d32 /boot ext3 noatime,commit=120,defaults 0 0
UUID+d9740df2-6b4f-4ddl-9cf4-bc7d0cab320a /live/cow ext3 noauto,noatime,commit=120,defaults 0 0
UUID=72ca459a-bb7a-4all-ab2b-79e37e416c45 /var ext3 noatime,commit=120,defaults 0 0

UUID=2bfc5306-a0e0-4e50-b32b-3e66fe6adc97 /home ext3 noatime,commit=120,defaults 0 2

---

### Post by lizhood on 2008-09-01
In the above post, I mistyped UUID= twice (putting the plus sign in instead of the equals sign). Should have previewed. Sorry!

---

### Post by philinux on 2008-09-01
Just run, no sudo needed.

```
df -h  /
```My output shows this, if yours shows 100% use then thats your problem.


```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  3.8G  6.9G  36% /

```

---

### Post by lizhood on 2008-09-01
Here's the output of "df -h /":

df: Warning: cannot read table of mounted file systems: No such file or directory

Filesystem

Size   |   Used |  Avail  | Use%  | Mounted on
335M   |   335M |    0    | 100%  | /


So obviously I have a problem, but I don't know how to fix it :(

---

### Post by philinux on 2008-09-01
Use 

System>admin>system monitor.

click the file system tab , click the print screen button and post the result.

Here's mine.

---

### Post by lizhood on 2008-09-01
Hi - unfortunately I can't give you a screenshot, because I can't use the internet on the machine with the problem.  However, I opened the System Monitor, clicked on File Systems, and it's empty.

---

### Post by bumanie on 2008-09-01
Looks as though the / partition is full - it is at 100%, that is why nothing will work properly, that is why you cannot install anything. You somehow made a / of only 335mb according to your output. You need to increase the size of /. Not sure how it is 335mb, would not have thought it was possible to install into that small space, anything something has changed re partition sizes since you did install. At this point, I would try to save anything that is important and reinstall, as a 335mb / partition is never going to work and trying to extend it without destroying other things may be difficult, as you can't even install anything to help you. If you can download and burn a gparted live cd, post a screen shot of your partitions and someone will see if they help work out whether your drive can be repartitioned successfully, but I have my doubts.

---

### Post by lizhood on 2008-09-01
I was afraid of that - but okay. On to a new adventure - reinstalling. Luckily there's nothing on the machine that I can't do without. Haven't had it long enough to put much on - just long enough to make a mess!

Thank you so for all your help.

Liz

---

### Post by xeth_delta on 2008-09-01
> **lizhood said:**
> I'm not sure what I did - I was trying to use Synaptic to load Thunderbird, but I may have inadvertently marked one or more other things to load. The system locked up; I rebooted. Then the machine told me to run dpkg --configure -a, and all my troubles began.

The output of "gedit /etc/fstab" is:

# This file was put in place by the classmate installer
unionfs / unionfs rw 0 0
UUID+980889dd-14fc-raf5-bf45-2dbb60378d32 /boot ext3 noatime,commit=120,defaults 0 0
UUID+d9740df2-6b4f-4ddl-9cf4-bc7d0cab320a /live/cow ext3 noauto,noatime,commit=120,defaults 0 0
UUID=72ca459a-bb7a-4all-ab2b-79e37e416c45 /var ext3 noatime,commit=120,defaults 0 0

UUID=2bfc5306-a0e0-4e50-b32b-3e66fe6adc97 /home ext3 noatime,commit=120,defaults 0 2

The file /etc/fstab seems a bit strange to me, to be more precise the line with the / partition. What kind of setup do you have? Is it a system in a network, perhaps in a school/university?

Also, there is no precise device specified for / via UUID or the regular /dev device file.
Anyone else has seen or used that file system before, unionfs?

I believe this might be related to your problem. Please run the following commands, one by one and post the output, maybe there is a back-up for the file:
```
cd /etc/
```
```
find * | grep -i fst
```

---

### Post by Flying caveman on 2009-02-13
I bought a 2gopc a few days ago.  I was having the same problems and after reading this thread I decided to do a clean install of Ubuntu 8.04.  I used Unetbootin to make a bootable flash drive.

I'm much happier now. I was also having system hangs too, I commented out (put a # before) the p-4 clockmod in /etc/modules and have been fine since. 

Oh, and don't change the bios setting quiet boot or you will need a usb keyboard to get back into the Bios set-up. 

I know this doesn't solve the problem, but it may come in handy for other 2gopc users.

there are lots of tweaks you can do to the desktop to make the most of the small screen too.

---

