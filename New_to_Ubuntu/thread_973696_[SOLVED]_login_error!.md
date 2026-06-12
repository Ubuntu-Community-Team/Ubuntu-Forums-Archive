---
title: "[SOLVED] login error!"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Abstinens on 2008-11-06
when i log in my screen goes black with a red line att the top and all i can see is the mouse pointer, then i get loged out again. can someone please tell me how to fix this ???

---

### Post by B34ST1Y on 2008-11-06
try running "fsck" to check the filesystem integrity, to make sure critical system files havnt become corrupted.

---

### Post by randy78 on 2008-11-06
After you check the filesystem integrity, you can drop to a Failsafe terminal (login menu, sessions>Failsafe Terminal) and try:
sudo dpkg-reconfigure xserver-xorg and see if that helps.

Good luck

---

### Post by Abstinens on 2008-11-06
> **B34ST1Y said:**
> try running "fsck" to check the filesystem integrity, to make sure critical system files havnt become corrupted.

im sorry, what is fsck? im new to ubuntu

---

### Post by handydan918 on 2008-11-06
> **Abstinens said:**
> im sorry, what is fsck? im new to ubuntu
never mind. just do the dpkg thing listed above in the other post.

---

### Post by Abstinens on 2008-11-06
nevermind. i fixed it by installing graphic drivers. thanks for the help anyways :D

---

### Post by B34ST1Y on 2008-11-06
that works too :-P :) happy ubuntu trails!

---

### Post by randy78 on 2008-11-06
Be sure to mark this post as SOLVED under the THREAD TOOLS tab near the top of the post!

---

