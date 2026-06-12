---
title: "error 17 in dell"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by wandering rose on 2008-07-07
Hi,

I have a Dell Inspiron 6400 and am running hardy heron.  I mashed the keys last night and opened MediaDirect.  Now when I boot poor Lapatron the following message comes up

GRUB Loading stage1.5.

GRUB loading, please wait
Error 17

I know this has probably been posted before but I can't find a jargon free solution I can follow.  If anyone can help with some simple instructions, that would be awesome

Thanks,

Jen

---

### Post by swati_j on 2008-07-07
We needed an accountant for our office. I looked on all the Job sites but hardly any resumes to choose from. Then I came across a classified website called [www.baajaa.com](www.baajaa.com). The have tons of resumes to choose from and the best part is that its free to use :-)

---

### Post by freeeedoooom on 2008-07-07
it metioned here : [http://ubuntuforums.org/showthread.php?t=611906](http://ubuntuforums.org/showthread.php?t=611906)
but not worked out :(

---

### Post by bumanie on 2008-07-07
Post output of from live cd > sudo fdisk -l (that's a lower case L)then> sudo grub> find /boot/grub/stage1

---

### Post by freeeedoooom on 2008-07-07
install it again, I think it could stopped on the installing way .  and  didn't finish the installing.

---

### Post by cariboo on 2008-07-07
It looks like somehow the identity of you partition changed. the only way to repair this, is to boot of off the livecd. Once it has finished booting, open a terminal and type:

```
sudo fdisk -l
```

This will give a listing of your partitions. If you could post the output in your next post it will help us solve your problem.

Jim

---

### Post by sharks on 2008-07-07
[http://ubuntuforums.org/showthread.php?t=804696](http://ubuntuforums.org/showthread.php?t=804696)

---

