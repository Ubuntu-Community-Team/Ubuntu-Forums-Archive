---
title: "After Installing over Windows need help finding second harddrive"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by JesseMat on 2008-10-10
I just installed xubuntu over my windows xp system. I have two hard drives. I'm brand new to all things linux, but I'm trying to use these forums as best I can. So far, I have ran ```
sudo fdisk -l
``` and this is what I've come back with:
[PHP]
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06690669

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2341    18804051   83  Linux
/dev/sda2            2342        2434      747022+   5  Extended
/dev/sda5            2342        2434      746991   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1023     8217243   55  EZ-Drive[/PHP]

I have tried using the various codes I've gleamed in some forums, so far what I've have done is this:

```
jesse@jesse-desktop:~$ sudo mkdir /mnt/2ndHD && sudo mount /dev/sdb /mnt/2ndHD
mount: you must specify the filesystem type
jesse@jesse-desktop:~$ sudo mkdir /media/2ndHD
jesse@jesse-desktop:~$ sudo getit /etc/fstab
sudo: getit: command not found
jesse@jesse-desktop:~$ sudo mount -t ext3 /dev/hdb /media/2ndHD
[sudo] password for jesse: 
mount: special device /dev/hdb does not exist
jesse@jesse-desktop:~$ sudo mount -t ext3 /dev/hdb1 /media/2ndHD
mount: special device /dev/hdb1 does not exist
jesse@jesse-desktop:~$ sudo mount -t ext3 /dev/hdb /media/2ndHD
mount: special device /dev/hdb does not exist
```

Any and all help would be appreciate, please remember that I'm completely new to this. Thanks.

PS I hope I using the CODE tags correctly

---

### Post by hyper_ch on 2008-10-10
What's other drive exactely?

---

### Post by JesseMat on 2008-10-10
The 80 gig one. The second one listed in the php colored stuff. I'm a little worried cause all of the other examples I saw did not have the Disk identifier as all 00000's.

i'm probably being an idiot. I just don't know how to get to the hard drive.

---

### Post by hyper_ch on 2008-10-10
I was rather referring as to what you used it because it's "EZ-Drive" and not "vfat" or "ntfs"

---

### Post by JesseMat on 2008-10-10
Unfortunately, I'm not sure that I understand what you mean. It was used as extra storage. It has music, movies, and other stuff. I have that feeling that I'm about to look like an idiot in a few seconds :)

---

### Post by hyper_ch on 2008-10-10
so, you have stuff on there that you want to keep?

---

### Post by JesseMat on 2008-10-10
This is where you tell me I can't, right? It's not the end of the world if I can't get anything, most of it is junk.

---

### Post by hyper_ch on 2008-10-10
Well, I don't have a clue what that "EZ-drive" is or how that works or what it's supposed to do...

So if you say you don't need any of that data, then I'd just format that drive with gparted...

However if you want to recover data from it, you'll ahve to find out how ;)

---

### Post by JesseMat on 2008-10-10
Haha. I don't need the space any time soon, and there are a few things I'd like to dig through. You have any suggestions about where to look? Should I open a new thread asking about EZ-drives?

---

### Post by hyper_ch on 2008-10-10
I just found this:

[http://fatooh.org/misc/ez-drive.html](http://fatooh.org/misc/ez-drive.html)

```

Alternatives

You probably don't have to remove EZ-Drive if you don't want to.

As far as I know, EZ-Drive is not ever needed for Linux, but Linux can work with a hard drive that has an EZ-Drive alternate partition table. Add the kernel option "hda=remap" (or hdb, hdc, etc.) to your LILO or GRUB configuration. If you're running Linux 2.6 off such a drive now, you've probably already done this.

As long as you can mount the filesystems with your data, you can always move the data elsewhere, wipe the beginning of the disk, re-create partitions, copy the data back, and recreate your boot record(s). I'm not going to go into how to do that here, but it is a more conservative approach. 

```

So basically

(1) edit grub entry
```

sudo nano /boot/grub/menu.lst

```

(2) find the kernel from which you boot
(it may look something like this: "/vmlinuz-2.6.27-6-generic root=/dev/sda1 ro quiet splash")

(3) add at the end
```

sdb=remap

```

(4) save and close nano

(5) reboot

No clue if that works.. it might render all data useless...

---

### Post by JesseMat on 2008-10-10
Thank you. I'm still trying to get language and logic down. You are the first person I've talked to after downloading linux for the first time. You're advice seems a little more daunting. I may take a break before I plunge into that, but I'll post after I do to report what happens.

---

### Post by Big_Kahunaca on 2008-10-10
Did you try typing "/dev/sdb1" instead of "/dev/hdb" or "/dev/hdb1"?

---

### Post by JesseMat on 2008-10-10
... Wow. I'm an idiot... Or atleast a poor typer/speller. 

I attempted to run > sudo mount -t ext3 /dev/sdb /media/2ndHD (With the correct spelling). This actually got the ball rolling, but it returned this:

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I'm not sure what I should try next.

---

### Post by hyper_ch on 2008-10-10
well, I told you what to do ;)

---

### Post by JesseMat on 2008-10-10
OK. I did what you had previously told be to do. Then I used the same code as above, and still got the same answer. Is that the correct way to try to mount it? Is there an alternative?

---

### Post by hyper_ch on 2008-10-10
might not be... so if you booted with the sdb=... option then run
```

sudo fdisk -l

```

Now you should have a different output if I understood that article correclty...

---

### Post by JesseMat on 2008-10-10
I believe it to be the exact same as before. Just to be safe I also tried running it with sdb1 and got the same error message. The fdisk said:

```
jesse@jesse-desktop:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06690669

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2341    18804051   83  Linux
/dev/sda2            2342        2434      747022+   5  Extended
/dev/sda5            2342        2434      746991   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1023     8217243   55  EZ-Drive

```

---

### Post by hyper_ch on 2008-10-10
what's the output of
```

cat /boot/grub/menu.list

```

---

### Post by JesseMat on 2008-10-10
Aaaah. Hopefully not as bad as it sounds: "cat: /boot/grub/menu.list: No such file or directory"

---

### Post by hyper_ch on 2008-10-10
it's "lst" and not "list" :)

---

### Post by JesseMat on 2008-10-10
I see what I did. When I did the remap before I placed it under the recovery mode kernel. I switched it and am going to reboot. brb

---

### Post by JesseMat on 2008-10-10
Sorry, I had place the remap on the part labeled (recovery) so I switched it and redid the whole thing. Same error message. Cat gives me:
```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2be7d872-4370-4bb6-b1c2-2f676745bfc4 ro quiet splash sdb=remap
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2be7d872-4370-4bb6-b1c2-2f676745bfc4 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

---

### Post by hyper_ch on 2008-10-10
what does
```

sudo fdisk -l

```
return now?

---

### Post by JesseMat on 2008-10-10
Looks the same:
```
jesse@jesse-desktop:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06690669

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2341    18804051   83  Linux
/dev/sda2            2342        2434      747022+   5  Extended
/dev/sda5            2342        2434      746991   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1023     8217243   55  EZ-Drive
```

---

### Post by hyper_ch on 2008-10-10
then I don't know...

---

### Post by JesseMat on 2008-10-10
Is > sudo mount -t ext3 /dev/hdb /media/2ndHD the only way to gain access to the drive?

---

### Post by hyper_ch on 2008-10-10
another option would be to see if gpart can restoare a "proper" partition table... I have some doubts but running it to see what it finds out cant hurt:

```

sudo apt-get install gpart

```

and then

```

sudo gpart /dev/sdb

```
and copy the output here...

---

### Post by JesseMat on 2008-10-10
It ran through everything fine, but the mount didn't work and both fdisk and cat look the same from what I can tell.

---

### Post by m_duck on 2008-10-10
It seems from [http://ubuntuforums.org/showthread.php?t=334794](http://ubuntuforums.org/showthread.php?t=334794) that once you have added the "sdb=remap" to the kernel line of menu.lst, you can mount the drive as ntfs like:
```
sudo mount -t ntfs /dev/sdb1 /mnt/2ndHD
```If you wanted to make it permanent, you must add an entry to the bottom of fstab such as:
```
/dev/sdb1 /mnt/2ndHD ntfs defaults 0 0
```

---

### Post by unutbu on 2008-10-10
JesseMat, there might be a way to circumvent this problem:

To change the partition type:
```

sudo fdisk /dev/sdb
```

Type 'h' to see the commands available to you. This will help you understand the following commands:

Type 't' to change the pratition type
Type 1 to select the first partition
Type 7 for a NTFS partition type or type 83 for a Linux partition type
Type 'w' to write the change to disk

To check that the change was successful, type
```

sudo fdisk -l
```

Now you should see something like

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1023     8217243   **7  HPFS/NTFS**
```

Note that changing the partition type does not in and of itself destroy the data on the partition. The change is reversible. 

**If the EZ-Drive has an NTFS filesystem on it, changing the partition type might be enough to allow Linux to mount the NTFS filesystem using m_duck's instructions above.**

If it doesn't work, try taking out the "remap=sdb" line from /boot/grub/menu.lst.
Reboot. Then try 
```

sudo mount -t ntfs /dev/sdb1 /mnt/2ndHD
```

and/or 
```

sudo mount -t ext3 /dev/sdb1 /mnt/2ndHD
```
again. 

Note that you should try to make the partition type and the filesystem type match. 
So you might have to try these instructions twice if you are unsure of the filesystem type on /dev/sdb1.

If it doesn't work, and you are willing to sacrifice the data on /dev/sdb1, then:

[list]
[*]To reformat /dev/sdb1 with an NTFS filesystem:
```
sudo mkfs.ntfs -v -Q -F /dev/sdb
mkdir /mnt/2ndHD
```
Then use m_duck's instructions to mount the drive and/or to automount the drive at boot.

[*]To reformat /dev/sdb1 with an ext3 filesystem:
```
sudo mke2fs /dev/sdb1
sudo mount /dev/sdb1   # This should be enough to mount an ext3 drive
```
To make it automounted at boot,
```
gksu gedit /etc/fstab
```
Add a line that reads
```

/dev/sdb1 /mnt/2ndHD ext3 defaults 0 0
```

[/list]
Note that in your /etc/fstab you should only have one line that begins with
```

/dev/sdb1

```

---

### Post by JesseMat on 2008-10-11
Thanks for sticking with me :)
I'll show you all what is happening:
```
jesse@jesse-desktop:~$ sudo mount -t ntfs /dev/sdb1 /mnt/2ndHD
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```
I get the same response if I change "sdb1" to "sdb"

```
jesse@jesse-desktop:~$ sudo fdisk /dev/sdb

The number of cylinders for this disk is set to 9729.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
```
I'm not sure if that was expected/part of the problem

I did what unutbu wanted with the partition change. That did work. But when I went back through m_duck's mounting the same thing occurred. When I tried to use linus partion instead, I didn't get as far. I also went through and deleted the sdb=remap and rebooted, still the same.

One question I have is am I only supposed to change the fist partition, or is there a way to go through the whole disk? Also, so I don't have to cycle through all of the possibilities, should I be using 'sdb' or 'sdb1' for most/all of this? And (last thing) I placed the folder '2ndHD' in 'media' is that what I should be using instead of '/mnt/2ndHD'?.. I hate being a noob... I have no need for the extra space on the drive right away, so I would like to hold off on reformatting. 

```
jesse@jesse-desktop:~$ sudo fdisk -l

.
..
...

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1023     8217243    7  HPFS/NTFS
```

---

### Post by unutbu on 2008-10-11
JesseMat, perhaps the EZ-Drive /dev/sdb1 has a Win FAT filesystem on it, rather than an NTFS filesystem. So, perhaps try this:
```

sudo fdisk /dev/sdb
```

(By the way, /dev/sdb refers to the whole drive, /dev/sdb1 refers to the first partition on the drive. When you run fdisk to edit the partition table, the partition table is relevant to the whole drive, so you specify a whole drive like /dev/sdb, never a single partition like /dev/sdb1.)

Type 't' 
Type 1
Type 55    # To make the partition type EZ-Drive
Type 'w' 
```

sudo fdisk -l /dev/sdb
```

The output should look like this:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1023     8217243   55   EZ-Drive
```

Now try to mount the partition with
```

sudo mount -t vfat /dev/sdb1 /media/2ndHD
```

---

### Post by JesseMat on 2008-10-11
I got this error ```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
The closest I get is by partioning it as ntfs, atleast it then tells me: ```
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
jesse@jesse-desktop:/$ sudo fdisk /dev/sdb
```
I'm kind of stumped by this whole thing (though I know nothing so that isn't hard). It sounds like this should be working, I'm kind of at a loss as to what the problem is...

---

### Post by unutbu on 2008-10-11
Does this drive work when connected to a Windows machine? Perhaps you can backup the stuff you wish to keep while in Windows and then reformat...

---

### Post by JesseMat on 2008-10-11
That is definitely on the table. A little bit of a pain since it's internal, but it can be done. I kept hoping that there would be a little trick that would work like magic, but that may need to be my next recourse. 

Thanks everyone for the help. I had been on the outside looking at reviews for Ubuntu, kept thinking that it soundly like the right way to go. I love open source philosophy. I got fed up one day and happened to StumbleUpon (I'm [JesseMat]("http://jessemat.stumbleupon.com/") on SU btw) Xubuntu and rashly decided to make the switch. Even with this hard drive hangup, I have been overjoyed with the results. Particularly, I was deeply impressed by this forum. I can't believe I received this much timely advice for something I didn't pay for.

If anyone has any more options, I'm all open. It may take me a while before I yank the hard drive out. 

Thanks again.

---

