---
title: "unable to mount DVD-R recorded in Windows"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by bsmith1051 on 2008-07-30
Near as I can tell, some DVD-Rs that were recorded in Windows have either a newer version of the UDF file-system or have multiple-sessions or have SOMETHING which prevents Linux (not just Ubuntu) from reading them. This seems to be an incredibly frequent problem, I'm surprised I didn't realize it sooner.  And why isn't there a sticky note about it?  Unfortunately, this is just one more massive disappointment for me with the latest Ubuntu; I realize, this problem existed before Hardy but it hadn't affected me until now.

At the very least, does anyone have any idea when this problem(s) will be fixed?

Here's a few links for reference:
- [http://ubuntuforums.org/showthread.php?t=718744](http://ubuntuforums.org/showthread.php?t=718744)
- [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233)
- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/106910](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/106910)
- [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/144242](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/144242)

---

### Post by SunnyRabbiera on 2008-07-30
Unknow, most of this sort of thing is not entirely the fault of linux as certain paries dont like to play nice with linux, especially microsoft,.

---

### Post by bsmith1051 on 2008-07-30
I don't think this has anything to do with Microsoft, as I'm using Nero -- a neutral 3rd party -- to burn my discs under WinXP.

Actually, I checked and my 'problem' discs were all burned using "ISO 9660 + Joliet" which is supposed to be a standard (and it's the default in Nero, both Windows and Linux versions).

---

### Post by SunnyRabbiera on 2008-07-30
Still the possibility was there.

---

### Post by bsmith1051 on 2008-07-30
aagh!  It was a bad DVD drive in my Ubuntu box.  It could successfully read everything **except** DVD-R data discs.

(Now I'm worried about all those discs I burned with it...)

---

### Post by bsmith1051 on 2008-07-31
> **bsmith1051 said:**
> It was a bad DVD drive in my Ubuntu box
scratch that, I'm still having problems even with a new Sony drive.  And I'm having problems with discs recorded by the new drive, too.  So it's probably nothing to do with Windows!

Here's something interesting: I booted 8.04.1 from a flash drive and the DVD drive worked perfectly.  So it's definitely something with the configuration and/or updated drivers on my installed system.

I found that if I specified 'ro' (readonly) in fstab that I could manually mount DVD-R.  But it still won't automount.  And since I have to use 'sudo mount' to manually mount I have to issue the 'sudo umount' command to eject it, i.e., my desktop/user can't unmount it.
_____________

So what would be different between the install boot and my installed OS?  Is it using a different (incompatible?!) ATA driver?  Did one of the kernel upgrades break something?

---

### Post by sir_cheats_a_lot on 2008-08-04
its not a problem with MS not playing nice with linux. have the same issume with data DVD-Rs burned under linux as well. it seems to do it in every distro that i've seen, so far.
 try this it works for me:
```
sudo mount -t auto /dev/scd0 /media/cdrom0 
```
will probably have to set it up to do this in your fstab file to get it to auto mount though. it's rather annoying it hasn't been fixed yet. been around long enough... but not bug can be fixed.. i imagine this could just be one of those problems. *shrugs*

:popcorn:

---

### Post by scorp123 on 2008-08-04
"Burning Issues with Vista":
[http://www.groklaw.net/article.php?story=20070422083715451](http://www.groklaw.net/article.php?story=20070422083715451)

In short: When you use Vista's own burning program and create a UDF disk, the software will default to **UDF 2.50** which **Linux does not (yet) understand**. You'd have to make sure that the software uses **UDF 2.0x** which is the standard that is understood by all OS's.

If you use other software (someone mentioned Nero ...) things might be different, e.g. Nero's makers probably selected better default values and most likely will per default choose a standard (e.g. ISO 9660?) that works on other platforms too.

---

### Post by bsmith1051 on 2008-08-04
my problems are unrelated to Vista (which I'm not using) nor the new UDF (which I'm not using).  In fact, it seems to be fixed since I uninstalled the official Nvidia video driver???  It seems to have been causing other seemingly unrelated problems, too, so maybe it was disrupting the kernel in general.

---

### Post by sir_cheats_a_lot on 2008-08-04
that's very odd that the nvidia drivers would interfere.  Just something about that just doesn't seem right.. but stranger things have happened.  


on a side note  "sudo mount -t auto /dev/scd0 /media/cdrom0"  is no longer working for me since reboot. :confused: only thing i've installed since was xine but why would that make a difference?  oh well.. ill have to remove it and try again. :mad:


*updated*
ok. removed xine rebooted, still nothing, reinstalled xine, opened up k3b and k3b still shows me the info on the DVD-R, but it still refuses to mount. try adding in the -f option and it tells me its already mounted according to mtab??  would be nice to see this fixed...oh well.](*,)
```
 sudo mount -f -t auto /dev/scd0 /media/cdrom0
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0

 sudo mount -t auto /dev/scd0 /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by sir_cheats_a_lot on 2008-08-08
heh.. ok after some messing around i sorta solved my issue without having to remove the proprietary nVidia driver.  still no auto-mount with it but... at least it works.  i can mount my data dvd-r discs using the same comand i use to mount iso files:
  sudo mount /dev/scd0 /media/cdrom0/ -t iso9660 -o ro,loop

nice eh?  hopefully someone else will be able to get similar results.

---

