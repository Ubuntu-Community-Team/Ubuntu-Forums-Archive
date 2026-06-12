---
title: "USB drive problems and Stepmania (OpenITG)"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by JanusDuo on 2008-10-03
Hey guys,

I'm trying to get flash drive support working for a game called StepMania.  It's basically an open-source reverse engineered clone of the arcade game Dance Dance Revolution (DDR).  It's a game that uses USB flash drives to save stats and scores.  So you plug in your flash drive, play a game, oh look your buddy wants to play a game so you pull your flash drive aaaand BITCH BITCH BITCH Ubuntu doesn't like that.  It wants you to unmount your drive before you pull it.  Windows does this to, but it has a secondary setting where it write caches and doesn't bitch at you when you yank without unmounting.  I don't know how to do this in Ubuntu (though research suggests Ubuntu does this write cacheing anyways and I really just need to find a way to turn off the bitching popup.

So I'm trying to get this game to use my flash drive.  Thing is it looks for it in gconf and if it's not there it ignores it when I plug it in, but with gconf you have to specify like /dev/hdc7, but if it's not unmounted cleanly and you plug something back in it will be something NEW like /dev/hdd8 and now its no longer in gconf and then it's ignored by Stepmania.  Is there any ways to specify by port and bus in gconf?

I'm eventually gonna have this be a homebuilt arcade cabinet and dance pads connected so there'll be no keyboard and mouse to mount/unmount the flash drives.  The short-lived In The Groove (ITG) series was a modification to DDR cabinets that was basically a Linux box running a modification of StepMania and they did USB drives the way I'm trying to so I know it's possible.  They weren't using Ubuntu like myself however.

---

### Post by Orange_and_Green on 2008-10-03
Hello Janus,

what version of Ubuntu are you using? In Ubuntu 8.04 ("Hardy Heron") external drives are mounted synchronously by default, which means no data loss and no complaints if you just remove the drive (although it still is a potentially dangerous procedure and will cause data loss if you are unlucky enough to pull out the drive in the midst of a write operation).

I wish you happy gaming :popcorn:

---

### Post by JanusDuo on 2008-10-05
Yeah, upgrading to Hardy Heron fixed the popup problem, however the game still wouldn't mount the flash drives.  After taking a look at the games logs and system logs I saw what was happening.

The game detected a drive plugged in, it would check fstab and if the drive wasn't listed it was ignored.

If the drive WAS listed the game would try to mount it.  Unfortunately because I have the usb-storage module if it's in fstab it gets mounted as soon as it's plugged in.

So the game would get a mount error as the drive is ALREADY mounted.

See appatently the game was written to use the ub module instead of usb-storage.

So I compiled a new kernel with the 2.6.26 version linux kernel code.  I used my old .config file and just modified it to include the ub module.

I install the .deb with dpkg and restart...X won't start.  After some digging I find out why.  Apparently the module/drivers for my nVidia Geforce FX 5200 PCI aren't in the default kernel or something.  No problem I'll just get em...oh look, nothing in unsupported drivers...I've got glx-nvidia, maybe I need glx-nvidia-new?  Nope that didn't help.  Well lets get the drivers for linux off the nVidia site, boot into a command prompt, turn off gdm and install it.

Yeah, so now my OLD kernel is hosed too.  I can only get a desktop if I boot with 'nv' driver or some other generic driver that doesn't support hardware acceleration.

That'd be fine if hardware acceleration wasn't required just to run my game!  So now I don't even know if the USB cards are working with it since I put ub into the kernel.

Once again my life looks like this:
[IMG]http://imgs.xkcd.com/comics/success.png[/IMG]

---

### Post by JanusDuo on 2008-10-06
Okay, little update here.  I reinstalled Hardy from a newly burned CD, then went to work trying to get the USB working.  From my previous work on it I found out:

> Okay so when I don't define my flash drives in fstab OpenITG goes:

[QUOTE]00:23.737: Ignoring /dev/sdd1 (couldn't find in /etc/fstab)

And when I DO put them in fstab

```
00:29.128: executing 'mount /dev/sdd1'
00:29.139: done executing 'mount /dev/sdd1'
00:29.139: WARNING: failed to execute 'mount /dev/sdd1' with error 256.
```

What is error 256? Well lets run mount /dev/sdd1 in terminal to see!

```
$ mount /dev/sdd1
mount: according to mtab, /dev/sdc1 is already mounted on /media/flashdrive1
mount failed
```

So fstab mounts the drives, OpenITG checks fstab to see if the drive is mounted, sees that it is, tried to mount it AGAIN fails, and tells me to go screw myself. What am I missing? ;-) Please help![/QUOTE]

So I need to disable automounting the drive.  Thus I edited my fstab to read:

```
/dev/sdb1   /media/sdb1   vfat   rw,user,noauto,sync   0   0
/dev/sdc1   /media/sdc1   vfat   rw,user,noauto,sync   0   0
/dev/sdd1   /media/sdd1   vfat   rw,user,noauto,sync   0   0
/dev/sde1   /media/sde1   vfat   rw,user,noauto,sync   0   0
/dev/sdf1   /media/sdf1   vfat   rw,user,noauto,sync   0   0
/dev/sdg1   /media/sdg1   vfat   rw,user,noauto,sync   0   0
/dev/sdh1   /media/sdh1   vfat   rw,user,noauto,sync   0   0
```

Unfortunatly Ubuntu is STILL MOUNTING anything I plug into it.  I then used gconf-editor to turn off automount and autobrowse in the nautilus settings, to no noticable effect.  Any other suggestions on making Ubuntu ignore my flash drive so this program can handle the mounting of the drives?  I still need the usb-storage as this program issues commands such as "mount" though.

Alternately I need to compile a custom kernel that supports nVidia graphics cards and has the ub module.

---

