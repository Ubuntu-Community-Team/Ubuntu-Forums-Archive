---
title: "New RAID setup has big chunk of hard drive space used up"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by pathos_society on 2011-10-11
I have four hard drives set up as a RAID 5.

[IMG]http://img.photobucket.com/albums/v465/saintsmythe/Screenshot-YUKIProperties.png[/IMG]

There's nothing on the drives except a single 600 MB movie and the "Lost+Found" folder.  Is there any way I can reclaim this 281 GB?

Worst case scenario, is this a sign something is wrong with my RAID or one of my drives?  If so, how do I check?

---

### Post by Lisiano on 2011-10-11
I assume you are using ext4 as the filesystem.
This space (5%) is reserved for Root and processes that run under Root. Completely removing this is a BAD idea but you can still decrease the %.
```
sudo tune2fs -m 1 /dev/sdx1
```
I don't know exactly where a raid volume is located at in /dev so substitute it with the real one. -m 1 means set the reserved block space to 1%, dot delimited numbers are accepted (My home has 0.3 set)

---

### Post by pathos_society on 2011-10-11
Would it still be a bad idea if I had a fifth (not part of the RAID) hard drive in there that I used for my boot drive?

---

### Post by Lisiano on 2011-10-11
As long as the boot partition is not in a Raid itself, then there are no problems.

---

### Post by pathos_society on 2011-10-11
Ok, I knocked it down to .1%, and now only 7 GB is taken up.  Thanks!

---

