---
title: "Problems trying to reformat, rename external HDD"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by EssexEagle on 2012-08-25
I have a Seagate Expansion Drive (1TB) which I can mount on my Kubuntu laptop.  It's formatted as NTFS but I want to reformat it using GParted.  However, GParted gives me a warning: "Unable to find mount point".  According to the following thread, this can be caused by having spaces in the mount point of the HDD: [http://gparted-forum.surf4.info/viewtopic.php?id=13431](http://gparted-forum.surf4.info/viewtopic.php?id=13431)

I do indeed have spaces in the mount point:
```
$ cat /proc/mounts
<snip>
/dev/sdb1 /media/Seagate\040Expansion\040Drive fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 0 0
```

According to the thread to which I linked above, this can be solved by removing spaces from the device label name (presumably the directory which is created under /media is automatically named after the device label).  So I want to rename the device label from "Seagate Expansion Drive" to just "Seagate".  I tried to use mlabel to do this.  I added the line
```
drive s: file="/dev/sdb1"
```
to /etc/mtools.conf but mlabel does not work:
```
$ sudo mlabel -s s:
Bad media types ee/f8, probably non-MSDOS disk
Cannot initialize 'S:'
mlabel: Cannot initialize drive
```

Can someone suggest how to get mlabel to work (or else suggest a better way of doing this, if there is one)?

Thanks!

---

### Post by Bashing-om on 2012-08-25
--eagle

 hi! 
    Try this: disk utility 
my system ...system=>administration=>disk utility //
In disk utility choose the device you want to change the label on, and choose "Edit Filesystem Label" 

[INDENT]hth <==BDQ

[/INDENT]

---

### Post by EssexEagle on 2012-08-25
> **Bashing-om said:**
> --eagle

 hi! 
    Try this: disk utility 
my system ...system=>administration=>disk utility //
In disk utility choose the device you want to change the label on, and choose "Edit Filesystem Label" 

[INDENT]hth <==BDQ

[/INDENT]

Hi,

Thanks for your reply.  I'm running KDE not Gnome, but I installed the gnome-disk-utility package.  I don't see an "Edit Filesystem Label" button anywhere (see screen shot)...

---

### Post by Miljet on 2012-08-25
It's right there, the last option.  Edit partition - change partition type, label and flags.

---

### Post by EssexEagle on 2012-08-25
> **Miljet said:**
> It's right there, the last option.  Edit partition - change partition type, label and flags.

LOL, I was clearly being a bit thick. :o

But still, I can't change the label name - I get a dialog box but "Partition Label" is blank, greyed out, and I can't enter any text into it.


EDIT: Actually, do I want to be altering the *partition* label at all?  Shouldn't I be editing the label for the entire device?

---

### Post by Wim Sturkenboom on 2012-08-25
Why not use mkfs.ntfs in a terminal? Read *man mkfs.ntfs*

I've never done ntfs this way, but definitely works for ext2.

```

sudo mkfs.ntfs /dev/sdX

```
where X is the device

---

### Post by bodhi.zazen on 2012-08-26
```
mkfs.ntfs -L <new_label_without_spaces>
```

---

### Post by EssexEagle on 2012-08-26
Thanks for all your advice :)  I'm going away for a couple of days and will have a look at what you've suggested when I'm back.

---

### Post by EssexEagle on 2012-08-29
Okay, so as I wrote in my original post I was trying to change the device label just so that I could get GParted to reformat the drive for me.  Thanks for suggesting the mkfs.ntfs command.  In fact I just used mkfs.ext3 which allowed me both to reformat to ext3 and rename the drive in one go.

[Note to anyone reading this in the future:
```
sudo mkfs.ext3 -L *new_device_label* /dev/sdX
```
will reformat the drive, so DON'T do this if you just want to rename it without losing the data that's on it.  In my case the drive was brand new and I wanted to reformat anyway.]

---

### Post by EssexEagle on 2012-08-29
Also, in case it's useful to anyone else who's new to this stuff, like me...

I found that the drive mounted with root ownership and was read-only to anyone but root.  You can change this by changing the permissions and ownership of the mount point (with the drive mounted):

```

$ sudo chown *my_user_name* /media/Seagate
$ chgrp *my_group* /media/Seagate
$ chmod 777 /media/Seagate

```

where /media/Seagate is the path to the mount point.

---

### Post by Wim Sturkenboom on 2012-08-30
> **EssexEagle said:**
> 
[Note to anyone reading this in the future:
```
sudo mkfs.ext3 -L *new_device_label* /dev/sdX
```
will reformat the drive, so DON'T do this if you just want to rename it without losing the data that's on it.  In my case the drive was brand new and I wanted to reformat anyway.]

See [man ntfslabel](http://linux.die.net/man/8/ntfslabel)

Reading the 'see also' sections of man pages helps :D
Found via [man mkfs.ntfs](http://linux.die.net/man/8/mkfs.ntfs)->[man ntfsprogs](http://linux.die.net/man/8/ntfsprogs)->man ntfslabel

---

