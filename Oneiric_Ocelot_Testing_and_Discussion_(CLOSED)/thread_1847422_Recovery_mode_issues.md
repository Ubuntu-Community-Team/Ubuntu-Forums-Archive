---
title: "Recovery mode issues"
date: 2011-09-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by paul_in_london on 2011-09-20
I often boot straight into recovery mode when I first power up the PC to apply updates before a normal boot. This has been painful in recent days.

Breaking with tradition earlier tonight I went for a normal boot before checking for updates. The sequence of events was fairly typical:

[LIST=1]
[*]Normal boot ok
[*]Gnome shell loaded ok after login
[*]Applied updates (one of which was gnome-shell)
[*]Logged out
[*]Logged in again: gnome shell failed to load.
[*]Rebooted into recovery mode
[*]"Hung" on "loading RAM disk" - no additional startup messages displayed on console
[*]SysRq key + R-E-I-S-U-B to reboot
[*]Chose recovery mode again from GRUB
[*]Boots to cut-down recovery menu: read-only filesystem
[*]Ran fsck - ok
[*]Exit to normal recovery menu
[*]Chose netroot with networking - no network
[*]Started networking manually - ok
[*]gnome shell failed to load after normal reboot
[*]...back into normal recovery mode after more messing about (see above)
[*]Deliberately scheduled fsck for next reboot
[*]Chose normal boot from GRUB
[*]gnone shell loaded normally after login this time
[*]Finally - for <snip> sake! :icon_frown:
[/LIST]

Mainly using 64 bit, but have seen the same sort of thing with 386 and in a virtualbox VM on my machine @work (in each case, minimal setup + gnome shell).

Anyone else?!

Btw, if I'd just done a normal reboot immediately after step 3 it would probably have been ok!

---

### Post by Rocksinboxes on 2011-09-20
Booting with the "nomodeset, noacpi, noapic" kernel parameters might get you to bootable system. To get there highlight  recovery mode in grub and them where it its "quiet, nosplash".  then hit ctrl-x to boot the system. Please let me know if this helps. Thanks.

---

### Post by Quackers on 2011-09-20
I suspect the latest updates have borked things.
After running them I can't boot into gnome-shell or unity and fallback is useless as no functions are available.
I'm back in Natty for the moment. I'll wait and see what develops - updating from time to time via chroot.

---

### Post by paul_in_london on 2011-09-20
Thanks for the input guys.

Was fully up to date tonight (64 bit). All working fine after I'd finally got to the desktop earlier.

Haven't tried alternative boot parameters via GRUB. Never normally have to do this. It does seem to be the recent updates.

Rebooted to see if avoiding recovery mode would get me straight back in.

[LIST=1]
[*]Logged in: pop up saying "Cannot load gnome"
[*]Tried normal reboot again: no pop-up this time, but gnome-shell fails to load, no panel, no gnome3, no window manager, just global menu, able to use gnome-terminal though
[*]Installed metacity - minimal setup remember!
[*]```
metacity --replace &
```
[*]No good
[*]```
sudo touch /forcefsck
```
[*]Reboot
[*]Same as step 2
[/LIST]

Booted into my 386 Oneiric install, which is a day or two behind the latest updates, same box. Normal boot, gnome shell comes straight up after login.

---

### Post by Quackers on 2011-09-20
Are you using ppa:ricotz/testing? I am and that seems to be my problem.

---

### Post by paul_in_london on 2011-09-20
> **Quackers said:**
> Are you using ppa:ricotz/testing? I am and that seems to be my problem.
 Yes mate. You know what they say - "if you're not living life on the edge, you're taking up too much room"! ;)

---

### Post by Harry33 on 2011-09-21
> **Quackers said:**
> Are you using ppa:ricotz/testing? I am and that seems to be my problem.

I do not have any problems with Ricots Testing PPA.
BUT
If you have installed xserver 1.11 from xorg-edgers, then you do have problems with all 3D desktop environments. Especially if you use nvidia-current.

---

### Post by rbrick49 on 2011-09-21
I was having a lot of problems with ricotz so Ireverted back to ubunto gnome-shell been ok but yesterday had a slight boot problem went to recovery mode a nd did a file reset and everything was ok again

---

### Post by paul_in_london on 2011-09-21
> **Harry33 said:**
> I do not have any problems with Ricots Testing PPA.
BUT
If you have installed xserver 1.11 from xorg-edgers, then you do have problems with all 3D desktop environments. Especially if you use nvidia-current.

Hi Harry,

Yes, also using xorg-edgers and nvidia-current - asking for trouble, eh?! :)

Just updated my VM @ work. No nvidia-current on that obviously, but the same sort of boot problems.

Gnome shell fails to load automatically and I can't start it manually (my VM's been like that for quite a while). The desktop is usable though.

Latest updates:

```
Aptitude 0.6.4: log report
Wed, Sep 21 2011 09:44:01 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 14 packages, and remove 0 packages.
45.1 kB of disk space will be used
===============================================================================
[UPGRADE] ca-certificates 20110502+nmu1 -> 20110502+nmu1ubuntu3
[UPGRADE] firefox-trunk 9.0~a1~hg20110919r77142-0ubuntu1~umd1 -> 9.0~a1~hg20110920r77186-0ubuntu1~umd1
[UPGRADE] firefox-trunk-globalmenu 9.0~a1~hg20110919r77142-0ubuntu1~umd1 -> 9.0~a1~hg20110920r77186-0ubuntu1~umd1
[UPGRADE] firefox-trunk-gnome-support 9.0~a1~hg20110919r77142-0ubuntu1~umd1 -> 9.0~a1~hg20110920r77186-0ubuntu1~umd1
[UPGRADE] gir1.2-freedesktop 1.29.18~git20110915.1e26aa41-0ubuntu1~11.10~ricotz0 -> 1.30.0-0ubuntu1~11.10~ricotz0
[UPGRADE] gir1.2-glib-2.0 1.29.18~git20110915.1e26aa41-0ubuntu1~11.10~ricotz0 -> 1.30.0-0ubuntu1~11.10~ricotz0
[UPGRADE] gir1.2-mutter-3.0 3.1.91.1+git20110919.c1368155-0ubuntu1~11.10~ricotz0 -> 3.1.92-0ubuntu1~11.10~ricotz0
[UPGRADE] gnome-shell 3.1.91.1+git20110919.d23d9c3b-0ubuntu1~11.10~ricotz0 -> 3.1.92-0ubuntu1~11.10~ricotz0
[UPGRADE] libcups2 1.5.0-6 -> 1.5.0-6bzr1
[UPGRADE] libcupsimage2 1.5.0-6 -> 1.5.0-6bzr1
[UPGRADE] libgirepository-1.0-1 1.29.18~git20110915.1e26aa41-0ubuntu1~11.10~ricotz0 -> 1.30.0-0ubuntu1~11.10~ricotz0
[UPGRADE] libmutter0 3.1.91.1+git20110919.c1368155-0ubuntu1~11.10~ricotz0 -> 3.1.92-0ubuntu1~11.10~ricotz0
[UPGRADE] light-themes 0.1.8.24 -> 0.1.8.25
[UPGRADE] mutter-common 3.1.91.1+git20110919.c1368155-0ubuntu1~11.10~ricotz0 -> 3.1.92-0ubuntu1~11.10~ricotz0
===============================================================================

Log complete.
```

---

### Post by shaneo1 on 2011-09-29
I can't even boot in to recovery mode, it hang on the installing Ram Disk blah blah....  then after a few minutes continues to normal boot.  Anyone else have this problem ?? or is there a fix/bug for this?

---

