---
title: "screen resolution stuck at 640*480"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by mahmater on 2008-11-29
how to get rid of safe mode?
hi,
because I failed to install ubuntu 8.10 on my intel 2845g because of incompatibility,I finally managed to install it using safe mode. now,the resolution is too large 640*480 (the resolution is stuck and cannot be changed) ...and everything looks big: the cursor,the panels .... my question is:

how can I get rid of the safe mode and restore the normal look of ubuntu?

---

### Post by Xiong Chiamiov on 2008-11-29
Can you post the contents of your /etc/X11/xorg.conf please?

---

### Post by mahmater on 2008-11-30
thank you all friends.

after two days of googling and trying out various solutions,I came across the suggestion in this post and it worked just like magic ..here it is:

[https://answers.launchpad.net/ubuntu/+source/xorg/+question/50317](https://answers.launchpad.net/ubuntu/+source/xorg/+question/50317)

renaming the xorg.config did the trick!!!!

---

