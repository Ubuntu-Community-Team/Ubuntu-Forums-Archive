---
title: "Ubuntu can't mount HD on crashed windows 8.1 laptop?"
date: 2014-10-12
forum: New to Ubuntu
---

### Post by jim_simmons on 2014-10-12
I have a laptop with windows 8.1 installed and it crashed and won't  start up again. I want to back up some files before I reinstall 8.1 so I  started the laptop with a Ubuntu on a USB stick. Unfortunately, from  what I've read, ubuntu is prevented from mounting the hard drive because  Win 8.1 doesnt' fully shut down but goes into hibernation and the fix  for this is to go into the windows settings and change it to fully shut  down. Well, if I can't start windows, I can't change that... does anyone  have another way or a work-around for this problem so I can mount my  windows partition with ubuntu?

---

### Post by sotiris2 on 2014-10-13
If you only want to recover files (and not write to disk) try mounting it read only try the following in a terminal.
First find out which partition is your partition as in sda#.```
lsblk
``` It will partitions on your system, you should be able to identify the windows partition by size. It's name will be sda# where # is a number. it may also be sdb# or sdc# but that's kind of unlikely (sdb will probably be your usb stick)
```
sudo mkdir /mnt/win
sudo mount -o ro /dev/sda# /mnt/win
sudo nautilus /mnt/win
```
Put one line in at a time (copy paste them, via selecting them here and middle clicking on terminal) and the first line will sudo will ask for your password: You will not see anything as you type (no *** or ###) but it is working, just type it in and press enter. 

1st line makes a directory, 2nd mounts the partition in read only mode (which it's supposed not to trigger an error for hibernated partitions) to that directory, and the third one will open up the files browser so you can copy your stuff (remember you can't write to it.)

If the contents are wrong, you probably picked the wrong partition. No worries do ```
sudo umount /dev/sda#
``` with the same sda# as before and then run the second line with a different sda#.

---

### Post by jim_simmons on 2014-10-15
Thank you. This worked perfectly. Just a note, my hard drive was Sdb5 -- not sda but I'm sure that's not a big deal. Anyway, now that I backed up what I needed to back up from my hard drive. Now, do you know if I can re-install windows from the recovery D drive after I start it up with Ubuntu on the flash drive?

---

### Post by sudodus on 2014-10-15
When you mount a partition read-only, nothing will be written it it so it will not be damaged. And partitions that are not mounted are not touched at all. If the recovery drive was healthy it is still healthy and should be possible to use. I think you should boot directly into the Windows recovery system (maybe via grub if you have a dual boot system, but not via Ubuntu).

-o-

You will get better tips how to use 'Windows recovery', if you ask at a Windows specific forum.

---

### Post by Mark Phelps on 2014-10-15
Windows 8 has both a Refresh and a Reset option.  To find out the details of both, and to decide which best to use, you should check in with the Windows 8 forum: [http://www.eightforums.com]("http://www.eightforums.com").

---

