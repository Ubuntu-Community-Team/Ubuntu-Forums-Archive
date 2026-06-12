---
title: "“not enough free space” for software update ubuntu 13.04"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by davoud2 on 2013-09-15
Hallo, I install ubuntu 13.04 on USB flash drive (32GB) and i try to
use software update for first time but i get this error “not enough free space” .
and i read some of answers in your web but it does not helped,Please help me ,i am new i ubutnu.
thank you.

---

### Post by ibjsb4 on 2013-09-15
Welcome to the forums :)

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
df -h
```

And please post the output.

---

### Post by coffeecat on 2013-09-16
Not a tutorial.

*Thread moved to **Absolute Beginners Section**.*

---

### Post by CeejRab on 2013-09-16
Is Ubuntu on a partition of the drive?

Is it a full installation of Ubuntu or a live CD set up with unetbootin or similar software? You can tell if its a full install or not this way: if there is a hard drive icon on the desktop and launcher that says "install this" it means you're running a live CD not a full install.

If it is a live CD, it likely doesn't have a persistence file set up and the squashfs size is the standard 695mb for the Ubuntu live CD so it won't it use more than a certain amount of your drive space. 

Can you upload a screenshot of the details section under system settings? (Via the cog at the top right of the screen on the menu bar) this will help me determine if you have a full install or not.

Any more info you can provide would help :)

---

