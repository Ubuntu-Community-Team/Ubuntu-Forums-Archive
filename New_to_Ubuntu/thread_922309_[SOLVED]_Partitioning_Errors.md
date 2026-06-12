---
title: "[SOLVED] Partitioning Errors"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by RobOrr on 2008-09-17
My uncle's wife managed to bork their family computer something terrible (they have XP and were all admins - bound to happen sooner or later) and wrecked it so bad that you can't even get the damn OS to load up. They give me a ring and so i try to access the harddrive using a Live CD. All goes well, turns out the malicious crap they downloaded deleted most of their stuff and put it's own crap in there. They tell me (with my encouragement) to install Ubuntu, but when it gets to the partition editor, i tell it to start the install and at 15%, when it tries to set up the filesystems, it fails saying that it could not create the ext3 filesystem. After this, Having forcemounted the volume, i find that I cannot remove certain folders, even with sudo rm -rf. They apparently have files in, however when i navigate to the directory and ask for dir or ls, it returns

: input / output error

nautilus cannot see any files in these directories either, and it's their inability to be removed that i think is causing the editor to fail. Help would be greatly appreciated, although my knowledge of this particular editor is limited. I'm using the newest Hardy Live CD for 32bit.

---

### Post by aeiah on 2008-09-17
use a gparted livecd to wipe and format the drive (after perhaps backing things up to an external drive or usb stick or whathaveyou). you should probably check the hard drive for physical errors, although this wont have been caused by whatever crap they probably installed there. you should also make sure all of their stuff is compatible before installing ubuntu. they may be turned off when their printer or scanner doesnt work

---

### Post by stalkingwolf on 2008-09-17
Try and back up their files. This may or may not be possible.  It may require the purchase of a recovery software for win.  Another option
is to install another HDD , install Ubuntu on it. You might be able to read the original files from there.

Another option is to plug their drive into another windows system and scan
it for viruses, malware ,etc.  Then if you can get it to boot, run Norton System Works utilities on it.

One way or another you should be able to rescue their files, unless their drive is totally FUBARed.

---

### Post by RobOrr on 2008-09-17
gave up, took drive out and connected it up to an old computer of mine. turns out there's some of the NTFS system wrecked (windows whinged at me) and all the data that was giving me errors was because of the shafted system. Have since formatted the input/output issue thanks to the gparted live cd (cheers for that :D) and now Heron is sparkly and nice on their computer. and i've given the uncle strict instructions about sudo and the rest of them have basic user accounts. hopefully that'll be that for now - they're taking to the change from xp reasonably well. Thanks all!

---

