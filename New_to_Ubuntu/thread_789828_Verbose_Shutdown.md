---
title: "Verbose Shutdown ?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Drakkor on 2008-05-10
How can I stop it ? :)

---

### Post by warbread on 2008-05-10
I believe if you add the word 'splash' to the end of your 'Kernel' line in /boot/grub/menu.list, you won't get verbose boots or shutdowns.

Example:
```
kernel        /boot/vmlinuz-2.6.22-14-rt root=UUID=7b8009fd-f6f4-4121-8714-8d7332fae0f2 ro quiet **splash**
```

---

### Post by Drakkor on 2008-05-10
Yeah , just in restarts or shutdowns,not on boot up here's my menu list\
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0df6eca9-1bbc-40e7-8398-9f2fb9480db6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

I should add it was not always like this, perhaps after some update ?

---

### Post by warbread on 2008-05-10
According to [this post,]("http://ubuntuforums.org/showthread.php?p=4708984") you should try running fsck -y from a live boot.  Apparently, usplash has a low threshold for errors and will get talkative at the first sign of trouble.  But then, I'm really just parroting here, and have no clue.

---

### Post by Drakkor on 2008-05-10
Thanks,warbread,will try that when I next boot :)

---

