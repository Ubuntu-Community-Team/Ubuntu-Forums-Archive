---
title: "newbie with some simple Qs,"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by s0n0f0siris on 2012-04-22
hey guys, Im new to this OS, just have some few questions
1) i have ubuntu running along side win7 and i forget what i did when i installed it, but it only has like 20 gigs of the hd devoted to ubunbu, the rest is only available in windows, HOw can I donate more of the Hd so that Ubuntu can use it and theres more than 16 gb free.
2) Not really a problem but every time i try to go on battery power it freaks out and tells me the battery is low when its fully charged, i usually just ignore this and it works fine.

---

### Post by pqwoerituytrueiwoq on 2012-04-22
20gb is fine for ubuntu especially if you sym link your music and stuff to your windows partition
windows need a lot more hdd space than it appears to due to its paging file
you could boot a live cd and open gparted and re-size and move partitions around but it can take a long time and has a risk of failure (aka data loss)

---

### Post by Peripheral Visionary on 2012-04-22
I set 10 gigs aside for Xubuntu and even after installing a bunch of stuff, it takes less than 4 gigs of space on my hard drive. 20 gigs is way more than enough!

---

### Post by mastablasta on 2012-04-22
> **s0n0f0siris said:**
> hey guys, Im new to this OS, just have some few questions
1) i have ubuntu running along side win7 and i forget what i did when i installed it, but it only has like 20 gigs of the hd devoted to ubunbu, the rest is only available in windows, HOw can I donate more of the Hd so that Ubuntu can use it and theres more than 16 gb free.

Don't know about the battery.

Ubuntu can read widnows partition as others mentioned, sou can keep data on windows partition while 20 Gb will be plenty for the Ubuntu OS. Linux porgrammes take much less than windows programmes, because they share their libraries (which brings a lot of other issues, but won't get into that now)..
But if you would still liek to increase linux partitions then you need to defragment the widnows part of the drive a couple of times (2 time should be OK), run a check disk after defragmentation. then use windows disk manager to create free (empty, unformated) disk space. then boot with liveCD/USB and use gparted to increase the linux partition size into the unformatted part of disk. reboot and that's it.

---

### Post by s0n0f0siris on 2012-04-22
Ok, thanks for the tips guys. I figured it out.
yeah i realize ubuntu does not need that much memory, I was gonna need more because i noticed(and it may be just me) that torrents seem to download alot faster on deluge than they ever did in bittorrent on windows, (for example this morning i dled last nights ufc ppv in about 20 min,It was over 2 gigs) SO using that reasoning i decided i should just do my downloading on ubuntu and thus would need much more drive space. Now im running out of reason to use windows, other than games its fast becoming obsolete,

---

