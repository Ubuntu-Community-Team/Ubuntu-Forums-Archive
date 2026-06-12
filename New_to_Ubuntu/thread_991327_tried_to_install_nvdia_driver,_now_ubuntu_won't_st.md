---
title: "tried to install nvdia driver, now ubuntu won't start"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by chipv12 on 2008-11-23
I don't know how to get back to previous setting

---

### Post by Sealbhach on 2008-11-23
What happens when you try to start?

Try these commands if you just get the login on a black screen:

```
sudo gdm start
```

if that doesn't work, try:

```
sudo dpkg-reconfigure xserver-xorg
```


.

---

### Post by chipv12 on 2008-11-23
great I'll give it a try....thanks

---

### Post by chipv12 on 2008-11-23
Got Ubuntu to start in low graphics mode.
My adapter type is :GeForce 6150SE nForce 430, NVIDIA compatable
trying to figure a way to get graphics better.

---

### Post by chipv12 on 2008-11-23
Got it fixed, opened a terminal, then typed sudo dpkg-reconfigure -phigh xserver-xorg

this corrected the problem and gave me the correct resolution.  Ubuntu runs circles around vista...I have both on 1 pc seperate hard drives.

---

