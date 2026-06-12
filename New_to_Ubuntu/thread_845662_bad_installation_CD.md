---
title: "bad installation CD"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by bu2971x on 2008-06-30
the stupid CD I got didnt let you scroll down to select the USA keyboard  so I picked Canada....
now its screwed..how do I change it to the USA keyboard
ubu 8.04

---

### Post by nkri on 2008-06-30
You have to reconfigure Xorg:
```
sudo dpkg-reconfigure xserver-xorg
```

It will prompt you for a bunch of things, one of which being the keyboard, and it should be in working order when done.

Good luck!

---

