---
title: "Ubuntu on vmware - more space"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by oddragnvald on 2008-10-17
Hi.

I have a vmware image running ubuntu. When I try to install vmware tools, I get this error message:

"Please make at least an additional 94914k available or choose another directory"

There should be plenty of space available on the harddrive. How do I make more of it available?

Thanks.

Odd-R.

---

### Post by oddragnvald on 2008-10-18
If I do a  sudo df -h i get this:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             479M  391M   64M  87% /
udev                   10M   80K   10M   1% /dev
/dev/sda1              54M   17M   34M  34% /boot
/dev/mapper/internal-usr
                      2.0G  1.3G  608M  69% /usr
/dev/mapper/internal-var
                      2.0G 1013M 1004M  51% /var
/dev/mapper/internal-opt
                     1008M  882M  127M  88% /opt
/dev/mapper/internal-tmp
                      248M  8.1M  228M   4% /tmp
/dev/mapper/internal-home
                      124M  4.1M  114M   4% /home
none                  443M     0  443M   0% /dev/shm
```

In my vmware settings, there is a drive that is 10 gb, ant it says that the current size is about 400 mb. How can I make more of the space available?

Thanks.

---

