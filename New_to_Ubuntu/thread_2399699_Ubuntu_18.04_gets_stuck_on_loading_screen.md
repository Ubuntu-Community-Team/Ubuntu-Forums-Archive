---
title: "Ubuntu 18.04 gets stuck on loading screen"
date: 2018-08-28
forum: New to Ubuntu
---

### Post by cadefoster on 2018-08-28
Just updated the last Lts which I had been using for many years to 18.04 but it gets stuck on the loading screen with Ubuntu and those dots every time. Only solution for me is to go into the recovery mode and do dpkg and then resume booting normally, but I’ve to do this every time to make the system work.

I’ve tried software update thinking it might be a bug and it’ll pick a package and fix it to no avail.

Kindly suggest a solution, I’m not a shell/command line user but I can type commmands when given. Thanks!

---

### Post by cadefoster on 2018-08-28
Can a moderator please move it to installation and upgrade section?

---

### Post by wildmanne39 on 2018-08-28
Hello, your thread is okay where it is at, the right people will see it here.

For future reference you can use the report button in the bottom left hand corner of the screen when you need to get a moderators attention and we will take a look.

Thanks

---

### Post by cadefoster on 2018-08-29
Ok thanks. I hope someone is able to help me a bit here.

---

### Post by kc1di on 2018-08-29
Hello cadefoster, 
Give use a little more info on your system, processor, ram video card? Thanks. 
Also you may want to run this command and see if there is something that's to blame.
```
systemd-analyze blame
``` List the output here.

---

### Post by cadefoster on 2018-08-29
> **kc1di said:**
> Hello cadefoster, 
Give use a little more info on your system, processor, ram video card? Thanks. 
Also you may want to run this command and see if there is something that's to blame.
```
systemd-analyze blame
``` List the output here.

Thanks for the reply but somehow I've solved the issue on my own.

I installed lightdm from the terminal instead of gdm3 and now I can boot without the dreaded stuck Ubuntu startup loading screen. In fact everything is a lot smoother now.

---

### Post by kc1di on 2018-08-29
Glad you got it going please mark the thread as solved.

---

