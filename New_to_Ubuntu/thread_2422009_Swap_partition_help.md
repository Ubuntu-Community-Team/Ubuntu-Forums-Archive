---
title: "Swap partition help"
date: 2019-06-30
forum: New to Ubuntu
---

### Post by danh4648 on 2019-06-30
Hello,

I installed lubuntu on my pc dual booting with windows 10. At installation, I did not set aside space for swap. My lubuntu installation is on sda7. I resized that partition and set up a new partition sda9 with 12gb of swap. I used the swapon command from lubuntu command line. It shows 0 swap is being used.

Do I need to do anything further to let lubuntu on sda7 know that the swap it can use is on sda9?

Any help would be appreciated. 


Thank you!

---

### Post by Bashing-om on 2019-07-01
danh4648; Well -

Is /etc/fstab aware of the swap partition ?
```

cat /etc/fstab

```

For reference is my memory usage - where too swap is not touched:
```

sysop@x1804mini:~$ free -m
              total        used        free      shared  buff/cache   available
Mem:           3945         670        2413          48         860        3003
Swap:          4499           0        4499
sysop@x1804mini:~$

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by CatKiller on 2019-07-01
A swap file is as good as a swap partition these days (it wasn't always the case) and is the Ubuntu default.

Swap doesn't actually get used for very much anyway, unless you're *really* RAM constrained.

---

### Post by Bashing-om on 2019-07-01
danh4648; Humm -- curious and curiouser -

Show us:
```

sudo blkid -c /dev/null -o list
sudo parted -l

```

[INDENT][INDENT]see which way the wind blows
[/INDENT][/INDENT]

---

