---
title: "Starting Ubuntu from GRUB command line ?"
date: 2016-11-11
forum: New to Ubuntu
---

### Post by titanic1955 on 2016-11-11
Hi everyone,

I wanted to try and start starting Ubuntu from the GRUB command line
 with:

```
set root=(sdX,Y)

linux /vmlinuz root=/dev/sdX,Y ro

initrd /initrd.img

boot
```

It does not work for me. :confused:

I have two harddisks
One is empty.
Ubuntu is on sdb*

Here is my sudo fdisk -l

```
Gerät      Boot Start      Ende  Sektoren Größe Id Typ
/dev/sda1        2048 625141759 625139712 298,1G 83 Linux

Medium /dev/sdb: 256,2 GiB, 275064201216 Bytes, 537234768 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 512 Bytes
I/O Größe (minimal/optimal): 512 Bytes / 512 Bytes
Typ der Medienbezeichnung: dos
Medienkennung: 0x68a65533


Gerät      Boot     Start      Ende  Sektoren Größe Id Typ
/dev/sdb1  *         2048 520458239 520456192 248,2G 83 Linux
/dev/sdb2       520460286 537233407  16773122     8G  5 Erweiterte
/dev/sdb5       520460288 537233407  16773120     8G 82 Linux Swap / Solaris

```
Thanks in advance for all tips . . .

---

### Post by Bashing-om on 2016-11-11
titanic1955; Hello;

Grub will always see the booting hard drive as 'hd0' - in the MBR partitioning scheme - and partitions numbered starting at '1'
So try this for a booting sequence from the grub prompt:
```

set root=(hd0,msdos1) #maybe not required to set this path, as grub may have discovered 
insmod linux # again, grub may have discovered 
linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```

In a consistent grub state .. only 3 commands needed to boot up : linux, initrd, and boot.

[INDENT][INDENT][INDENT]grub is some kind of smart
[/INDENT][/INDENT][/INDENT]

---

### Post by titanic1955 on 2016-11-12
Hi Bashing-om,

Thanks for your fast reply.
I tried it with your configuration 

and even tried to replace hd0 with hd1.
but the kernel 

Ends at Busybox     built in Shell (ash).  :(

I have a graphic GRUB Customizer installed.

Here is the boot sequence:

```
recordfail
load_video
gfxmode $linux_gfx_mode
insmod gzio
if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
insmod part_msdos
insmod ext2
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  7af42550-7553-4dd2-8aaf-e6610ea7bc43
else
  search --no-floppy --fs-uuid --set=root 7af42550-7553-4dd2-8aaf-e6610ea7bc43
fi
linux    /boot/vmlinuz-4.4.0-47-generic root=UUID=7af42550-7553-4dd2-8aaf-e6610ea7bc43 ro  quiet splash $vt_handoff
initrd    /boot/initrd.img-4.4.0-47-generic


```
Talk to ya soon . . .

---

### Post by wildmanne39 on 2016-11-12
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

### Post by titanic1955 on 2016-11-12
Hallo Wild Man,

That means you also don't know the answer ? :confused:

---

### Post by wildmanne39 on 2016-11-12
No I do not know the answer I would have posted it, I work with wireless issues. But we are a large community and their are some very knowledgeable people here so I am confident someone will have the answer.

---

### Post by yancek on 2016-11-12
Your attempt to start Ubuntu from a Grub command prompt in your initial post will obviously not work since you are telling it to find the kernel (vmlinuz) in the root of the filesystem when as your later post clearly shows that it is in the /boot directory.  Same with the initrd line which is in /boot.  Set root should be hd1,msdos1 if it is on sdb1.

---

### Post by titanic1955 on 2016-11-12
Hallo Yancek,
> **yancek said:**
> Your attempt to start Ubuntu from a Grub command prompt in your initial post will obviously not work since you are telling it to find the kernel (vmlinuz) in the root of the filesystem when as your later post clearly shows that it is in the /boot directory.  Same with the initrd line which is in /boot.  Set root should be hd1,msdos1 if it is on sdb1.


I tried myself using  **/boot/vmlinuz** and **set root=(hd1,msdos1)**
and I had a** Kernel Panic**. :shock:

Could you give me the correct 4 lines:

set root=(sdX,Y)

linux /vmlinuz root=/dev/sdX,Y ro

initrd /initrd.img

boot

---

### Post by Bashing-om on 2016-11-12
titanic1955; Hey;

Let's back up to square 1, so we know what we are dealing with and where.

Boot up a liveUSB(DVD) and post back the outputs - between code tags - of terminal commands:
```

sudo fdisk -lu # because this is a msdos partitioning
sudo blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And which hard drive is set as 1st boot priority in bios ?

Makes sense to me to try and boot the system from the grub prompt - properly instructed - and then see where we go from this attempt.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by titanic1955 on 2016-11-13
Hi Bashing-om

> **Bashing-om said:**
> titanic1955; Hey;

Let's back up to square 1, so we know what we are dealing with and where.

Boot up a liveUSB(DVD) and post back the outputs - between code tags - of terminal commands:
```

sudo fdisk -lu # because this is a msdos partitioning
sudo blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And which hard drive is set as 1st boot priority in bios ?

Makes sense to me to try and boot the system from the grub prompt - properly instructed - and then see where we go from this attempt.[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]


[B]sudo fdisk -lu
[/B]
is

______________________________________________________________________

**Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors**
**Units: sectors of 1 * 512 = 512 bytes**
**Sector size (logical/physical): 512 bytes / 512 bytes**
**I/O size (minimum/optimal): 512 bytes / 512 bytes**
**Disklabel type: dos**
**Disk identifier: 0xb95f5cc5**

**Device     Boot Start       End   Sectors   Size Id Type**
**/dev/sda1        2048 625141759 625139712 298.1G 83 Linux**


**Disk /dev/sdb: 256.2 GiB, 275064201216 bytes, 537234768 sectors**
**Units: sectors of 1 * 512 = 512 bytes**
**Sector size (logical/physical): 512 bytes / 512 bytes**
**I/O size (minimum/optimal): 512 bytes / 512 bytes**
**Disklabel type: dos**
**Disk identifier: 0x68a65533**

**Device     Boot     Start       End   Sectors   Size Id Type**
**/dev/sdb1  *         2048 520458239 520456192 248.2G 83 Linux**
**/dev/sdb2       520460286 537233407  16773122     8G  5 Extended**
**/dev/sdb5       520460288 537233407  16773120     8G 82 Linux swap / Solaris**




**Disk /dev/sdc: 14.3 GiB, 15376000000 bytes, 30031250 sectors**
**Units: sectors of 1 * 512 = 512 bytes**
**Sector size (logical/physical): 512 bytes / 512 bytes**
**I/O size (minimum/optimal): 512 bytes / 512 bytes**
**Disklabel type: dos**
**Disk identifier: 0x0008e636**

**Device     Boot Start      End  Sectors  Size Id Type**
**/dev/sdc1  *     2048 30023679 30021632 14.3G  b W95 FAT32**


**Disk /dev/sdd: 3.8 GiB, 4059561984 bytes, 7928832 sectors**
**Units: sectors of 1 * 512 = 512 bytes**
**Sector size (logical/physical): 512 bytes / 512 bytes**
**I/O size (minimum/optimal): 512 bytes / 512 bytes**
**Disklabel type: dos**
**Disk identifier: 0xe28dce7c**

**Device     Boot Start     End Sectors  Size Id Type**
[B]/dev/sdd1  *      128 7928831 7928704  3.8G  b W95 FAT32

_______________________________________________________________________________________________________________

sudo blkid
[/B]
is

**/dev/sda1: UUID="70477080-4d48-4098-a2c5-b6f767195aff" TYPE="ext4" PARTUUID="b95f5cc5-01"**
**/dev/sdb1: UUID="7af42550-7553-4dd2-8aaf-e6610ea7bc43" TYPE="ext4" PARTUUID="68a65533-01"**
[B]/dev/sdc1: LABEL="USB-Stick" UUID="01AC-1080" TYPE="vfat" PARTUUID="0008e636-01"

_______________________________________________________________________________________________________________
[/B]
I **USUALLY** have the **System drive** &#8203; set as **1st boot priority** in bios ?
Sometimes I leave it as DVD.

---

### Post by Bashing-om on 2016-11-13
titanic1955; Well ..

that "> 
 System drive &#8203; set as 1st boot priority in bios ?

as you say sda is "empty" would then be sdb for the installed operating system.
Now if grub's config files are inplace and consistent, then:
```

linux (hd0,msdos1)/vmlinuz root=/dev/sdb1 ro
initrd (hd0,msdos1)/initrd.img
boot

```
"hd0" because I do expect that grub will see the booting hard drive as hd0 .
"msdos1" because the root of the operating system is installed onto that 1st partition of the sdb drive .

verify that hd0 is that booting drive: From the grub >  prompt ;
```

ls -al
ls -al (hd0,msdos1)/boot/grub/grub.cfg
search -f /vmlinuz
search -f /sbin/init

```

If it fails to boot from grub, well we find out why.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by wildmanne39 on 2016-11-13
@titanic1955 please read post four and edit your posts accordingly.
Thanks

---

### Post by titanic1955 on 2016-11-14
Hi Bashing-om
> **Bashing-om said:**
> titanic1955; Well ..


```

linux (hd0,msdos1)/vmlinuz root=/dev/sdb1 ro
initrd (hd0,msdos1)/initrd.img
boot

```

"hd0" because I do expect that grub will see the booting hard drive as hd0 .
"msdos1" because the root of the operating system is installed onto that 1st partition of the sdb drive .[INDENT][INDENT]
[/INDENT]
[/INDENT]


[B][SIZE=3]IT WORKED ! ![/SIZE]

[/B]
> **Bashing-om said:**
> titanic1955; Well ..

```

ls -al
ls -al (hd0,msdos1)/boot/grub/grub.cfg
search -f /vmlinuz
search -f /sbin/init

```[INDENT][INDENT]
[/INDENT]
[/INDENT]


from that I got:

**Partition hd0**:              no known file system
**Partition hd0,msdos5**: no known file system
**Partition hd0,msdos1**: file system  ext4
**Partition hd1,msdos1**: file system  ext4


Thanks for your patience with me      :P:guitar:

---

### Post by titanic1955 on 2016-11-14
> **Wild Man said:**
> @titanic1955 please read post four and edit your posts accordingly.
Thanks

Sorry, I didn't notice the thread had a second page. :oops:

---

### Post by Bashing-om on 2016-11-14
titanic1955; Great !

Glad ya got it fingered out .
Me, I bet I do not ever get grub all figured out .. but I keep on keep'n on at it .

If this matter is now concluded to your satisfaction:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]and we have fun elsewhere
[/INDENT][/INDENT]

---

