---
title: "[SOLVED] reinstalling gnome-desktop in rescue mode?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by ubume2 on 2008-06-26
I had audio problems and followed a thread which involved deleting alsa and installing it again.  

When I rebooted, I had no desktop.

I have a live cd for 8.04.

How do I, can I, reinstall gnome-desktop from the command line?

Thanks.

---

### Post by Troll_the_Great on 2008-06-26
It's easy, just type this code:

```
sudo apt-get install gdm
```

and your done.Tell me if that worked.
Cheers!

---

### Post by ubume2 on 2008-06-26
That did it. for some reason i had to use sudo aptitude install gdm.  thanks for your help.

---

### Post by Troll_the_Great on 2008-06-26
Glad I could help :). And it's best you used aptitude, you can remove it easier later if you want.
Cheers!

---

