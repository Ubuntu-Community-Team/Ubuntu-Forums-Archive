---
title: "Start 11.10 exclusively in 2D sessions."
date: 2011-10-27
forum: New to Ubuntu
---

### Post by hazmatt86 on 2011-10-27
I just have had to install 11.10 on a slow netbook I have and I know it runs light years faster if its in a 2D Unity session. I'm taking it back to my family who aren't at all tech savvy, so I'd rather not explain to them that they need to login in 2D and the steps involved to do so. Is there any way to always login to 2D, rather than choose it from the list everytime? Thanks!

---

### Post by enkay009 on 2011-10-27
Edit /etc/lightdm/lightdm.conf

There's a line in there for user-session. 

```
user-session=ubuntu
```

This is the default window manager. Change it to:

```
user-session=ubuntu-2d
```

... or whatever you prefer.

---

### Post by 3rdalbum on 2011-10-28
Once you select Unity 2D from the cog menu on the login screen, it will remain selected even after a restart or cold shutdown.

---

