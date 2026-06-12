---
title: "Problem with GRUB"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Steel Lord on 2008-05-08
I have Ubuntu and Windows XP installed on the same PC. When I turn it on, and GRUB loads, rather than the usual menu that gives me my choices of OS, I get a screen like this -

```
[Minimal BASH-like line editing is supported. 
For the first word, TAB lists possible command completions. 
Anywhere else TAB lists the possible competions of a device/filename. ]

grub> _
```

How do I get it back to normal?

(You've probably noticed that I'm total noob with this.)

---

### Post by warbread on 2008-05-08
That's interesting.  What have you done lately?  Also, post the contents of you /boot/grub/menu.list file.

---

### Post by glennric on 2008-05-08
Try to follow the directions in the following link to restore grub
[Recovering Grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
If that doesn't work ask again.

---

### Post by Steel Lord on 2008-05-08
> **glennric said:**
> Try to follow the directions in the following link to restore grub
[Recovering Grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
If that doesn't work ask again.

I tried this and it didn't work.

---

### Post by Biggy on 2008-05-08
Install Startup-Manager from Add/Remove or download [Super Grub Disc]("http://supergrub.forjamari.linex.org/?section=download") to fix the problem.

---

### Post by glennric on 2008-05-08
Do you know how to access the contents of your hard drive while running the live cd?  If so do what warbread said and post the contents of your menu.list file.

---

### Post by Steel Lord on 2008-05-08
I fixed the problem the drastic way - sticking in the live CD, deleting the old partitions, and reinstalling Ubuntu and GRUB altogether. I haven't lost anything important since I only just using.

Thanks for the help, guys. It's nice to know there's such a supportive community here :)

---

