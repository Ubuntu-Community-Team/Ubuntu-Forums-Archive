---
title: "startup problems in gutsy"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by wolf3491 on 2008-06-21
I was happy with my install of Gutsy, so I haven't updated since before this problem started occurring.  This is on a dell Inspiron 1521 laptop.

Recently, half of my boots would freeze after login, and after a hard poweroff I could get in fine.  Halfway through the splash today, the splash disappeared to a black screen with a blinking cursor for 2 minutes, then booted fine.  Now, usually my ram usage(I have 2 gigs) is 13% with 26% cache, but now its 13 and 46!  Why the change? and is this bad?  And why is my boot crap all of a sudden?  I have messed with my grub and will see if it makes a difference next boot.

---

### Post by nowshining on 2008-06-21
note: linux uses disk cache a lot so if u have little RAM it's most likely good, :) 2. the kernel takes up X amount of memory and leave the apps to have at the rest. 3. if u reboot/boot X amount of times it does a fsck check. 4. also something could of hung for a second.

in terminal do a sudo /bin/bash

type ur pw and type it as normal - don't worry it won't show as u type:

cd /

then do

touch /forcefsck

what this does is #e2fsck force check next reboot.

---

