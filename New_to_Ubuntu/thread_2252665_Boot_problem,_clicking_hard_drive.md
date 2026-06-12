---
title: "Boot problem, clicking hard drive"
date: 2014-11-13
forum: New to Ubuntu
---

### Post by Greg Mueller on 2014-11-13
Running 12.04 ubuntu with KDE desktop normally, but also have Kubuntu 14.04 installed in a partion.

Last night I shut down and everything was normal. I didn't install anything and there were no issues. 
This morning when I went to boot the grub normally gives me the 10 second count down and then auto boots to 12.04
Today, no count down
Hit return and the hard drive just clicked at me about once a second
Tried a reboot and was able to change selections and boot in to 14.04

Eventually booted off a 14.04 dvd and ran Grub Boot repair.
It said it worked, so I pulled the dvd and tried to boot.
It went in to the one second click and a bunch of diagnostic stuff worked it's way up the screen

Now it is at a black screen with **Ubuntu** in the middle with white dots underneath it which turn red from left to right and then turn white again.

I was thinking the hard drive might be dieing but it boots ok to 14.04



**I really need some help**

G

---

### Post by buzzingrobot on 2014-11-13
If the drive is producing audible clicks, that could very well mean its failing. I've only had one drive fail, in a Mac, and it behaved similarly.

Whatever is going on, it's a good time to have your backups in order.

---

### Post by Bashing-om on 2014-11-13
Greg Mueller; Hi !

Grub's booting with no time out counter is indicative of a problem booting the time before .

What we can do is to (re-)install grub and in that process IF there is a problem get some hints on where the problem may lay.

Boot the liveDVD and post the outputs of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
-if partitions are not labeled, advise what partition is what.

Advise of which operating system you want as the primary, as only 1 grub can control the booting process for all installed operating systems .
With the provided info, we will know how and where to install grub - see what happens.

[INDENT][INDENT][INDENT]it is all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by Greg Mueller on 2014-11-13
Here they are and thanks



kubuntu@kubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eabc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       16065   136423979    68203957+  83  Linux
/dev/sda2       486064126   490233855     2084865    5  Extended
/dev/sda3       136665088   188813311    26074112   83  Linux
/dev/sda5       486064128   490233855     2084864   82  Linux swap / Solaris

Partition table entries are not in disk order






kubuntu@kubuntu:~$ sudo parted -l
Model: ATA Maxtor 7Y250M0 (scsi)
Disk /dev/sda: 251GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      8225kB  69.8GB  69.8GB  primary   ext4            boot
 3      70.0GB  96.7GB  26.7GB  primary   ext4
 2      249GB   251GB   2135MB  extended
 5      249GB   251GB   2135MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

---

### Post by Bashing-om on 2014-11-13
Greg Mueller; Hey;

Regret the delay in responding, I do get side tracked .

OK, what is where ?
'sda1' is what ? 
'sda3' is what ?

All we know presently is that these partitions are dedicated to "linux". and currently 'sda1' is marked as the booting partition (maybe not what you intend ?). - a separate /home partition (sda3), or is 'sda3' the Kubuntu install ? I can not tell so please advise. Also advise what you desire for that primary operating system by location ( sda1 ??) .

[INDENT][INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by Greg Mueller on 2014-11-13
sda1 is 12.04 ubuntu with kde
sda3 is kubuntu 14.04

I wish to boot 12.04

there's nothing but ubuntu on this hard drive if that is what you are asking?

---

### Post by Bashing-om on 2014-11-13
Greg Mueller; Good 'nuff ;

OK, Let's do this:

Boot the liveDVD of ubuntu 12.04 ! - and we (re-)install grub to 12.04;
Terminal commands:
```

sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```
I do not expect any errors, but if a problem is reported, please note and advise of such.

Reboot and if needed reset the boot priority to the hard drive, continue the boot process and in the grub boot menu select "ubuntu on  (sda1)" to boot.

Boot to desktop -> terminal:
Now run terminal command in the install:
```

sudo update-grub

```

These set ubuntu12.04 as the primary system, and 'grub-update' picks up the (k)ubuntu install .

Reboot once more and tell me ->
[INDENT][INDENT][INDENT]all is finer than a frog's hair
[/INDENT][/INDENT][/INDENT]

---

### Post by Greg Mueller on 2014-11-13
ok
but I'll have to wait to boot with 12.04 as I can't find that disk right at the moment. (search as I may)

I have been using the 14.04 disk

---

### Post by Bashing-om on 2014-11-13
Greg Mueller; Hey, hey.

The grub versions are different between 12.04 and 14.04 is the reason I direct to use the 12.04 liveDVD.
Now, that said, will not hurt to try and see what results installing 14.04's grub, just see if it does work . IF there are problems one can always (re) (re-)install 12.04's grub. I am sure the obverse is not a good thing (12.04 installed to 14.04 operating system ) .

But but do bear in mind would be a very nice thing to have on hand the liveDVD of 12.04 .

[INDENT][INDENT]we can try and see
[/INDENT][/INDENT]

---

### Post by Greg Mueller on 2014-11-13
Found it
Got to line 2

sudo grub-install --boot-directory=/mnt /dev/sda

and it gave me a bunch of syntax choices

---

### Post by Greg Mueller on 2014-11-13
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt 

ubuntu@ubuntu:~$ sudo grub-install --boot-directory/mnt /dev/sda 
Unrecognized option `--boot-directory/mnt' 
Usage: grub-install [OPTION] install_device 
Install GRUB on your drive. 

  -h, --help              print this message and exit 
  -v, --version           print the version information and exit 
  --modules=MODULES       pre-load specified modules MODULES 
  --boot-directory=DIR    install GRUB images under the directory DIR/grub 
                          instead of the /boot/grub directory 
  --grub-setup=FILE       use FILE as grub-setup 
  --grub-mkimage=FILE     use FILE as grub-mkimage 
  --grub-mkrelpath=FILE   use FILE as grub-mkrelpath 
  --grub-mkdevicemap=FILE use FILE as grub-mkdevicemap 
  --grub-probe=FILE       use FILE as grub-probe 
  --no-floppy             do not probe any floppy drive 
  --allow-floppy          Make the drive also bootable as floppy 
                          (default for fdX devices). May break on some BIOSes. 
  --recheck               probe a device map even if it already exists 
  --force                 install even if problems are detected 
  --disk-module=MODULE    disk module to use 

INSTALL_DEVICE can be a GRUB device name or a system device filename. 

grub-install copies GRUB images into /boot/grub, and uses grub-setup 
to install grub into the boot sector. 

Report bugs to <bug-grub@gnu.org>. 
ubuntu@ubuntu:~$

---

### Post by Bashing-om on 2014-11-13
Greg Mueller; Humm ??

Try again:
the correct syntax IS:
```

sudo grub-install --boot-directory=/mnt/boot /dev/sda

``` that silly little '=' between directory and /mnt is meaningful.
copy and paste for best results.

let's see how it goes, now

[INDENT][INDENT]because we can do this
[/INDENT][/INDENT]

---

### Post by Greg Mueller on 2014-11-13
That made a difference.
It took all the terminal commands and I shut it down to reboot.
It came up with the grub and I selected the default, now there's a bunch of check stuff scrolling up the screen which steps with each click
Something about "unable to read itable block"

---

### Post by Greg Mueller on 2014-11-13
That made a difference.
It took all the terminal commands and I shut it down to reboot.
It came up with the grub and I selected the default, now there's a bunch of check stuff scrolling up the screen which steps with each click
Something about "unable to read itable block"
and now it is just sitting at the "Ubuntu" logo

---

### Post by Greg Mueller on 2014-11-13
Some of the message....

ata4.00: status: { DRDY ERR }
ata4.00: error: { UNC }
end_request: i/o error, dev sea, sector 134235466
EXT4-fs error (device sda1): __ext4_get_inode_loc:3632: inode #4197148: block 16777425: comm 99-footer: unable to read itable block

---

### Post by Greg Mueller on 2014-11-13
I think it's toast

---

### Post by Bashing-om on 2014-11-13
Greg Mueller; Now that is UnGood !

Maybe the hard drive is dying ??
Maybe the file system is messed up ?
Maybe the KDE environment is messing with the unity environment ?

Let's check the hard drive:
From the liveDVD -> dash -> search term "disk utility" :
in the utility choose "SMART" test;

What does the short test reveal ?

IF the disk looks good, then check the file system:
 From the liveDVD:
```

sudo e2fsck -C0 -p -f -v /dev/sda1
##If errors then run:##
sudo e2fsck -f -y -v /dev/sda1

```

IF these are good we start investigating the desk top environments .

[INDENT][INDENT]a process in fault isolation
[/INDENT][/INDENT]

---

### Post by yancek on 2014-11-13
> Hit return and the hard drive just clicked at me about once a second

Based on that comment, the first thing I would suggest is to back up anything you want to keep from that drive while you still can, then you can try getting it to boot.

---

### Post by Bashing-om on 2014-11-13
Greg Mueller; Yuk (maybe) ;

See yancek's last. It is always a good idea to have back ups.

The forgoing is precautionary measures- just to make sure. I have seen where there are ATA errors when grub can not determine the proper root location. If all test are good, then we can try and purge grub and rebuild grub's config files.

What I am saying is it is not hopeless to this time.

[INDENT][INDENT]fault isolation is what we do
[/INDENT][/INDENT]

---

### Post by Greg Mueller on 2014-11-13
I think I will walk away today before some goes flying

---

### Post by Greg Mueller on 2014-11-13
New plan
I found an 80gb hard drive in the back room
I finally got through downloading Kubuntu 12.04.4 and burned it to a disk and am doing a fresh install on the 80gb
When that's done I'll be able to boot from that and then hook up the dieing Maxtor and fish for all my Firefox/Thunderbird/Gnucash etc etc etc files
Not to mention all those pictures
I'll probably need help figuring out where Mozilla hides those things
Tomorrow *IS* another day

---

### Post by Bashing-om on 2014-11-13
Greg Mueller; Ho-Kay;

Where there is a will, there is a way, or so I say.
But to this time is it a certainity that the drive has failed ?

[INDENT][INDENT]more than one way
[/INDENT][/INDENT]

---

### Post by Greg Mueller on 2014-11-13
No not for sure, but I want to get out what I can first and then experiment

---

### Post by Bashing-om on 2014-11-13
Greg Mueller; Hey, outstanding !
> 
 but I want to get out what I can first and then experiment


Like, count me in ! 
I have learned the most when I have broke the most .

[INDENT][INDENT]if it ain't broke,
[INDENT][INDENT][INDENT]ya ain't tweaked it enough
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Greg Mueller on 2014-11-14
New day

I installed ubuntu/kde on the new 80gb hdrive
I boot from that and I can access _all_ of the problem drive.

Is there a way to start Firefox and Thunderbird on the old drive with the terminal on the new drive?
If so I can export all my bookmarks (json) and email stuff.

I've already saved my gnucash files (wahoo)

---

### Post by deadflowr on 2014-11-14
> [COLOR=#000000]Is there a way to start Firefox and Thunderbird on the old drive with the terminal on the new drive?[/COLOR]
[COLOR=#000000]If so I can export all my bookmarks (json) and email stuff.
[/COLOR]

Why don't you copy the profile folders for .mozilla and .thunderbird from the old drive to the new drive?
It should move everything over.

You might need to tinker with ProfileManager
```
firefox -ProfileManager
```
(thunderbird is same changing firefox for thunderbird)

---

### Post by Greg Mueller on 2014-11-14
Yippee
It worked for Thunderbird...now for Firefox

Thank you

---

### Post by Bashing-om on 2014-11-14
Greg Mueller; Hey, hey ;

Lot's of ways to do anything with linux, But, I do believe deadflowr's advise is the better course.
Else one looks at 2 terminals open, and exporting the display to support the GUI applications.

[INDENT][INDENT]not all things are easy
[/INDENT][/INDENT]

---

### Post by Greg Mueller on 2014-11-14
I found a json file that I guess was automatically done the day before the crash for Firefox

Back in business again

I think I will start to do regular backups......

Thanks guys
You're a life saver

---

### Post by Greg Mueller on 2014-11-14
Only thing left is my passwords.
Can't seem to find them

---

