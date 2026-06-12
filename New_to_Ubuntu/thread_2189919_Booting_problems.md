---
title: "Booting problems"
date: 2013-11-24
forum: New to Ubuntu
---

### Post by bencouve on 2013-11-24
Hello experts!!

I am having difficulty booting my laptop, it appears to hang. It is connected to an external monitor as the screen is broken but this is not a problem. I can boot from usb key and once booted from here I can see the old files with the browser. They appear under Devices and 284GB.

If I cd to /media from termial I see a e08<long hex number> and can cd to that and bingo all my files are there.

I am sure that someone will be able to advise how to recover my system so that it boots. 

Did have a similar problem before and have tried a few things but to no avail.

Thanks in advance for your help.

---

### Post by Bashing-om on 2013-11-24
bencouvel Hello;

Is your USB key the same version as what is installed onto the hard drive ?
Perhaps we can (re-)install grub to the hard drive, see what results ?

[INDENT][INDENT]hey, it is a thought
[/INDENT][/INDENT]

---

### Post by bencouve on 2013-11-25
Hello [**[COLOR=#000000]Bashing-om[/COLOR]**]("http://ubuntuforums.org/member.php?u=1111508"),

Thanks for your comment. I think it is versino 12.04 on usb and I may have upgraded my laptop verstion to 13... or so, can't actually remember. Did the install originally from the usb though. I am open to suggestions, and it is much appreciated.

---

### Post by Bashing-om on 2013-11-25
bencouve; Hello ;

I am not familiar with the liveUSB, on a liveDVD there is a boot options screen and one of those options is to boot from hard drive.

Try this and advise on results:
Boot the liveUSB, soon as bios screen clears depress and hold the shift key -> language screen; escape key to accept the default -> Boot options screen.

Do you have the option "boot from hard disk" on that liveUSB ? What results when you choose that boot option ?

Might also run a file system check/repair from that liveUSB (the file system must not be mounted when a file system check is run, hence from the liveUSB)from "try ubuntu" -> terminal;
Terminal codes:
```

sudo e2fsck -C0 -p -f -v /dev/sda1

``` I have had success in recovering the boot code using this method.
If we are to (re-)install grub from the liveUSB, we must use the same versions in each instance.

Looks to me like it is but a matter of restoring the boot code.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by bencouve on 2013-11-25
Hi Bashing-om,

I have tried the code supplied. Was hopeful that it may work but unfortunatley it has not. 

I need to find out how to check the installed version. If you know how to do this then let me now if there is a file I can look into. Will re-search this now.

Thanks for your help.

---

### Post by Bashing-om on 2013-11-25
bencouve; Well,

At least it was worth a try.
One way to determine what version is installed is to see what kernels you have installed - if this is a standard install and you have not gotten exotic with installing "upstream" kernels.
Boot the liveUSB -> "try ubuntu" ->Terminal;

Mount the installed operating system from the liveUSB:
```

sudo fdisk -lu
sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work
ls -la /mnt/work/boot
sudo umount /mnt/work

```
This is "assuming" that ubuntu is installed onto that 1st hard drive (sda) and that the "root" file system was installed onto that 1st partition.
The command "fdisk" will tell what the partitioning is. If there is doubt, show me the output of the "fdisk" command so I am able to verify and adjust the "mount" command.

This procedure will tell us the kernels you have in the installed system. With that info we can cross reference to the version of the operating system.
That known, burn an .iso image to DVD (what I am accustomed to ) and from that liveDVD (RE-)install grub to the install operating system.


[INDENT][INDENT]sounds like a plan to me
[/INDENT][/INDENT]

---

### Post by bencouve on 2013-11-26
Bashing-om Bonjour,

Here is the output

total 113288
drwxr-xr-x  3 root root     4096 May 23  2013 .
drwxr-xr-x 28 root root     4096 Nov 25 23:25 ..
-rw-r--r--  1 root root   791023 Apr 11  2012 abi-3.2.0-23-generic
-rw-r--r--  1 root root   791132 May 24  2012 abi-3.2.0-25-generic
-rw-r--r--  1 root root   792532 Sep 26  2012 abi-3.2.0-32-generic
-rw-r--r--  1 root root   792830 Feb 19  2013 abi-3.2.0-38-generic
-rw-r--r--  1 root root   852490 May 14  2013 abi-3.5.0-30-generic
-rw-r--r--  1 root root   140279 Apr 11  2012 config-3.2.0-23-generic
-rw-r--r--  1 root root   140407 May 24  2012 config-3.2.0-25-generic
-rw-r--r--  1 root root   140488 Sep 26  2012 config-3.2.0-32-generic
-rw-r--r--  1 root root   140488 Feb 19  2013 config-3.2.0-38-generic
-rw-r--r--  1 root root   148096 May 14  2013 config-3.5.0-30-generic
drwxr-xr-x  3 root root    12288 May 23  2013 grub
-rw-r--r--  1 root root 14164815 Jun 22  2012 initrd.img-3.2.0-23-generic
-rw-r--r--  1 root root 14170758 Oct 14  2012 initrd.img-3.2.0-25-generic
-rw-r--r--  1 root root 14204552 Mar  1  2013 initrd.img-3.2.0-32-generic
-rw-r--r--  1 root root 13537705 May 23  2013 initrd.img-3.2.0-38-generic
-rw-r--r--  1 root root 15310544 May 23  2013 initrd.img-3.5.0-30-generic
-rw-r--r--  1 root root   176764 Jan  3  2013 memtest86+.bin
-rw-r--r--  1 root root   178944 Jan  3  2013 memtest86+_multiboot.bin
-rw-------  1 root root  2884358 Apr 11  2012 System.map-3.2.0-23-generic
-rw-------  1 root root  2886695 May 24  2012 System.map-3.2.0-25-generic
-rw-------  1 root root  2884076 Sep 26  2012 System.map-3.2.0-32-generic
-rw-------  1 root root  2887333 Feb 19  2013 System.map-3.2.0-38-generic
-rw-------  1 root root  2901505 May 14  2013 System.map-3.5.0-30-generic
-rw-------  1 root root  4965840 Apr 11  2012 vmlinuz-3.2.0-23-generic
-rw-------  1 root root  4969488 May 24  2012 vmlinuz-3.2.0-25-generic
-rw-------  1 root root  4966768 Sep 26  2012 vmlinuz-3.2.0-32-generic
-rw-------  1 root root  4968592 Feb 19  2013 vmlinuz-3.2.0-38-generic
-rw-------  1 root root  5130128 May 14  2013 vmlinuz-3.5.0-30-generic

My only concern is creating the iso. DVD as I had created a few but non worked. 

Let me know what you think and hanks a lot for all this.

---

### Post by fantab on 2013-11-26
Try **[Boot-Repair ]("https://help.ubuntu.com/community/Boot-Repair")**tool from Ubuntu DVD/USB. Create '**BootInfo Summary**', note the LINK it creates and post it here. That should give us a good idea of what is going on.

---

### Post by bencouve on 2013-11-26
Perfect!!!

I would like to thank you both for your comments on this ticket. It is very much appreciated. Brilliant man!!!!

If you want to check the link then here it is

[http://paste.ubuntu.com/6479155](http://paste.ubuntu.com/6479155)

I have only booted the system so far so am assuming that all is ok.

Thanks again.

P.s. I had my external hard drive connected when running the repair and heard it ticking away (was going to backup my data but decided to just go ahead - silly I know). I see the report appears to be on the external drive of 320 GB. My laptop has booted with the external hard drive disconnected so hope all is ok. Also, just upgraded to 13.04, will see how that goes

---

### Post by fantab on 2013-11-26
I am glad that you could fix the boot.

A suggestion:
> parted -l:

Model: ATA Hitachi HTS72503 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  284GB  284GB   primary   ext4
3      284GB   305GB  21.0GB  primary   ext3
4      305GB   316GB  10.5GB  primary   linux-swap(v1)
2      316GB   320GB  4192MB  extended
5      316GB   320GB  4192MB  logical   linux-swap(v1)
You have two swap partitions, you only need ONE. Not that it matters but the 2 swap is a waste of space. 10.5Gb to swap is again bit much, 2-4Gb should be good.
Later when you upgrade to ubuntu do a fresh install, lets say in April 2014, you can Delete the the partions 2 and 5. Shrink partition 4 to 5Gb and add the remaining space of 5.5Gb to Partition 3.

Good Luck.

Mark the thread as 'Solved' using Thread Tools.

---

### Post by Bashing-om on 2013-11-26
^ What fantab said ! Good deal .

---

