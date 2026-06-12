---
title: "drive mounting in debian (sidux)"
date: 2007-09-18
forum: Other OS Talk
---

### Post by HappyFeet on 2007-09-18
i have a pretty good handle now on ubuntu, and would ike to start to really learn how to do things the "hard way". im installing sidux on another drive and was wondering if anyone can point me to a step by step guide to mounting hard drives and enabling read and write. thanks a bunch.

---

### Post by kidders on 2007-09-19
Hi there,

Your post is a little strange, in that most people couldn't use Linux for 10 minutes without mounting something, be it a CD, hard disk, network share, etc. There's really nothing to it ... **mount [device] [mount_point]**

The man page for "mount" contains detailed information on more advanced usage, such as how to enable/disable write access to something. Write access is _always_ enabled by default, with the exception of situations where Linux considers it unsafe, or simply can't do it, for example ...[LIST]
[*]When you mount a CD.
[*]When mounting a journalised HFS filesystem.
[*]When using the kernel's NTFS drivers.[/LIST]I can't help wondering if I'm misreading your o/p somehow though ... if there's something in particular about filesystem management that's confusing you, I'd be happy to try to point you in the right direction.

---

### Post by HappyFeet on 2007-09-19
> **kidders said:**
> Hi there,

***Your post is a little strange, in that most people couldn't use Linux for 10 minutes without mounting something, be it a CD, hard disk, network share, etc.*** There's really nothing to it ... **mount [device] [mount_point]**

The man page for "mount" contains detailed information on more advanced usage, such as how to enable/disable write access to something. Write access is _always_ enabled by default, with the exception of situations where Linux considers it unsafe, or simply can't do it, for example ...[LIST]
[*]When you mount a CD.
[*]When mounting a journalised HFS filesystem.
[*]When using the kernel's NTFS drivers.[/LIST]I can't help wondering if I'm misreading your o/p somehow though ... if there's something in particular about filesystem management that's confusing you, I'd be happy to try to point you in the right direction.

i think you're forgetting that in ubuntu there is something called ntfs-config. it requires no knowledge of the command line. i dont know why you would be confused about my post. i was merely asking for help on how to mount drives. oh, btw, there are alot of distros now that automount drives.

it doesnt matter now because after 2 hours googling for answers, i found out how. thanks anyway.

---

### Post by pedro_cesar on 2007-09-19
What happens if the Drive is not in the Fstab nor the mtab, beacuse I just plugged an external hard drive in and it's not mounting it, how can I mount it?

---

### Post by wolfen69 on 2007-09-19
hey kidders: "***There's really nothing to it ... mount [device] [mount_point]***" is not an answer a newbie can understand. 

THIS would be an answer:
open terminal:
mkdir /media/name
mount /dev/sda1(replace with your drive) /media/name

sux
apt-get update && apt-get install ntfs-3g
umount /media/xdxx
mount -t ntfs-3g /dev/disk/by-uuid/xxyyzz[etc] /media/xdxx
To get out of the konsole type: exit

maybe you shouldnt respond if you're going to give a half-baked answer.

---

### Post by HappyFeet on 2007-09-19
thanks wolfen. where were you yesterday? jk.

---

### Post by pedro_cesar on 2007-09-19
That's the thing, I don't know where is the new Drive, I even reset the computer and nothing. I know it's somewhere in /dev or /media, but I don't know it's name

---

### Post by wolfen69 on 2007-09-19
check /dev/disk

---

### Post by kidders on 2007-09-19
> **wolfen69 said:**
> maybe you shouldnt respond if you're going to give a half-baked answer.Yikes. You make it sound as though I should be apologising for bumping up an unanswered post!

Glad you found what you needed, HappyFeet. :-)

---

### Post by pedro_cesar on 2007-09-19
I have this devices:

```
scsi-1ATA_WDC_WD2500JS-75NCB3_WD-WCANKJ380029
scsi-1ATA_WDC_WD2500JS-75NCB3_WD-WCANKJ380029-part1
scsi-1ATA_WDC_WD2500JS-75NCB3_WD-WCANKJ380029-part2
scsi-1ATA_WDC_WD2500JS-75NCB3_WD-WCANKJ380029-part5
usb-Maxtor_6_767G_222222222222-0:0
usb-Maxtor_6_767G_222222222222-0:0-part2
usb-Memorex_TRAVELDRIVE_005B_0775182C0A7A-0:0
usb-Memorex_TRAVELDRIVE_005B_0775182C0A7A-0:0-part1

```

and I'm getting this:
```
root@pedro-desktop:/dev/disk/by-id# mount -t ntfs usb-Maxtor_6_767G_222222222222-0\:0 /media
mount: wrong fs type, bad option, bad superblock on usb-Maxtor_6_767G_222222222222-0:0, missing codepage or other error. In some cases useful info is found in syslog - try dmesg | tail  or so
```

I dunno if this is relevant: I am mounting this Drive in Ubuntu because it won't boot, my sisters messed it up, and I have A LOT of important information that I CAN'T lose 'cuz they're mainly college assignments.
One more thing the HD has a ntfs FS but I have ntfs-3g and FUSE installed so I'm thinking that's not the issue.

---

### Post by pedro_cesar on 2007-09-21
Well I gave up, I had to mount it on a Vista System, after I forced it in Vista, Ubuntu loaded it, too bad I had already done everything I needed and erased some files, that would come in handy to have now.

I still want to know how I could force the mounting of a drive, in case something like this happens again -and with the siss I got this there's a pretty good chance it does :D-

---

