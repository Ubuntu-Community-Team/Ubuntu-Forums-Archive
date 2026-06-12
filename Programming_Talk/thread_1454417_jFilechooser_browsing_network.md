---
title: "jFilechooser browsing network"
date: 2010-04-14
forum: Programming Talk
---

### Post by bobvanderputten on 2010-04-14
I wrote some program that uses JAVA jFilechooser. Under Windows, I can get to external network drive's. Under Ubuntu, I can only browse through local drive's Even when the network drive was mounted. How can I get the network drive from within a jFilechooser?

---

### Post by Morbius1 on 2010-04-14
> I can only browse through local drive's Even when the network drive was mounted.

If you're mounting it through Nautilus is has a hidden mount point at:

/home/your_user_name/.gvfs

I know nothing of jFilechooser but the question becomes - can it access a hidden directory. If not then you may need to create a symbolic link to a "real" directory.

---

### Post by bobvanderputten on 2010-04-16
Thanks Morbius1. 
I mounted the external network drive by Nautilus. I can see the /home/your_user_nam/.gvfs file and browse through the directory mentioned there.
I can see .gvfs/public on 192.168.2.3/music.
But I'am unable to create a link. When I use the Make Link command, it creates a broken link.
When I try to make a link within terminal, with 
ln -s /home/your_user_name/mnt/link2music /home/your_user_name/.gvfs/public on 192.168.2.3/music/ 
it says Target 192.168.2.3/music/ is not a file or directory. It seems that the spaces are giving the trouble?
Then I tried 
ln -s /home/your_user_name/mnt/link2music  "/home/your_user_name/.gvfs/public on 192.168.2.3/music/"
it says Operation not supported.
Any suggetsions to get any further?

---

### Post by geirha on 2010-04-16
```
ln -s "$HOME/.gvfs/public on 192.168.2.3/music/" "$HOME/mnt/link2music"
```

---

### Post by bobvanderputten on 2010-04-16
THANKS!! That worked!!

---

