---
title: "[SOLVED] Cannot start X after changes to Grub and fstab"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by gerben1 on 2008-06-29
Hi,

I was following this guide to speed up Ubuntu 8.04:
[http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml)

After step 2 I cannot log into the Xserver anymore...

This is what i did:

(1)```

changed this line in /etc/fstab
UUID=fa8...1e2 / ext3 defaults,errors=remount-ro 0 1
into:
UUID=fa8...1e2 / ext3 defaults,noatime,nodiratime,errors=remount-ro,data=writeback 0 1

```
(2)```

changed these lines in /boot/grub/menu.lst:
#defoptions=quiet splash vga=795
  and
#altoptions=(recovery mode) single
into:
#defoptions=quiet splash vga=795 rootflags=data=writeback
  and
#altoptions=(recovery mode) single rootflags=data=writeback

```
(3)```

sudo update-grub

```

After rebooting I get to a screen with this message:
"Could not start the X server (your graphical environment) due to some internal error. Please contact your system admin etc.")

I can, via ctrl-alt F2, log into tty2 and check things. I tried changing /etc/fstab and /boot/grub/menu.lst back to what they were, but I cannot save the changes. When I try to save I get the error:"Error writing /etc/fstab: Read-only file system".

any ideas on things i could try?

---

### Post by sisco311 on 2008-06-29
try to remount the filesystem:
```
sudo mount -o remount,defaults /dev/sd**XY
```**

---

### Post by gerben1 on 2008-06-29
> **sisco311 said:**
> try to remount the filesystem:
```
sudo mount -o remount,defaults /dev/sd**XY
```**

that gives me this error:
```
Mount: can´t find /dev/hda1 in /etc/fstab or /etc/mtab
```

probably because the partitions are indicated by UUID in fstab now

---

### Post by bumanie on 2008-06-29
To get editable text docs > gksudo gedit /etc/fstab  and > gksudo gedit /boot/grub/menu.lst gksudo gives admin rights gedit is gnome editor.

---

### Post by gerben1 on 2008-06-29
Well, I just read this in the comments on that Guide
([http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml):](http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml):)
```

Hi,
This is a good article, but ..
One important part is missing .. (Must do to avoid crashing)
In Step-2,after tweak one
run the following command --->
sudo tune2fs -o journal_data_writeback /dev/

```

so yeah, that is the step i missed and that is whty i crash.
But how can i now do that step, as i am booting in Read Only mode, automatically?

---

### Post by PmDematagoda on 2008-06-29
> **gerben1 said:**
> Well, I just read this in the comments on that Guide
([http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml):](http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml):)
```

Hi,
This is a good article, but ..
One important part is missing .. (Must do to avoid crashing)
In Step-2,after tweak one
run the following command --->
sudo tune2fs -o journal_data_writeback /dev/

```

so yeah, that is the step i missed and that is whty i crash.
But how can i now do that step, as i am booting in Read Only mode, automatically?

Do you have the Ubuntu Live CD? If so, boot the PC using that and then execute the required commands and see if that fixes it.

---

### Post by gerben1 on 2008-06-29
No, I do not have the live CD as I upgraded from Gutsy Gibbon, but I could download it. Would that work though? I mean if I run that "tune2fs"command will that affect anything on my Hard Disk installation after I have booted from CD? I would assume it will do something to the /dev/ in the loaded filesystem.

---

### Post by dwhitney67 on 2008-06-29
> **bumanie said:**
> To get editable text docs  and  gksudo gives admin rights gedit is gnome editor.
I'm sorry, but I have to point out this is dumbest comment I have ever seen.  Did you not read the OP, or for that matter, the thread title?

No X11 means no Gnome, which in turn means no gedit.

Perhaps using 'vim' would be a better choice.

---

### Post by PmDematagoda on 2008-06-29
> **gerben1 said:**
> No, I do not have the live CD as I upgraded from Gutsy Gibbon, but I could download it. Would that work though? I mean if I run that "tune2fs"command will that affect anything on my Hard Disk installation after I have booted from CD? I would assume it will do something to the /dev/ in the loaded filesystem.

Well, you don't have to get the Ubuntu Live CD exactly, just getting a small Live CD such as Knoppix or Damn Small Linux(or even Puppy Linux) should be enough. About the hard drive, you wouldn't need to mount it, and yes, it shouldn't do anything but change the attributes of the file system, even though you see the path as /dev/, it really means nothing since /dev is dynamic.

---

### Post by dwhitney67 on 2008-06-29
> **gerben1 said:**
> that gives me this error:
```
Mount: can´t find /dev/hda1 in /etc/fstab or /etc/mtab
```

probably because the partitions are indicated by UUID in fstab now

Try this:
```
sudo mount -o remount,defaults -U fa8...1e2   # get the full UUID for the / partition from /etc/fstab
```

---

### Post by gerben1 on 2008-06-29
@PmDematagoda
Ah ok, well i have a puppy linux 4.0 cd here, I will try that. 

I do not totally understand your explanation of what will happen. What I was wondering about was this:
How can the "tune2fs" command change anything in my HardDrive-Ubuntu-Install, when I just run a command that has no notion that there is an OS install on the HD. 

In other words: after I have ran the command in Pupppy linux, when I take out the CD, shutdown the computer and then boot Ubuntu from the hard drive will any of it's settings have changed?

---

### Post by gerben1 on 2008-06-29
> **dwhitney67 said:**
> Try this:
```
sudo mount -o remount,defaults -U fa8...1e2   # get the full UUID for the / partition from /etc/fstab
```

gives me this error:
```

[   405.055346] EXT3-fs: cannot change data mode on remount
mount: / not mounted already, or bad option

```

---

### Post by PmDematagoda on 2008-06-29
> **gerben1 said:**
> @PmDematagoda
Ah ok, well i have a puppy linux 4.0 cd here, I will try that. 

I do not totally understand your explanation of what will happen. What I was wondering about was this:
How can the "tune2fs" command change anything in my HardDrive-Ubuntu-Install, when I just run a command that has no notion that there is an OS install on the HD. 

In other words: after I have ran the command in Pupppy linux, when I take out the CD, shutdown the computer and then boot Ubuntu from the hard drive will any of it's settings have changed?

The only settings which would have changed would be the way the file system works. According to the tune2fs man:-
> DESCRIPTION
       tune2fs allows the  system  administrator  to  adjust  various tunable filesystem parameters on Linux ext2/ext3 filesystems.

---

### Post by gerben1 on 2008-06-29
> **PmDematagoda said:**
> The only settings which would have changed would be the way the file system works. According to the tune2fs man:-

yes, but am I not just changing the puppy linux filesystem then?

---

### Post by PmDematagoda on 2008-06-29
> **gerben1 said:**
> yes, but am I not just changing the puppy linux filesystem then?

No, when Puppy is run as a Live environment, it is on the RAM and isn't ext, you just have to select the proper /dev/path which can be found with:-
```
sudo fdisk -l
```

---

### Post by gerben1 on 2008-06-29
> **PmDematagoda said:**
> No, when Puppy is run as a Live environment, it is on the RAM and isn't ext, you just have to select the proper /dev/path which can be found with:-
```
sudo fdisk -l
```

Aha, that clears things up

so in my case I should have mounted hda1 and than ran:
```

sudo tune2fs -o journal_data_writeback /mounted-media/hda1/dev/
instead of 
sudo tune2fs -o journal_data_writeback /dev/

```
such a reasonable thing to do, no clue why I couldn't have thought of something like that.

Anyways, thanks a lot, I really learned quite a bunch from this.

I chose to just change everything back for now, using the Puppy Linux Live CD:
- booted from the puppy cd, 
- mounted hda1 
- changed the settings in /mounted-media/hda1/etc/fstab and in /mounted-media/hda1/boot/grub/menu.lst back to the default settings. 
All works fine again.

I may try this again some other time, after reading up on tune2fs, doing it the proper way.

---

### Post by PmDematagoda on 2008-06-29
No no, you got it wrong, it's not:-
```
/mounted-media/hda1/dev/
```
it's:-
```
/dev/hda1
```(or might be different in Puppy) 

As I said before, /dev is dynamic and not static.

---

### Post by gerben1 on 2008-06-29
Right, I got it now.

Thanks

---

