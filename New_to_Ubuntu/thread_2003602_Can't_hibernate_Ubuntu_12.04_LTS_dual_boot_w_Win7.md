---
title: "Can't hibernate: Ubuntu 12.04 LTS dual boot w/ Win7"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by SNortonUConn on 2012-06-14
I'm trying to adjust power settings on my laptop to allow the computer to hibernate when losing the lid or after 30 mins idle on battery.  However, the hibernate option is grayed out.  Here is what Terminal has to say:

```
scott@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:       3996252    3620616     375636          0     750628    1509368
-/+ buffers/cache:    1360620    2635632
Swap:       262140          0     262140
scott@ubuntu:~$ cat /proc/swaps
Filename				Type		Size	Used	Priority
/host/ubuntu/disks/swap.disk            file		262140	0	-1

```

Any advice on how to enable hibernation?

---

### Post by afixane on 2012-06-14
If i'm not wrong, the hibernate feature is deleted in ubuntu 12.04 :/

---

### Post by irw on 2012-06-14
Hibernation is not deleted, just hidden.
Have a look [here]("https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html")

---

