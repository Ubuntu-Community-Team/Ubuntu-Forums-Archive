---
title: "seize issues"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by GeoffNZ on 2013-02-01
Hi folks,

I've got 12.04 32 bit running dual with W7 on my Thinkpad T500. It has the gnome shell desktop.

While downloading torrent file via qbittorrent i ran out out memory (yes Wubi install - Now I realise the limitations of this method!) and qbittorent locked up, then everything froze. 

Restart gets me to login fine, then it locks up. Frozen mouse and only wallpaper visible - no top bar or other icons. Can restart via REISUB and tried a few of the safe mode options but no change.

I can open a terminal window on the frozen desktop but unsure what commands to execute (did look at a few lists but no wiser)

Anything I can do? Or is it a case of a reinstall (and a bigger partition)?

Thanks,

Geoff

---

### Post by d4m1r on 2013-02-02
Do you have a lot of stuff saved within the WUBI install? if I were you, I'd access the files by navigating the disk under Windows 7, the uninstall WUBI and duel boot the laptop instead for better stability + performance.

---

### Post by GeoffNZ on 2013-02-02
> **d4m1r said:**
> Do you have a lot of stuff saved within the WUBI install? if I were you, I'd access the files by navigating the disk under Windows 7, the uninstall WUBI and duel boot the laptop instead for better stability + performance.


Hi, thanks for replying. Yes I imagine the file is full. I had no idea you could access it from W7, but it makes sense if it's just another folder/file. ;)

You suggest uninstall WUBI and duel boot. How do I go about this? Reinstall off a disk? Or will uninstalling WUBI achieve this?

Geoff

---

### Post by bcbc on 2013-02-02
You can get read only access from windows with the tool from [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

You can resize the root.disk from a Live CD as described here: [https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)

If you uninstall/reinstall Wubi your existing install will be erased completely.

---

### Post by GeoffNZ on 2013-02-02
Thanks!  The ext2read tool wasn't very user friendly but I bumbled about and managed to copy everything over into W7 - and the downloaded stuff still works :p (partner very happy to continue watching Breaking Bad ;) )

Still can't get into ubuntu though, so while your resize idea looks interesting, I wonder if it will just mean I have more storage on a system I can't access.

So still looking for advice to restore 12.04 - but now that I have my data I will move to reinstall in a few days if no more advice is offered. 

Thanks again.

Geoff

---

### Post by bcbc on 2013-02-02
I loved breaking bad - watched it on Netflix. And was glad when I finally finished because I became addicted (meth will do that to you I guess)

Yes there's no guarantee it will work following a resize, however, it takes - like a couple of minutes (the resize itself is seconds, but you have to type in the commands) - and if the only reason it's not booting is due to space, then it should work.

Another benefit is that you can still switch to a normal dual boot and keep all your settings/data by [migrating]("https://help.ubuntu.com/community/MigrateWubi"). But I wouldn't recommend that unless you know the wubi is booting properly.

Anyway - if you have your data backed up that's the important bit.

---

### Post by bcbc on 2013-02-02
PS if you boot a live USB/DVD, you can mount the root.disk and delete files to make space. That's another option.

You need to know which partition it's on, but assuming /dev/sda3, you would enter:

```
sudo mkdir /media/win
sudo mount /dev/sda3 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```

Then open the file browser to delete stuff:
```
nautilus /mnt/home
```

You probably need at least 500 MB free for a root.disk to boot.

---

### Post by GeoffNZ on 2013-02-06
Hi, I'm keen to give resizing WUBI a try but not sure how to install it when I can only access the terminal - it needs downloading and extracting. Are there commands to install it?

Thanks,

Geoff

---

### Post by bcbc on 2013-02-06
That resize instructions I linked to is supposed to be run from a live CD. There's another link to a script for duplicating the disk from within Wubi but I wouldn't try to run that if you're short on space.

If you're at a terminal you can also free up some space as described here [http://askubuntu.com/a/107476/14916](http://askubuntu.com/a/107476/14916)

(Obviously just do the ones from terminal - auto-remove, autoclean, uninstall old kernels etc.)

---

### Post by GeoffNZ on 2013-02-08
Hi,

I powered up to look into your advice re cleaning up the crap but ran into this message:

Try (hd0,0): NTFS5: 

Okay, so maybe this is a result of using the read tool?

So, I figured that was enough farting about - lets do a fresh install. 

Downloaded to a USB and installed (although it only gave me a WUBI option when I thought you could take another option - but I  upped the GB amount so not too worried).

On reboot it gave me the same message:

Try (hd0,0): NTFS5:

Hard kill required.

Back to W7!

Anyone know what has happened??

Thanks,

Geoff.

---

### Post by bcbc on 2013-02-08
That part is all grub4dos. Wubi boots via grub4dos - two files: wubildr.mbr and wubildr.

When you see the message Try(hd0,0) that's wubildr.mbr (think of it as a bootloader) looking for wubildr in the root of the first partition /dev/sda1. 

Wubildr.mbr is tiny as are all bootloaders so it needs to load it's 'second stage' that has the code to loop mount the root.disk and present the grub menu - and boot the wubi install.

Anyway that's a lot of mumbo jumbo, but the point is that grub4dos is running, and it's looking for a file on the NTFS partition - and apparently its taking a long time. This has nothing to do with the problems you were having and nothing likely to do with the readonly tool you used. More likely something funny on the NTFS partition.  I've no idea why it worked fine before and suddenly stopped working (or how long you waited before rebooting - i.e. is it really hung up or just slow). 

Maybe it's time to ditch Wubi and do a normal dual boot.

---

### Post by GeoffNZ on 2013-02-09
Yep i  agree.

But I've been trying all fecking afternoon - I get stuck on the whole partition thing and have had no luck finding a simple explanation...

Why oh why can it not just do it itself??

Which partition has W7 on it? The big one? Why do all the guides show a 'free space' partition but mine doesn't? 

I realise that this is now off-topic, but can someone please direct me to a user-friendly guide?

thanks,

Geoff

---

### Post by bcbc on 2013-02-09
The free space is what you make by splitting your windows partition. Assuming you don't already have 4 primary partitions (some HP computers come like that) it's not too complex.

In fact, the recommended way is to let Windows 7 split itself. Here's how: [http://technet.microsoft.com/en-us/magazine/gg309169.aspx](http://technet.microsoft.com/en-us/magazine/gg309169.aspx)

Basically you select C: and shrink it and what you get left with is the smaller C: and a free unpartitioned space. 

You could also let the Ubuntu installer do it automatically, but some people have reported that Windows may require a repair CD to work afterwards. You should make a repair CD/USB beforehand to be safe whichever method you choose.

If you want help, post a picture of your partitions from the disk management console.

---

### Post by GeoffNZ on 2013-02-09
Awesome.

Shrunk drive C by 50 gig (very easy) and let the installer do the rest. 12.04 happily installed (although it won't save my wallpaper) on 50gig partition so we shouldn't have any space issues!

Season 5 of Breaking Bad is now down and a day on the couch is planned :popcorn:...

...dedicated to the ubuntu community!

Thank you!!

(should I mark this as solved? Cos it wasn't really eh?)

---

### Post by bcbc on 2013-02-09
Great to hear! You don't need to mark it as solved - that's up to you.

---

