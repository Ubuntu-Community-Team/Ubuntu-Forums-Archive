---
title: "permanent links to other partition?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by reg55 on 2008-04-30
I am dual-booting Gutsy Gibbon with Vista.  Being fairly new to ubuntu, most of my old documents, music, etc. are in folders on my Vista partition.  I can find those files in the file browser and have made links on my desktop to jump to them quickly but every time I restart ubuntu the links disappear.  Is there a way to make permanent links on my desktop to the other partition on my drive?

I have a similar issue maintaining the path to my music in Amarok - related?

Thank you in advance.  I may be slow in responding if there are follow-up questions but I will respond.

---

### Post by swoll1980 on 2008-04-30
create shortcuts by holding shift+ctrl then drag and drop

---

### Post by reg55 on 2008-04-30
Thank you for your quick response.  I am able to make the shortcuts but here is what I get after a restart:

The link "Music" is Broken.
This link can't be used, because its target "/media/disk/Users/Rex/Music" doesn't exist.

---

### Post by T-Virus on 2008-04-30
Do you have to remount drive every time you start ubuntu again?

---

### Post by reg55 on 2008-04-30
I don't know what you mean by "remount drive", although I see that mentioned on these forums a lot.

---

### Post by T-Virus on 2008-04-30
I mean - as you start ubuntu do you have to "mount drive" or do ubuntu mount it itself?

Ok, even simplier - can you access drive you are linking from since computer boots up or you take any other actions?

Sorry if I didn't made this clear yet, just let me know if so.

---

### Post by reg55 on 2008-04-30
Ubuntu loads on one partition of my hard drive after I select it in the Grub loader.  I can find the other volume or partition of my hard drive that has my Vista files but I'd like to make a shortcut to those files that still works after a restart in Ubuntu.  Right now, I can make a link/shortcut but after a restart it won't work and says that it's broken (see message above with actual text).
Thanks again.

---

### Post by T-Virus on 2008-05-01
My only guess it that Ubuntu monts your vista drive at different place every time you start it.

Eg - you start ubuntu, it mounts drive at /media/sdb. You make a symbolic link. Restart. Ubuntu mounts drive at /media/sdc. Previous link does not work. Well that's just a guess. We better wait for someone who'll know this for sure.

---

### Post by reg55 on 2008-05-01
Thanks.  Hopefully someone has a definite answer...

---

