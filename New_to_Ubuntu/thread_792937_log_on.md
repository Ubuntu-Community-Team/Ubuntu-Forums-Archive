---
title: "log on"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by thomseddon on 2008-05-13
hi guys

i have a bit of a problem with my laptop, in that it does not recognize when i open the lid after closing it! (its an inspiron 6000 if anyone has further info on that front)

but it is often inconvnient to keep it on and open so sometimes i close it in the hope it will come back on

i never does

but i can navigate to the terminal and run

```
sudo restart now -h
```

without the screen on...

but i have found that if i run it without the -h i find myself with the screen all black where it just says root@thom-laptop:~ from which i can subsequently run

```
sudo restart now -h
```

and bam were turned off

the question i pose is; can i log back on from this screen?

what should i type?

---

### Post by phidia on 2008-05-13
There is a recent [thread]("http://ubuntuforums.org/showthread.php?t=766402&highlight=suspend+inspiron+6000") on this at the hardware/laptop forum hope that helps.

---

### Post by django0909 on 2008-05-13
```
sudo /etc/init.d/gdm restart
```

That should restart GNOME, I think.

---

