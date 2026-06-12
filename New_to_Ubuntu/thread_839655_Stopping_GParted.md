---
title: "Stopping GParted"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by drunkardivan on 2008-06-24
OK, my daughter managed to get a very nasty bunch of malware on her XP partition. She asked me for help, and, being a doting father, I agreed. She also wanted the Heron... No problem. Until she asked for more space in XP- she does a lot of photo manipulation, and images take up space.

I've had GParted running on her computer for the past hour, and it's stopped at *"check filesystem on /dev/hda2 for errors and (if possible) fix them"*. 

Is it normal gor GParted to take this long? Should I stop it? If I do, will I "dissolve" her hard drive?

Just looking for opinions.

---

### Post by avtolle on 2008-06-24
Did you defragment the HDD before starting Gparted?

---

### Post by kk0sse54 on 2008-06-24
Definitely sounds like a defragmentation issue. Did you also make sure that none of the partitions that Gparted was working with were mounted?

---

### Post by forestpixie on 2008-06-24
In addition - it can take a long time depending on what you are actually doing and how big the partitions involved are.

---

### Post by drunkardivan on 2008-06-24
Thanks, all.

I still have no idea what happened. I'd de-fragged everything, and for some reason, after an hour, it just quit.

I'm going to reboot and see what I've managed to do. Worst case, I'll have to do two clean reinstalls, but that's OK- we'd backed up all data.

---

### Post by Tea4all on 2008-06-24
I had problems with that too. I ran chkdsk in Windows and shutdown and restarted it twice to fix. Hope it helps.

---

