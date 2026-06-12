---
title: "Root partition is full and now I can no longer view my applications"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by MrDrPib on 2013-06-19
I was running ubuntu 12.10 decided to upgrade to 13.04 and although I had a few complications (unity did not show up at all) I eventually was able to get the system to appear to run correctly. Not too long after that I received a warning that my root partition was becoming full (I have separate partitions for root, home, and swap). After browsing the forums I was able to temporally remedy the problem by running apt-get autoclean, autoremove, purge, and update. After a while it said my root partition was full and no longer let me view my applications using unity. I can only see applications on my launcher and when I try to pull up my applications it says its loading but never shows any applications  On top of that when I try to remove some of the applications I have installed using the software center I get an error that says *"There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks." *I have tried resetting unity but the same problem occurs. What can I do to fix this problem and also was this error caused by somthing I did? I am hoping I can fix the problem without having to do a clean install.

---

### Post by MidnightGrey on 2013-06-19
can you copy paste the output of 
```
 df -h 
```

---

### Post by Impavidus on 2013-06-19
Read this: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by user_of_gnomes on 2013-06-19
run sudo apt-get clean and restart the system afterwards. (sudo shutdown -r now)

---

### Post by MrDrPib on 2013-06-21
> **MidnightGrey said:**
> can you copy paste the output of 
```
 df -h 
```

```
michael@GERTY:~$  df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       7.3G  7.0G     0 100% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.8G  4.0K  2.8G   1% /dev
tmpfs           572M  964K  571M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.8G  560K  2.8G   1% /run/shm
none            100M   32K  100M   1% /run/user
overflow        1.0M  1.0M     0 100% /tmp
/dev/sda6       899G  147G  707G  18% /home
michael@GERTY:~$
```

---

### Post by agillator on 2013-06-21
Your root partition (/dev/sda1/)is terribly small, it seems to me. Your home partition (/dev/sda6/), on the other hand, appears far larger than it needs to be unless you plan to have a hundred or so movies there. In short, it appears you need to enlarge your root partition and shrink your home partition. You can do that with gparted, either using a live (installation) cd or a gparted live cd. Be aware, though, that it is going to take some (probably a lot!) of time. I would do it in several steps. First, BACK EVERYTHING UP! Then I would MAKE SUrE i BACKED EVERYTHING UP and then I would shrink /dev/sda6 to something reasonable like 50G or even 100G and put the partition at the end of the space. Next step would be to move the newley unallocated space to be the next thing AFTER /dev/sda1. Finally expand /dev/sda1 into the unallocated space. This assumes, of course, that you do not want to leave some space unallocated. In fact it might not be a bad idea to leave 100G or so unallocated. This would allow you to update to a new release when one comes out without losing your current one, just in case. I find that very handy. I usually keep three releases (current and the last two) on my computer and often find it very useful to be able to drop back into an old release for something specific. I find 30G is enough for a complete active system if I keep biggies like movies on a separate partition, although 50G is probably better. The 'ideal' space for a system is sort of like 'how many angels fit on the head of a pin'.

---

### Post by Impavidus on 2013-06-21
Indeed, make your /home smaller and your / bigger. Currently your / is simply too small.

First backup the files in your /home, except those you can simply recreate (re-extracting archives you didn't delete, recompiling, caches etc). You may want to clean up your /home a bit, because the more is in there, the slower shinking that partition will be. You shouldn't loose any data, but you never know.

Next boot from a live medium, start gparted and shrink your /dev/sda6. I don't know where your swap is located on your disk, but you may have to move it. In case you decide to delete it and recreate it somewhere else, you may have to fix your /etc/fstab. Shrink the extended partition (the container for your /dev/sda6, probably called /dev/sda2), make sure the unallocated space is next to /dev/sda1 and make that partition bigger.

I think moving about 20GB from /home to / will be enough. 27GB in your / partition wil be enough and it won't have significant effect on the size of your /home partition. The more you move, the longer it may take. I recently shrank a partition with few data from 300GB to 120GB, which took aboult 40 minutes. Maybe you have some unallocated space on your disk. Be creative with that. I assume you don't have windows partitions on your drive. If you have, report back and show us a screenshot of gparted.

---

