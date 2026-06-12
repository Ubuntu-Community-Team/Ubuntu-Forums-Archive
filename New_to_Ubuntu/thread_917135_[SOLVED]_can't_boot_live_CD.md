---
title: "[SOLVED] can't boot live CD"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by punkbohemian on 2008-09-11
It might be more appropriate to ask this on an HP board, but the folks here seem to be plenty knowledgeable and more accessible...

I just got my new laptop (HP dv6700tse) and I'm trying to set it up to boot Ubuntu off a CD (so I can check it out before committing to an install). However, I can't figure out how to get my machine to boot from a CD instead of just launching into Vista. I checked out all the BIOS menus that I could access during startup, but couldn't find anything mentioning booting from a CD. I've obviously missed something, can anyone clue me in? Thanks.

---

### Post by Znupi on 2008-09-11
Try searching for something like "boot order" or "1st boot device", "2nd boot device", etc.

Also, how did you burn the Live CD? Did you just copy the .iso to the drive or did you burn the actual image file with some specialized software?

---

### Post by DFlame on 2008-09-11
Take another look at that BIOS. There should definitely be something named "Boot Order", "Boot Priority" or something similar. The key is to make the CD drive higher priority than the hard disk. once you've managed that F10 (on most systems) will save the configuration and restart.

There may also be an option to select where to boot from yourself during the startup. Check back if there's any progress :)

DFlame

---

### Post by clive littlewood on 2008-09-11
Hi

The boot options are usually on the 2nd page of Bios try page down.

It will then give you the option of moving the "Boot from CD " up to 1st priority.

Hope this helps

---

### Post by punkbohemian on 2008-09-11
Ok, this is freaky.

I went into the same menu I was in before I posted (the BIOS menu you get from hitting F10), and it was totally different than it was before.

Anyway, I now have Ubuntu up and running.

---

### Post by DFlame on 2008-09-11
Excellent. Hope you enjoy it. Could you [mark your thread as solved](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) unless there's anything else?

Feel free to drop by again if you need more help.

DFlame

---

### Post by punkbohemian on 2008-09-11
> Excellent. Hope you enjoy it. Could you mark your thread as solved unless there's anything else?

I've seen that "solved" thing around, I always kinda wondered what it was about. Thanks.

---

### Post by Znupi on 2008-09-11
> **punkbohemian said:**
> Ok, this is freaky.

I went into the same menu I was in before I posted (the BIOS menu you get from hitting F10), and it was totally different than it was before.

Anyway, I now have Ubuntu up and running.
Maybe you were pressing DEL? :)

---

