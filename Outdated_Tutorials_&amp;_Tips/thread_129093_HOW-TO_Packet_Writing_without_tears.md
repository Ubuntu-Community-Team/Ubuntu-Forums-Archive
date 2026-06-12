---
title: "HOW-TO: Packet Writing without tears"
date: 2006-02-12
forum: Outdated Tutorials &amp; Tips
---

### Post by GTvulse on 2006-02-12
**Packet Writing Without Tears: How to use Rewritable Optical Media in Ubuntu**
*Pedro A. López-Valencia*
*[SIZE="1"]python -c 'print "cGFsb3BlenZAZ21haWwuY29t".decode("base64")'[/SIZE]*

The Linux kernel supports packet writing on read-only and rewritable media since kernel 2.6.8, as was the case in Hoary. Yet I only managed to have it work consistently in Breezy. It took some head scratching, but then it hit like a truck: *You don't need to be a rocket scientist to do it!!!*. But trying to understand how to do it can make a grown man cry.

**What the heck is *Packet Writing*?**

Good question! One of the design goals of the UDF filesystem was to allow incremental data addition to optical media. That is, to be able to *write packets* of data. In essence it allows one to use a CD or a DVD as an oversized floppy disk. In fact, many of you may have used EasyCD, Roxio's Write-On-CD, Nero InCD, or some other commercial product in MS Windows to read and write CDs, particularly CDRWs, this way.

As it is the case with floppy disks, reliability is poor; any glitch and your data is done for. Furthermore many software vendors in the MS Windows world have managed to make their implementations incompatible to each other, to the point that you may not be able to open for writing a disk created with a different utility, and even fail to read it. And they may claim to use the same UDF format version!

In other words, if you think you will be doing your critical data backups with packet writing instead of old-fashioned CD mastering and burning or tape backups or whatnot, you are playing with fire. Now that I've given you dire warnings, let me tell you that packet writing has its uses. It is up to you to take the risk or not.

**The ingredients**

Although the kernel has support for packet writing, you need to install the user space tools to be able to access the kernel services. Enable the universe repositories and:
```
sudo apt-get install udftools
```
Now add the cd writer to the init files:
```
sudo <your_editor> /etc/default/udftools
```
In my particular case I'm using a CD writer in [FONT="Courier"]/dev/hdd[/FONT], thus I edited the file to contain this line:
```
DEVICES="/dev/hdd"
```
Do read the comments in that file but don't bother trying to be creative with the device filenames defined in [FONT="monospace"]NEWINTNAMES[/FONT], else you'll have access permissions trouble later on.

Now, set up your drive:
```
sudo /etc/init.d/udftools start
```

This init script loads the kernel module and sets up the link between the block device ([FONT="monospace"]/dev/hdd[/FONT] in this case) and the virtual packet drive device [FONT="monospace"]/dev/pktcdvd/0[/FONT] (there is only one device defined and it gets the first alllocated name). If you want to know more, I strongly recommend you read the manual pages for [FONT="monospace"]mkudffs[/FONT], [FONT="monospace"]cdrwtool[/FONT] and [FONT="monospace"]pktsetup[/FONT].

**Formatting your CD-RW**

Take a CD-RW or DVD-/+RW and format it:
```
sudo cdrwtool -t 4 -d /dev/hdd -q
```
Go brew a carafe of cofee  and grab some muffins. Drink slowly... There are several options you can set up including the UDF version, you'll find that information in the manual pages. 

[font=monospace]cdrwtool[/font] burns at a speed of 12x by default, yet most CDRWs and DVD-/+RWs, particularly the cheap ones, support slower burning speeds. 4x seems to be a very common maximum speed for rewritable media, so I've put it in the example above. It is always a good idea to define explicitly the max writing speed of your media, or formatting will fail.

Before you start formatting your CD, make sure that you have DMA active in your burner; else you'll get funny formatting errors and failures. By default, Ubuntu's kernels do not activate DMA busmastering on anything different to PATA disks, because older CD readers and burners tend to belly up when you activate DMA in the IDE bus and lock up the system.

In order to activate permanently DMA, you must edit your [font=monospace]/etc/hdparm.conf[/font]. Suppose you have a CD or DVD burner in /dev/hdc then you would add the following lines:
```

/dev/hdc {
    dma = on
    io32_support = 1
}

```

[font=monospace]/etc/hdparm.conf[/font] is read every time your box boots up. If you can't wait, you can activate the settings from the command line too. Open a terminal window and type:
```
sudo hdparm -c1 -d1 /dev/hdc
```

**Mounting your cd**

There is only one thing to consider. You need to use the special packet writing device, not the normal disk device!!! Like this:
```
sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /your/mount/point
```
I've added the utf8 option because that's the default filesystem encoding in Ubuntu, and noatime because that reduces drastically the number of access writes to the disc. This is particularly important if using a DVD-/+RW, because *writable DVDs are programmed to allow 1000 writes, not one more*!!!

**Making the CD/DVD-RW writable by you**

Before you start using your CD-RW, you need to make it writable by other users different to root:
```
sudo chown 777 /your/mount/point/.
```
Note the dot at the end.

**Making a permanent addition to your system**

Now you are ready to set up your system to mount and unmount your CDs without effort. Create an entry in [FONT="monospace"]/media[/FONT]:
```
sudo mkdir -p /media/cdwriter
```
and add the following to [FONT="monospace"]/etc/fstab[/FONT]:
```
/dev/pktcdvd/0  /media/cdwriter  udf  user,noauto,noatime,utf8  0  0
```
You will be able to mount the CD/DVD-RW by double-clicking on an icon in the computer browser, if using Ubuntu. If using KDE, you are on your own. ;-)

---

### Post by Zeroangel on 2006-02-17
I seem to be getting illegal seek errors during formatting.

```
dave@ubuntu:~$ sudo cdrwtool -d /dev/hdc -q
Password:
using device /dev/hdc
672KB internal buffer
setting write speed to 12x
Settings for /dev/hdc:
        Fixed packets, size 32
        Mode-2 disc

I'm going to do a quick setup of /dev/hdc. The disc is going to be blanked and formatted with one big track. All data on the device will be lost!! Press CTRL-C to cancel now.
ENTER to continue.

Initiating quick disc blank
wait_cmd: Input/output error
Command failed: a1 01 00 00 00 00 00 00 00 00 00 00 - sense 05.30.00
blank disc: Illegal seek
dave@ubuntu:~$

```
I'm aware that it may be a firmware problem thats causing this, unfortunately I can't seem to update my firmware in Linux. Is there a workaround I can use to write UDF filesystem to the disk in this application?

mkudffs + dvd+rw-format haven't been working for me.

---

### Post by GTvulse on 2006-02-17
[quote=Zeroangel]
seem to be getting illegal seek errors during formatting.
[/quote]

Yes, that has happened to me as well. That would happen if you don't have DMA active in your CDRW block device. You can use
```
sudo hdparm -d1 /dev/hdc
```
before starting to format your CDRW, and add it to [font=monospace]/etc/hdparm.conf[/font] so it is set up everytime your system boots up.

I forgot to mention it in the howto.

EDIT: Added.

Another thing I missed. cdrwtool defaults to burning to 12x. Most CD-RW and DVD-/+RW disks support slower sppeds and you should use the speed flag explicitly.

---

### Post by dcstar on 2006-02-19
I have my UDF set up in a similar manner to what has been described, I also have my UDF disk auto-mounted at boot up, here is how I did that:

[http://ubuntuforums.org/showpost.php?p=725718&postcount=2](http://ubuntuforums.org/showpost.php?p=725718&postcount=2)

---

### Post by GTvulse on 2006-02-19
[QUOTE=dcstar]I have my UDF set up in a similar manner to what has been described, I also have my UDF disk auto-mounted at boot up[/QUOTE]

When you create your mount points under [FONT="monospace"]/media[/FONT], the gnome volume manager will automatically mount them unless you use the [FONT="monospace"]noauto[/font] option in [font=monospace]fstab[/font]. I find it more practical to use the options [font=monospace]noauto,user[/font] and mount the disk by hand, because that sets the [FONT="monospace"]euid[/FONT] and [FONT="monospace"]egid[/FONT] to my account's not root's.

---

### Post by Cariboo1938 on 2006-09-01
> **dradul said:**
> **Packet Writing Without Tears: How to use Rewritable Optical Media in Ubuntu**
*Pedro A. López-Valencia* 
In my particular case I'm using a CD writer in [FONT="Courier"]/dev/hdd[/FONT], thus I edited the file to contain this line:
```
DEVICES="/dev/hdd"
```I have a DVD-R/W and a seperate CD-R/W drive installed. How do I know where I use them? hda, hdb, hdc, etc? Please help! I'm trying to get packet writing running since I first used Linux 2 years ago. Now I found Pedro's HowTo and it seems I'm very close, but still don't know how to continue?

---

### Post by GTvulse on 2006-09-02
> **Cariboo1938 said:**
> I have a DVD-R/W and a seperate CD-R/W drive installed. How do I know where I use them? hda, hdb, hdc, etc? Please help! I'm trying to get packet writing running since I first used Linux 2 years ago. Now I found Pedro's HowTo and it seems I'm very close, but still don't know how to continue?

You can enable several devices in /etc/default/udftools (see the file for exact syntax). Now, on where are your burners, that depends on where you have them installed. Most older mainboards have 2 IDE interfaces, a primary and a secondary each capable of managing two PATA (Parallel ATA) disks, a master (disk0) and a slave (disk1). The custom has been to install the CD/DVD devices in the secondary bus, while leaving the primary for installing hard-drives (most BIOS would only boot from IDE0/disk0). IDE devices are seen by the Linux kernel as /dev/hd*, where "hda" is IDE0:disk0, "hdb" is IDE0:disk1, "hdc" is IDE1:disk0 and so on.

Newer mainboards come with only one IDE interface (for CD/DVD devices), and use SATA (Serial ATA) interfaces for hard-drives. Linux uses a SCSI emulation for the interface of such devices and therefore they are seen as /dev/sd*. In this case, the Cd/DVD devices would be in the primary IDE interface (IDE0) and will be seen as "hda" and "hdb".

---

### Post by Cariboo1938 on 2006-09-02
> **dradul said:**
> You can enable several devices in /etc/default/udftools (see the file for exact syntax). Now, on where are your burners, that depends on where you have them installed. Most older mainboards have 2 IDE interfaces, a primary and a secondary each capable of managing two PATA (Parallel ATA) disks, a master (disk0) and a slave (disk1). The custom has been to install the CD/DVD devices in the secondary bus, while leaving the primary for installing hard-drives (most BIOS would only boot from IDE0/disk0). IDE devices are seen by the Linux kernel as /dev/hd*, where "hda" is IDE0:disk0, "hdb" is IDE0:disk1, "hdc" is IDE1:disk0 and so on.
Newer mainboards come with only one IDE interface (for CD/DVD devices), and use SATA (Serial ATA) interfaces for hard-drives. Linux uses a SCSI emulation for the interface of such devices and therefore they are seen as /dev/sd*. In this case, the Cd/DVD devices would be in the primary IDE interface (IDE0) and will be seen as "hda" and "hdb".

Hi dradul, and many thanks for this excellent explanation! Remains only one quick question to this naming issue: 
The Device Manager tells me that the Parallel ATA controller has 2 IDE devices connected--Master device DVDRAM GSA-4160B and Slave device CDRAM GCE-8526B. So, during the Ubuntu installation the hardware was detected correctly. Now the question: Into which file is the information and the name of the two drives written? Is it in /etc/fstab?

---

### Post by Cariboo1938 on 2006-09-02
> **dradul said:**
> You can enable several devices in /etc/default/udftools (see the file for exact syntax).Hello dradul, and once again thank you for your reply. I'm a little mixed up how to enable both of my optical drives. The line in /etc/default/udftools responsible for the enabling is [COLOR="Blue"]DEVICES="/dev/cdrom"[/COLOR], where I replace <cdrom> with hda (for the master device). 
To enable the other drive, would I have to repeat this line? So my file would look like this?
[COLOR="Blue"]DEVICES="/dev/hda"
DEVICES="/dev/hdb"[/COLOR]
or is the entry rather: 
[COLOR="Blue"]DEVICES="/dev/hda /dev/hdb"[/COLOR]???

---

### Post by GTvulse on 2006-09-03
> **Cariboo1938 said:**
> ```
DEVICES="/dev/hda /dev/hdb"
```


That's the ticket. :D

---

### Post by Cariboo1938 on 2006-09-04
> **dradul said:**
> **Packet Writing Without Tears: How to use Rewritable Optical Media in Ubuntu**
*Pedro A. López-Valencia*
*[SIZE="1"]python -c 'print "cGFsb3BlenZAZ21haWwuY29t".decode("base64")'[/SIZE]*
Hi dradul, I'm still working on it....
Following your instructions so far, I got the  following messages when I formatted a blank CD-R/W:> owner@Owner-Desktop:~$ sudo cdrwtool -t 4 -d /dev/hdb -q
setting speed to 4
using device /dev/hdb
1905KB internal buffer
setting write speed to 4x
Settings for /dev/hdb:
        Fixed packets, size 32
        Mode-2 disc

I'm going to do a quick setup of /dev/hdb. The disc is going to be blanked and formatted with one big track. All data on the device will be lost!! Press CTRL-C to cancel now.
ENTER to continue.

Initiating quick disc blank
Disc capacity is 295264 blocks (590528KB/576MB)
Formatting track
start=0, blocks=16, type=RESERVED
start=16, blocks=3, type=VRS
start=19, blocks=237, type=USPACE
start=256, blocks=1, type=ANCHOR
start=257, blocks=31, type=USPACE
start=288, blocks=32, type=PVDS
start=320, blocks=32, type=LVID
start=352, blocks=32, type=STABLE
start=384, blocks=1024, type=SSPACE
start=1408, blocks=293568, type=PSPACE
start=294976, blocks=31, type=USPACE
start=295007, blocks=1, type=ANCHOR
start=295008, blocks=160, type=USPACE
start=295168, blocks=32, type=STABLE
start=295200, blocks=32, type=RVDS
start=295232, blocks=31, type=USPACE
start=295263, blocks=1, type=ANCHOR
Writing UDF structures to disc
Quick setup complete!
owner@Owner-Desktop:~$
[COLOR="Blue"]This looks ok to me, what do you think?[/COLOR]
 
But now I got stuck again. 
You wrote:> **Mounting your cd**
There is only one thing to consider. You need to use the special packet writing device, not the normal disk device!!! Like this:
```
sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /[COLOR="Magenta"]your[/COLOR]/mount/point
```
I've added the utf8 option because that's the default filesystem encoding in Ubuntu, and noatime because that reduces drastically the number of access writes to the disc. This is particularly important if using a DVD-/+RW, because *writable DVDs are programmed to allow 1000 writes, not one more*!!!
[COLOR="Blue"]Here I don't know what would be /[COLOR="Magenta"]my[/COLOR]/mount/point??[/COLOR]
 
One more question. 
You wrote:> Making a permanent addition to your system

Now you are ready to set up your system to mount and unmount your CDs without effort. Create an entry in /media:
Code:
sudo mkdir -p /media/cdwriter
and add the following to /etc/fstab:
Code:
/dev/pktcdvd/0 /media/cdwriter udf user,noauto,noatime,utf8 0 0
If I have two drives to use for packet writing, [COLOR="Blue"]would I have to enter 2 different cdwriters???[/COLOR]

---

### Post by GTvulse on 2006-09-05
> **Cariboo1938 said:**
> Hi dradul, I'm still working on it....
Following your instructions so far, I got the  following messages when I formatted a blank CD-R/W:[COLOR="Blue"]This looks ok to me, what do you think?[/COLOR]

That's the expected output. You are fine.
> 
But now I got stuck again. 
You wrote:[COLOR="Blue"]Here I don't know what would be /[COLOR="Magenta"]my[/COLOR]/mount/point??[/COLOR]

Anywhere you want. If you want the volume to be managed by GNOME's automounter, create the mounting directory under /media.
> 
One more question. 
You wrote:If I have two drives to use for packet writing, [COLOR="Blue"]would I have to enter 2 different cdwriters???[/COLOR]

Yes, definitely.

---

### Post by Cariboo1938 on 2006-09-07
> **dradul said:**
> That's the expected output. You are fine.
Anywhere you want. If you want the volume to be managed by GNOME's automounter, create the mounting directory under /media.
Yes, definitely.Thank you dradul. 
I feel sorry for bothering you with this issue, but I hope it is the last time. I have trouble to mount the drives. 
Here is what I did so far:> [COLOR="Magenta"][SIZE="3"]My configuration for hdparm:[/SIZE][/COLOR]

##The following lines were added Sept.03, 2006 to prepare for
##packet writing. hda is the DVD/CD-R/W drive (Master, cdvdwriter) and hdb is the
##CD-R/W drive (Slave, cdwriter).

/dev/hda {
    dma = on
    io32_support = 1
 }

/dev/hdb {
    dma = on
    io32_support = 1
}
----------------------------------------------------------------------
[SIZE="3"][COLOR="Magenta"]My Mount Points:[/COLOR]
[/SIZE]
/media/cdvdwriter
/media/cdwriter

owner@Owner-Desktop:/media$ ls
cdwriter  cdvdwriter

-----------------------------------------------------------------------

[COLOR="Magenta"][SIZE="3"]Mounting seems not to work:[/SIZE][/COLOR]

owner@Owner-Desktop:/$ sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/cdvdwriter
mount: /dev/pktcdvd/0: can't read superblock
owner@Owner-Desktop:/$ sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/cdwriter
mount: /dev/pktcdvd/0: can't read superblock
owner@Owner-Desktop:/$

The "Computer Browser" shows two new icons: cdwriter, cdvdwriter.
Clicking on them gives error message: 

Unable to mount the selected volume.
Show more details:
mount: /dev/pktcdvd/1: can't read superblock 
[COLOR="Blue"]What does this mean:"can't read superblock"???
What do I have to do next to get the drives mounted???
[/COLOR]
I can, in both drives, format a CD-RW and I can use it in Windows XP to copy and delete files or directories as I was used to when working only in Windows XP. So, I think I'm pretty close now to have this feature in Linux too.

Here is more information. Maybe there is something wrong in /etc/fstab: 

> [COLOR="Magenta"][SIZE="3"]My "fstab":[/SIZE][/COLOR]

##Last two lines entered Sept.07, 2006, to enable packet writing.
##
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /Storage        ext3    defaults        0       2
/dev/sda1       /boot           ext3    defaults        0       2
/dev/sda5       /home           ext3    defaults        0       2
/dev/sda6       /usr            ext3    defaults        0       2
/dev/sda7       /var            ext3    defaults        0       2
/dev/sda8       none            swap    sw              0       0

/dev/hda        /dev/dvdrw         udf,iso9660 user,noauto        0  0
/dev/hdb        /dev/cdrw          udf,iso9660 user,noauto        0  0

/dev/pktcdvd/0  /media/cdvdwriter  udf  user,noauto,noatime,utf8  0  0
/dev/pktcdvd/1  /media/cdwriter    udf  user,noauto,noatime,utf8  0  0


---

### Post by GTvulse on 2006-09-08
> **Cariboo1938 said:**
> Thank you dradul. 
I feel sorry for bothering you with this issue, but I hope it is the last time. I have trouble to mount the drives. 
Here is what I did so far:
[COLOR="Blue"]What does this mean:"can't read superblock"???
What do I have to do next to get the drives mounted???
[/COLOR]
I can, in both drives, format a CD-RW and I can use it in Windows XP to copy and delete files or directories as I was used to when working only in Windows XP. So, I think I'm pretty close now to have this feature in Linux too.

Here is more information. Maybe there is something wrong in /etc/fstab:

You may need to disable the other, default, entries. The message means that the cd has already been mounted as a read-only volume probably. You can solv it by setting the default entries to be "noauto" and using pmount to mount them as neded.

---

### Post by Cariboo1938 on 2006-09-08
> **dradul said:**
> You may need to disable the other, default, entries. The message means that the cd has already been mounted as a read-only volume probably. You can solv it by setting the default entries to be "noauto" and using pmount to mount them as neded.[COLOR="Blue"]Where can/must I do this *"disable the other, default, entries"*? 
Would it be in /etc/fstab? [/COLOR]
I have tried this, altough the default entries alreadly were 'noauto':> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0

/dev/sda2 / ext3 defaults,errors=remount-ro 0 1
/dev/sda3 /Storage ext3 defaults 0 2
/dev/sda1 /boot ext3 defaults 0 2
/dev/sda5 /home ext3 defaults 0 2
/dev/sda6 /usr ext3 defaults 0 2
/dev/sda7 /var ext3 defaults 0 2
/dev/sda8 none swap sw 0 0

[COLOR="Red"]#/[/COLOR]dev/hda /dev/dvdrw udf,iso9660 user,noauto 0 0
[COLOR="Red"]#/[/COLOR]dev/hdb /dev/cdrw udf,iso9660 user,noauto 0 0

/dev/pktcdvd/0 /media/cdvdwriter udf user,noauto,noatime,utf8 0 0
/dev/pktcdvd/1 /media/cdwriter udf user,noauto,noatime,utf8 0 0
I'm afraid I messed up now. The "Computer - File Browser" shows 4 optical drives now:
1) CD-RW drive
2) CD-RW/DVD+/-R drive
3) cdwriter
4) cdvdwriter
CD-RW and CD-RW/DVD drives can be opened, but not cdwriter and cdvdwriter.
I checked "/var/log/syslog" and got lots of messages like:> Sep  8 08:00:54 localhost kernel: [49317.123078] cdrom: open failed.

Sep  8 08:02:50 localhost kernel: [49381.682978] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'LinuxUDF', timestamp 2006/09/04 11:40 (1e5c)


Sep  8 08:03:15 localhost kernel: [49395.875328] hda: command error: status=0x51 { DriveReady SeekComplete Error }
Sep  8 08:03:15 localhost kernel: [49395.875335] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Sep  8 08:03:15 localhost kernel: [49395.875339] ide: failed opcode was: unknownSep  8 08:03:15 localhost kernel: [49395.875342] end_request: I/O error, dev hda, sector 1280
Sep  8 08:03:15 localhost kernel: [49395.875345] Buffer I/O error on device hda, logical block 320
Sep  8 08:03:52 localhost kernel: [49416.181746] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'LinuxUDF', timestamp 2006/09/04 11:40 (1e5c)
 
Sep  8 08:04:38 localhost kernel: [49441.789939] cdrom: hdb: mrw address space DMA selected
Sep  8 08:04:38 localhost kernel: [49441.800567] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Sep  8 08:04:38 localhost kernel: [49441.800573] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[COLOR="SeaGreen"]I'm lost, please help![/COLOR]

---

### Post by Cariboo1938 on 2006-09-11
Hello dradul,
I'm still struggling with /MY/MOUNT/POINT. I followed your instructions and I can format CD-RWs for packet writing in both drives (I can open them under Windows XP and find the Folder 'Lost&Found' on them). 
I still can not set up my system to mount and unmout my CD's.
In my case I have a DVD/CD-RW combo drive (hda) and a standard CD-RW drive (hdb) installed.
Putting a formatted CD in drive hda I get "dvdrecorder" entered in /media.
Putting a formatted CD in drive hdb I get "cdrecorder" entered in /media. If I eject the CD, /media/dvdrecorder or /media/cdrecorder is deleted.

In both cases, when I try to open the CD, I get the message:
> 
The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "dvdrecorder" / "cdrecorder".
This makes sense, because I didn't enable all owners yet. 
You recommend  in your HOW-TO to make the CD/DVD-RW writable to other users with the command: 
*sudo chown /your/mount/point/.* 
Now, I guess the mount point in my case would be : 
/media/dvdrecorder or /media/cdrecorder
If I apply this in the command line, I can see (in properties of dvdrecorder or cdrecorder) that the owner is changed from root to 777, but I still get the message (see above Quote). 
[COLOR="Blue"]What do I do wrong?[/COLOR]

---

### Post by Cariboo1938 on 2006-09-13
Hello dradul,
Since days I try to get [COLOR="Blue"]MY/MountPoint/Problem[/COLOR] fixed, without success. Maybe you find a minute to check where I'm making a mistake when carrying out your instructions. I wrote a conclusion what I did so far:> Conclusion of  [dradul's HOWTO]("http://www.ubuntuforums.org/showthread.php?t=129093&highlight=Packet+Writing+tears") how it worked in my case. All codes and instructions are derived from the above mentioned HOWTO.

Before installing the software for "packet writing" :
1) Set the drive hirachy:
pktcdvd/In my case I have two IDE drives, a CD-R/W drive and a DVD/CD-R/W Combo drive. It seems that Linux expects to have a CD-drive as master (hda) and the DVD-drive as slave (hdb).
2) Check /etc/fstab if the drives a entered correctly:
In my case I entered the lines 
/dev/hda      /media/cdrom1    udf,iso9660   rw,users,noauto       0       0
/dev/hdb      /media/cdvdrw    udf,iso9660   rw,users,noauto       0       0

**Install udftools for packet writing.**
```
sudo aptitude install udftools
```
**Add the drives used for packetwriting.**
```
sudo gedit /etc/default/udftools
```
**Un-comment and edit (in my case):** 
```
DEVICES="/dev/hda /dev/hdb"
```
Remark: CR-RW drive is IDE-Master device hda
        DVD/CD-RW combo drive is IDE-Slave device hdb

**Start packet writing.**
```
sudo /etc/init.d/udftools start
```
Prompt:Starting udftools packet writing:
            /dev/pktcdvd/0=/dev/hda /dev/pktcdvd/1=/dev/hdb

**Activate permanently DMA.**
```
sudo gedit /etc/hdparm.conf
```
**Add the following lines:**
```
/dev/hda {
    dma = on
    io32_support = 1
 }
/dev/hdb {
    dma = on
    io32_support = 1
}
```
**Insert and format a blank CD-RW or DVD-/+RW.**
Ignore the message: You have inserted a blank disc.
(Depending which drive you choose, the code uses either hda or hdb. Here I chose the DVD drive hdb).
```
sudo cdrwtool -t 4 -d /dev/hdb -q
```
Prompt:
setting speed to 4
using device /dev/hdb
1029KB internal buffer
setting write speed to 4x
Settings for /dev/hdb:
        Fixed packets, size 32
        Mode-2 disc
I'm going to do a quick setup of /dev/hdb. The disc is going to be blanked and formatted with one big track. All data on the device will be lost!! Press CTRL-C to cancel now.
ENTER to continue.
Initiating quick disc blank
Disc capacity is 295264 blocks (590528KB/576MB)
Formatting track
start=0, blocks=16, type=RESERVED
start=16, blocks=3, type=VRS
start=19, blocks=237, type=USPACE
start=256, blocks=1, type=ANCHOR
start=257, blocks=31, type=USPACE
start=288, blocks=32, type=PVDS
start=320, blocks=32, type=LVID
start=352, blocks=32, type=STABLE
start=384, blocks=1024, type=SSPACE
start=1408, blocks=293568, type=PSPACE
start=294976, blocks=31, type=USPACE
start=295007, blocks=1, type=ANCHOR
start=295008, blocks=160, type=USPACE
start=295168, blocks=32, type=STABLE
start=295200, blocks=32, type=RVDS
start=295232, blocks=31, type=USPACE
start=295263, blocks=1, type=ANCHOR
Writing UDF structures to disc
Quick setup complete!

**Create a mount point and mount the CD.**
```
sudo mkdir -p /media/udf0
```
```
sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/udf0
```
[SIZE="3"][COLOR="Red"]Prompt:
mount: /dev/pktcdvd/0: can't read superblock[/COLOR][/SIZE]
 
This is my fstab:
> 
# /etc/fstab: static file system information.
#<file system> <mount point>   <type>   <options>          <dump>  <pass>
## Linux 'Ubunu 6.06'
proc             /proc           proc     defaults             0       0
/dev/sda2        /                ext3    defaults,errors=remount-ro 0       1
/dev/sda3        /Storage         ext3    defaults             0       2
/dev/sda1        /boot            ext3    defaults             0       2
/dev/sda5        /home            ext3    defaults             0       2
/dev/sda6        /usr             ext3    defaults             0       2
/dev/sda7        /var             ext3    defaults             0       2
/dev/sda8        none             swap    sw                   0       0
#/dev/hda      /media/cdrom1    udf,iso9660   rw,users,noauto        0      0
#/dev/hdb      /media/cdvdrw    udf,iso9660   rw,users,noauto        0      0
#/dev/pktcdvd/0  /media/cdwriter   udf    users,noauto,noatime,utf8  0      0
#/dev/pktcdvd/1  /media/dvdwriter  udf    users,noauto,noatime,utf8  0      0
## Windows 'XP Home'
#/dev/sdb1        /mnt/Windows  HPFS/NTFS    ro,defaults                0      1
#/dev/sdb2        /mnt/User     HPFS/NTFS    rw,defaults,users,noauto,  0      2
 I commented /devhda,/dev/hdb,/dev/pktcdvd/0 and /dev/pktcdvd/1 when I couldn't mount the CD. [COLOR="Red"]Still Error Can't read super block![/COLOR]
You already wrote >  Originally Posted by dradul [View Post]("http://www.ubuntuforums.org/showpost.php?p=1476368&postcount=14") 
You may need to disable the other, default, entries. The message means that the cd has already been mounted as a read-only volume probably. You can solv it by setting the default entries to be "noauto" and using pmount to mount them as neded.[COLOR="Blue"]Where can/must I do this "disable the other, default, entries"? I don't know how to do it.[/COLOR]

---

### Post by Cariboo1938 on 2006-09-18
> **dradul said:**
> You may need to disable the other, default, entries. The message means that the cd has already been mounted as a read-only volume probably. You can solv it by setting the default entries to be "noauto" and using pmount to mount them as neded.:-\" It works! Yes, 'Packet Writing' works on my system!
I think... old as I am... I still made one of those stupid mistakes doing things without exactly knowing what I do. 
I had to mount a CD and not the CD drive, because the CD has the File System on it I wanted to use...UDF. 
The solution is: 
When executing the command ```
sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/udf0
```**the CD has to be inserted** in the corresponding drive! Oh yeah! Forgive me, dradul, for bothering you so terribly. I'm slow, I know, but sooner or later I'll get it. Thanks to all who helped!=D>

---

### Post by Cariboo1938 on 2006-10-07
Hi everybody, 
I have wrecked my Ubuntu 6.06 (Dapper Drake) installation and I want to install Ubuntu 6.10 (Edgy Eft).
Can I use [dradul's HowTo]("http://www.ubuntuforums.org/showthread.php?t=129093&highlight=Packet+writing+without+tears") to enable 'Packet writing'...I mean, 
[COLOR="Blue"]is the procedure the same for Ubuntu 6.10 as it was for Ubuntu 6.06???[/COLOR]
Thanks in advance for any reply!
:-k Cariboo

---

### Post by jis on 2006-10-14
> **dradul said:**
> **Packet Writing Without Tears: How to use Rewritable Optical Media in Ubuntu**
*Pedro A. López-Valencia*

Now, set up your drive:
```
sudo /etc/init.d/udftools start
```


The command you suggested gives me this output:
> Starting udftools packet writing:
/dev/pktcdvd/0=/dev/hdd/ open cd-rom: Not a directory

Is there something wrong?

P.S I just modified line
DEVICES="/dev/hdd/"
to be 
DEVICES="/dev/hdd"
Now the command does not complain.


Is there any point to setup normal packet writing, if you have a Mount Rainier capable drive? AFAIK formatting to Mount Rainier format requires using a separate software not available in any ubuntu repository! (I would like to see the utility included in all ubuntu distros via some repository.) I have successfully used Mount Rainier format as I have explained in [this thread]("http://www.ubuntuforums.org/showthread.php?t=196951").

---

### Post by trents on 2006-11-08
Okay, been trying to follow your directions to get packet writing going. I have two devices capable of packet writing: a cd burner and a cddvd burner. I edited udftools and added the line: DEVICES="/dev/hdd /dev/sr0" so that the relevant section looks like this:

# Drives to register for packet writing:
#DEVICES="/dev/hdd /dev/sr0"
DEVICES="/dev/hdd /dev/sr0"

Then I issued the command in terminal: sudo /etc/init.d/udftools start

But, I got this message:
Starting udftools packet writing:
/dev/pktcdvd/0=/dev/hdd Device node '0' already in use
/dev/pktcdvd/1=/dev/sr0 open cd-rom: No such file or directory

What did I do wrong?

Steve

---

### Post by Cariboo1938 on 2006-11-12
> **trents said:**
> 
# Drives to register for packet writing:
#DEVICES="/dev/hdd /dev/sr0"
DEVICES="/dev/hdd /dev/sr0"
SteveAre you sure you choose the right device names? 
Did you check /etc/fstab? 
What are the names for the drives there?
Mine look like this:> 
[COLOR="Magenta"]/dev/hda[/COLOR]        /media/cdrom0   udf,iso9660 	rw,user,noauto     		0      0 (This is my [COLOR="Magenta"]CD-R/W[/COLOR])
[COLOR="Magenta"]/dev/hdb [/COLOR]       /media/cdrom1   udf,iso9660 	rw,user,noauto     		0      0 This is my [COLOR="Magenta"]CDVD-R/W[/COLOR])


---

### Post by Cariboo1938 on 2006-11-13
> **Cariboo1938 said:**
> :-\" It works! Yes, 'Packet Writing' works on my system!
But...It's not working for DVD-RW's because I found no way to format them. cdrwtool doesn't work. 
For CD-RW's it works partially.... there is still an issue with mounting... 
So, actually it is not what I was used to in "Nero, InCD":-k

---

### Post by Cariboo1938 on 2006-11-18
> **dradul said:**
> **Packet Writing Without Tears: How to use Rewritable Optical Media in Ubuntu**
*Pedro A. López-Valencia*
*[SIZE="1"]python -c 'print "cGFsb3BlenZAZ21haWwuY29t".decode("base64")'[/SIZE]*

**Formatting your CD-RW**
Before you start formatting your CD, make sure that you have DMA active in your burner...
In order to activate permanently DMA, you must edit your [font=monospace]/etc/hdparm.conf[/font]
 My /etc/hdparm.conf entries are as follows:
> #Activating DMA permanently for Packet Writing 
/dev/hda {
    dma = on
    io32_support = 1
 }
/dev/hdb {
    dma = on
    io32_support = 1
}

> **dradul said:**
> 
Take a CD-RW [COLOR="Magenta"]or DVD-/+RW [/COLOR]and format it:
```
sudo cdrwtool -t 4 -d /dev/hdd -q
```
Go brew a carafe of cofee  and grab some muffins. Drink slowly...  
Error message when I try to format the DVD:
> root@BitByter:~# sudo cdrwtool -t 4 -d /dev/hdb -q
setting speed to 4
using device /dev/hdb
1088KB internal buffer
setting write speed to 4x
Settings for /dev/hdb:
        Fixed packets, size 32
        Mode-2 disc

I'm going to do a quick setup of /dev/hdb. The disc is going to be blanked and formatted with one big track. All data on the device will be lost!! Press CTRL-C to cancel now.
ENTER to continue.

Initiating quick disc blank
Disc capacity is 3524075584 blocks (2753183872KB/6882960MB)
Formatting track
[COLOR="Red"]wait_cmd: Input/output error
Command failed: 04 17 00 00 00 00 00 00 00 00 00 00 - sense 00.24.00
format disc: Illegal seek[/COLOR]
root@BitByter:~# My DVD drive is a LG GSA-4160B which, the Device Manager tells me, is found as HL-DT-ST DVDRAM GSA-4160B.
[COLOR="Blue"]Is this a hardware problem or do I have to use a different command to format the DVD?[/COLOR]

---

### Post by sawjew on 2006-12-05
cariboo, I have been using dvd-ram for quite a while now with no problems.  If you are using a dvd-ram drive, as it appears you are, you shouldn't need to do any of this it should just work.  If you buy a preformatted dvd-ram disk you should be able to just use it in your dvd-ram drive and save to it, drag and drop and everything just like using a hard drive.  

To format a dvd-ram disk just use the standard hard drive formatting tools.  I use fat32 for my dvd-ram now as it's readable anywhere but I last formatted it in Windows.  To format with udf just open a terminal and enter
```
mkudffs --utf8 --media-type=dvdram /dev/<your device name>
```

This should get you working with udf.

Otherwise you can use use mke2fs for ext2 or anything else you would like to use.

NOTE: you will need udftools installed to use mkudffs but it is installed by default in Edgy and I think in Dapper too.

---

### Post by Cariboo1938 on 2006-12-06
> **sawjew said:**
> ....
 To format with udf just open a terminal and enter
```
mkudffs --utf8 --media-type=dvdram /dev/<your device name>
```
This should get you working with udf.
Thanks sajew, for offering help! I just came home and found your response. I want to use disks from TDK "DVD-RW recordable 4x 4.7GB". would these be dvd-ram types you talk about? Another  quick question: the term "--media-type=dvdram" in the above code is valid in general or do I have to enter something specific to my installation?

---

### Post by sawjew on 2006-12-06
> **Cariboo1938 said:**
> Thanks sajew, for offering help! I just came home and found your response. I want to use disks from TDK "DVD-RW recordable 4x 4.7GB". would these be dvd-ram types you talk about? Another  quick question: the term "--media-type=dvdram" in the above code is valid in general or do I have to enter something specific to my installation?

No dvd-ram disks are a specific type of disk not a dvd-rw, they usually come pre-formatted with udf although sometimes you can get them with fat32 (or so I have been told, I have never seen them).  I don't know if you can do packet writing on a dvd-rw but if you have a dvd-ram drive then using dvd-ram disks is much simpler.  Be warned that dvd-ram disks are quite expensive (about AU$15) but they can be reused and re-formatted a lot more times than a standard dvd-rw.  

As far as the "--media-type=dvdram" goes that is telling it that you are formatting a dvd-ram disk, you would put "--media-type=cdrw" if you were formatting a cd-rw disk.  If you want the full information about mkudffs just open Yelp (Help) and in the search box type ```
man mkudffs
```

You may be able to format a dvd-rw as udf and use it with packet writing as in this how-to but dvd-ram is much easier.  I think the difference is that packet writing is done by software whereas dvd-ram writing uses the firmware in the drive and therefore requires no extra configuration to use it.

Hope this helps

---

### Post by Cariboo1938 on 2006-12-06
> **sawjew said:**
> No dvd-ram disks are a specific type of disk not a dvd-rw, they usually come pre-formatted with udf although sometimes you can get them with fat32 (or so I have been told, I have never seen them). 
You may be able to format a dvd-rw as udf and use it with packet writing as in this how-to but dvd-ram is much easier.  I think the difference is that packet writing is done by software whereas dvd-ram writing uses the firmware in the drive and therefore requires no extra configuration to use it.
Hope this helpsVery interesting, sajew, thank you for the info...:-k 
I didn't know about DVD-ram disks...so would I need to have a special drive too?
I try, since I have started to use Linux systems, to get packet writing working as it works in Windows with Nero's InCD. I have no clue why it is is such a problem to have this feature in Linux systems. Do you have an answer for that? PS.: I'm not a programmer or developer, I only use my computer for all these trivial like Text, Music, Picture, e-mail, Internet and it is very convenient to save your daily stuff just by using a re-writable disk and add /delete a folder without burning the whole CD again and again as K3b, GenomeBaker,....all do.

---

### Post by sawjew on 2006-12-06
> **Cariboo1938 said:**
> Very interesting, sajew, thank you for the info...:-k 
I didn't know about DVD-ram disks...so would I need to have a special drive too?
I try, since I have started to use Linux systems, to get packet writing working as it works in Windows with Nero's InCD. I have no clue why it is is such a problem to have this feature in Linux systems. Do you have an answer for that? PS.: I'm not a programmer or developer, I only use my computer for all these trivial like Text, Music, Picture, e-mail, Internet and it is very convenient to save your daily stuff just by using a re-writable disk and add /delete a folder without burning the whole CD again and again as K3b, GenomeBaker,....all do.

You do need to have a special drive but I only made this comment to you because in your initial post you mentioned that your drive was identified as a > HL-DT-ST DVDRAM GSA-4160B which appears to be a dvd-ram drive.  If this is the case you should be able to use a dvd-ram disk and be happily packet writing in no time.

I am no programmer either, I use the computer for everyday tasks and some engineering modelling tasks.  I gave up on packet writing a while ago with a normal cd-rw drive because it was too complicated and that was what drew me to this post to see if it had become easier.  I had it working at one stage, but it took quite a while to set up and I have since upgraded the system, but I have found the dvd-ram to be flawless.  

The easiest thing to do if you can't get packet writing working properly and don't have a dvd-ram drive, is just to get a large (2G or more) flash drive and use that or an external hard drive.

That said, your initial request was about formatting the drive and mkudffs should sort that one out.  I have never had any success formatting a disc in udf format with cdrwtools but have had no problems with mkudffs.

Addition: I used to use Direct Cd for Windows and I found that a disc formatted with Direct Cd would work in Linux perfectly but one formatted using mkudffs would not work in Windows.  I read somewhere that this is because Windows packet writing uses the older udf 1.5 format whereas Linux uses the newer udf 2.0 format.  Just a little extra info.

---

### Post by bitzbox on 2006-12-08
> **sawjew said:**
> To format a dvd-ram disk just use the standard hard drive formatting tools.  I use fat32 for my dvd-ram now as it's readable anywhere but I last formatted it in Windows.
I've been trying without success to format a DVD-RAM disk with the FAT32 filesystem. I'm a bit new to Linux so I'm probably doing something wrong but I've been using *mkdosfs* to do the formatting and it appears to work but Dapper won't mount the newly formatted DVD-RAM disk. It complains about an unknown filesystem - any ideas please?

---

### Post by sawjew on 2006-12-09
> **bitzbox said:**
> I've been trying without success to format a DVD-RAM disk with the FAT32 filesystem. I'm a bit new to Linux so I'm probably doing something wrong but I've been using *mkdosfs* to do the formatting and it appears to work but Dapper won't mount the newly formatted DVD-RAM disk. It complains about an unknown filesystem - any ideas please?

I have never used mkdosfs myself but from reading the man page it appears that you should just be able to enter```
mkdosfs -F 32 /dev/<your device>
```

I have only used mke2fs and mkudffs under linux to format dvd-ram disks.  The last format as a fat32 I did under Windows and it is working with no problems at all.

---

### Post by bitzbox on 2006-12-09
> **sawjew said:**
> I have never used mkdosfs myself but from reading the man page it appears that you should just be able to enter```
mkdosfs -F 32 /dev/<your device>
```
I entered this:
```
mkdosfs -F 32 -I /dev/hdc
```
I had to add -I because the disk had already been formatted under Windoze.
> 
I have only used mke2fs and mkudffs under linux to format dvd-ram disks.  The last format as a fat32 I did under Windows and it is working with no problems at all.
I'll try mke2fs and see what happens.

Another thing that's puzzling me is that my DVD drive is not listed in /etc/fstab but my CD-RW drive is.

---

### Post by Cariboo1938 on 2006-12-11
> **sawjew said:**
>  
The easiest thing to do if you can't get packet writing working properly and don't have a dvd-ram drive, is just to get a large (2G or more) flash drive and use that or an external hard drive.
 Thanks sawjew for your interesting comments. Do you know why there is a problem with the UDFs (Universal Data File system) or packet writing in the Linux world? Nobody was able yet to answer this question yet to me.
The large flash drive you are talking about, could this be also a SD memory card which I use in my Digital Camera?

---

### Post by jis on 2006-12-11
> **Cariboo1938 said:**
> Do you know why there is a problem with the UDFs (Universal Data File system) or packet writing in the Linux world? Nobody was able yet to answer this question yet to me.

Nowdays people use flash drives, external hard drives and network for backup, and transfer. Few developers use optical drives & UDF, even less have Mount Rainier cabable drive. (See [here]("http://www.ubuntuforums.org/showthread.php?t=196951") how I installed program that formats Mount Rainier.)

---

### Post by jis on 2006-12-11
> **Cariboo1938 said:**
> 
You recommend  in your HOW-TO to make the CD/DVD-RW writable to other users with the command: 
*sudo chown /your/mount/point/.* 
Now, I guess the mount point in my case would be : 
/media/dvdrecorder or /media/cdrecorder
If I apply this in the command line, I can see (in properties of dvdrecorder or cdrecorder) that the owner is changed from root to 777, but I still get the message (see above Quote). 
[COLOR="Blue"]What do I do wrong?[/COLOR]

When I am writing this, it is actually
```
sudo chown 777 /your/mount/point/.
```
in the how-to. I guess it should be
```
sudo chmod 777 /your/mount/point/
``` That way everybody can write to the disc. Could this be security risk? I wonder, if you could prevent other from changing your disc by using chown.

I have problem in unmounting the disc. If I give command
```
umount /my/mount/point
``` I get message
> umount: it seems /media/cdpktwriter is mounted multiple times

However, I can unmount by command
```
sudo umount -f /my/mount/point
``` Am I the only one having this problem? When I first time wrote big folder to the disc,  it seemed to work pretty fast. Then I tried to unmount, but it seemed to last forever and it seemed to me that files were still being copied. I tried to kill umount. After some time, umount stopped, so I wonder, if it has something to do with my unmounting problems. Maybe I should use sync option in fstab to prevent caching?

---

### Post by sawjew on 2006-12-12
> **bitzbox said:**
> I entered this:
```
mkdosfs -F 32 -I /dev/hdc
```
I had to add -I because the disk had already been formatted under Windoze.

I'll try mke2fs and see what happens.

Another thing that's puzzling me is that my DVD drive is not listed in /etc/fstab but my CD-RW drive is.

I tried mkdosfs and had the same problem and had to use -I, but then it complained about not being able to find the geometry and would not format the disk.  I have searched all over and it seems that it is a common problem and I have not found a solution.

I checked with mke2fs and it worked perfectly and mkudffs worked after a chmod -R 777 /media/cdrom0

You will need a fstab entry for the dvd-ram to work correctly because you will need to specify vfat and ext2 in fstab for your dvd-ram drive to mount it.  My fstab entry looks like this ```
/dev/hdc        /media/cdrom0   udf,vfat,ext2,rw,iso9660 user,noauto     0       0
```

> Thanks sawjew for your interesting comments. Do you know why there is a problem with the UDFs (Universal Data File system) or packet writing in the Linux world? Nobody was able yet to answer this question yet to me.


I don't really know why there is a problem with udfs under Linux but I have had almost as many problems with packet writing under Windows.  I used to use DirectCD for packet writing but I had numerous corrupted disks and lost data and the format used by DirectCd isn't compatible with Nero InCD and other vendors.  The whole packet writing situation seems to be a disorganised mess.  I only use dvd-ram now because it seems to be much more reliable. I have had few problems with dvd-ram but I mainly use flash drives and an extra hard drive for backups and file transfer now.

> The large flash drive you are talking about, could this be also a SD memory card which I use in my Digital Camera?

Yes you can use an SD memory card in exactly the same way as a flash drive if you have a way to mount it which you can usually do through your camera if nothing else.

---

### Post by jis on 2006-12-12
> **jis said:**
> 
I have problem in unmounting the disc. If I give command
```
umount /my/mount/point
``` I get message

However, I can unmount by command
```
sudo umount -f /my/mount/point
``` Am I the only one having this problem? When I first time wrote big folder to the disc,  it seemed to work pretty fast. Then I tried to unmount, but it seemed to last forever and it seemed to me that files were still being copied. I tried to kill umount. After some time, umount stopped, so I wonder, if it has something to do with my unmounting problems. Maybe I should use sync option in fstab to prevent caching?

I found that after rebooting, I can unmount normally :)

As for the sync option, I found this in the man page of mount:
> The following options apply to any file system that is being mounted (but not every file system actually honors them - e.g., the sync option today has effect only for ext2, ext3 and ufs):

so the sync option has no effect for udf "today".

---

### Post by jis on 2006-12-12
> **dradul said:**
> 
**Mounting your cd**

There is only one thing to consider. You need to use the special packet writing device, not the normal disk device!!! Like this:
```
sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /your/mount/point
```
I've added the utf8 option because that's the default filesystem encoding in Ubuntu, and noatime because that reduces drastically the number of access writes to the disc. This is particularly important if using a DVD-/+RW, because *writable DVDs are programmed to allow 1000 writes, not one more*!!!


I suppose utf8 option has no effect since it is not listed in the "Mount options for udf" section of man page of mount.

I wonder what user and group you see if you list directory contents of a cd in a machine other than the one cd is written by?

---

### Post by bodhi.zazen on 2006-12-17
Nice How-to

This thread has been added to the UDSF wiki.

[Packet_Writing](http://doc.gwos.org/index.php/Packet_Writing)

[color=blue]Thanks Crane[/color]

---

### Post by phenest on 2007-04-14
I have followed the instructions carefully and managed to format a CDRW and mount the disc. But, it won't let me copy anything to the disc. It doesn't say: 'Access denied', but instead: 'Couldn't write ...'.

Also, why 2 mount points: /your/mount/point and /media/cdwriter?:confused:

---

### Post by phenest on 2007-04-25
Ok. I made this work but only by using sudo. At first I could only copy files to the mount point (/media/udf in my case) using the terminal and even then had to use sudo. I realised I could open nautilus using sudo and drag and drop files but this doesn't seem a good way to do this. Is there a way so I don't have to use sudo?

---

### Post by phenest on 2007-05-02
I have to say, with a bit of determination, and trial and error, I got this working. My problem was getting read/write permissions for my mounting point. I resorted to using the root terminal to do this. Using sudo just didn't seem to make any difference.

---

### Post by phenest on 2007-05-05
I have found one small problem. If I have a pre-formatted CDRW in the drive when I boot my machine, the disc is mounted as read-only, and I have 2 icons for the CDRW in the tree view in nautilus (only 1 is usable). If I eject and re-mount (from nautilus), it becomes writable, and I only have 1 icon in the tree view (which is usable). But I also have 2 icons in nautilus permanently (only 1 is usable).

---

### Post by jw5801 on 2007-07-02
I have a UDF CD created using Windows that I can't seem to mount on Ubuntu. I haven't followed any of the writing parts of this HOW-TO as I don't want to be able to write to the CD, simply to read from it.
The important line of my fstab file reads as follows:
```
/dev/hda /media/cdrom0 udf,iso9660 rw,user,noauto 0 0
```
and here is my udftools file:
```
# Drives to register for packet writing:
DEVICES="/dev/hda"

# Pktcdvd patches for kernels 2.6.8 and later use a new interface for
# talking to the kernel, as well as a new set of device nodes. In case
# detection of the proper interface on your system fails, override
# it here. Possible values are "true" or "false".
# NEWINT=true

# Only when using the new interface do you have the option to choose the
# names for the packet writing devices. This is ignored otherwise.
# For example, if DEVICES="/dev/hdd /dev/sr0" and
# NEWINTNAMES="cdwriter dvdwriter", then /dev/hdd will correspond to
# /dev/pktcdvd/cdwriter, and /dev/sr0 will correspond to
# /dev/pktcdvd/dvdwriter. The default setting is NEWINTNAMES="0 1 2 3".
NEWINTNAMES="0 1 2 3"
```
If I try to stop and then start udftools this is what happens:
```
jw5801@jw5801-laptop:~$ sudo /etc/init.d/udftools stop
Stopping udftools packet writing:
/dev/pktcdvd/0=/dev/hda Can't find major/minor numbers

jw5801@jw5801-laptop:~$ sudo /etc/init.d/udftools start
Starting udftools packet writing:
/dev/pktcdvd/0=/dev/hda Device node '0' already in use
```
and if i uncomment and change the NEWINT line to NEWINT=false, this is what I get:
```
jw5801@jw5801-laptop:~$ sudo /etc/init.d/udftools stop
Stopping udftools packet writing:
/dev/pktcdvd/0=/dev/hda ioctl: Inappropriate ioctl for device

jw5801@jw5801-laptop:~$ sudo /etc/init.d/udftools start
Starting udftools packet writing:
/dev/pktcdvd/0=/dev/hda ioctl: Inappropriate ioctl for device
```

So the packet writer cannot open properly therefore attempting to mount through it gets this:
```
jw5801@jw5801-laptop:~$ sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/cdrom0
mount: /dev/pktcdvd/0 is not a block device (maybe try `-o loop'?)
jw5801@jw5801-laptop:~$ sudo mount -t udf -o loop /dev/pktcdvd/0 /media/cdrom0mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

jw5801@jw5801-laptop:~$ dmesg | tail
[20681.458436] UDF-fs: No fileset found
[20681.595117] Unable to identify CD-ROM format.
[20798.576184] APIC error on CPU0: 40(40)
[20840.260246] APIC error on CPU0: 40(40)
[20859.772417] APIC error on CPU0: 40(40)
[20892.449063] APIC error on CPU0: 40(40)
[20898.816874] APIC error on CPU0: 40(40)
[20948.112256] APIC error on CPU0: 40(40)
[21351.801021] APIC error on CPU0: 40(40)
[21537.107010] UDF-fs: No partition found (1)
```
Anyone have any ideas?

EDIT: It's not the CD that's bad either, it still mounts fine under XP.

---

### Post by HuwSy on 2008-06-20
Is this still possible under ubuntu? There seems to be support for readonly udf access in the kernel which im thinking must be conflicting.

Iv installed udftools setup its devices and started it to get the pkcdvd devices, but whenever I insert a packet dvd formated disk its automounted. If I remove udf from the dvdrw entry in fstab it atleast stops the automount with a nice error. 

But running:

mount -t udf -o utf8,noatime,rw /dev/pktcdvd/0 /media/cdrom0 && chmod 0777 /media/cdrom0

gives me a warning that its a readonly file system, how do I force it to the udftools version of the rw module, if that makes sense.

Thanks.

---

### Post by HuwSy on 2008-06-24
anyone?

---

### Post by RonCam on 2009-08-11
I came upon this thread through Google, hoping I would find a discussion of my question, but I didn't.  So ... 

How does one format an optical disc for MRW (Mount Rainier) compatibility?

Is this automatic, if the recorder's firmware supports it, without having to type anything special at the Command Line?  Or is some special syntax required?

For example, CD-RWs formatted with the Windows InCD utility (with MRW check-box checked) function normally, in Ubuntu, and then continue to work properly when returned to a Windows environment.

Isn't there someway to start the disc in Ubuntu, with a proper MRW format, and not have to dual-boot to Windows?

---

### Post by jis on 2009-08-11
You have to use cdmrw tool. I had to compile it myself, see [here]("http://ubuntuforums.org/showpost.php?p=1400422&postcount=10"). The link in it does not work now, but I guess you could use the source code available [here]("http://www.kernel.org/pub/linux/kernel/people/axboe/tools/cdmrw.c").

---

### Post by RonCam on 2009-08-12
:grin: Many thanks for hard-to-come-by information.  I will bookmark this and get back to the thread should I need help.  Good to know one other person has managed to do this!

I was able to get two Mount Rainier drives on my new system, partly because I knew GNU/Linux supported it, so I'd be hardware-ready to make the switch.  

Nero's InCD gives the choice of MRW, or the higher versions of UDF.  The Mount Ranier-formatted CD-RWs seem more responsive when dragging files in and out of a directory.  Not certain why the UDF's with error correction seem to have replaced it.

---

### Post by BubbaBlues on 2010-01-17
Thought you said without tears. :(  I was crying like a baby by the second page.

---

