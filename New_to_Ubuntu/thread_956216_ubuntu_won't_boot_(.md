---
title: "ubuntu won't boot :("
date: 2008-10-23
forum: New to Ubuntu
---

### Post by joey-elijah on 2008-10-23
did an upgrade to 8.10 beta earlier this evening and all went well.

rebooted a few times after so everything was jolly.

however, after trying to fix an error with no login screen appearing, upon logging in again ubuntu froze.

what else is there to do in a freezing situation but hit restart? 

since then arrrgh x repeatedly. 

i edited menu.lst via DSL, but nothing.

for some reason, when it gets to grub, it only displays a list of the kernel i just upgraded from (2.6.24-19-generic). 

editing these via GRUB CLI to what i know is my boot disk (hd0,0) yields nothing.

then i (for some reason) edited the everything in grub to match the 2.6.27-7.generic that i knew was the most recent kernel

however, this does boot but dumps me into busybox.

:(

how can i fix this? i'd hate to have to reinstall. everything was fine until i ran the xorg configure thingy to fix my login issues...

---

### Post by PhoenixP3K on 2008-10-23
Don't really know bro... try an older kernel? Might be a conflict or bug with the most recent one.

---

### Post by prematurebaby on 2008-10-23
You should have waited until 8.10 officially comes out.

---

