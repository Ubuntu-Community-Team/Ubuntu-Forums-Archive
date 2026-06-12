---
title: "Clone/Copy to another disk"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by darkzu on 2012-03-01
So basically i have installed ubuntu server 10.04.4 on a 40GB disk using the whole disk, all is fine and running, now the thing i want to do is to clone/copy that installed system including everything (configurations, /home) to a empty 10GB disk, the actual data used is 4.6GB and that could easily fit on the new drive. Now is this possible and how?

```

root@andromeda:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  4.6G   29G  14% /
none                  493M  200K  493M   1% /dev
none                  498M     0  498M   0% /dev/shm
none                  498M   52K  497M   1% /var/run
none                  498M     0  498M   0% /var/lock
none                  498M     0  498M   0% /lib/init/rw
none                   36G  4.6G   29G  14% /var/lib/ureadahead/debugfs

```

---

### Post by col48 on 2012-03-02
Just come across this, which you might look into:

[https://launchpad.net/relinux](https://launchpad.net/relinux)

Apparently not yet finished to the writer's satisfaction, but obviously well under way.

---

### Post by Grenage on 2012-03-02
To add to the above, Clonezilla is something I would recommend.

---

### Post by aeiah on 2012-03-02
yea, use clonezilla or just plain old dd.

you'll want to shrink the size of the partition to under 10gb beforehand though

---

### Post by Grenage on 2012-03-02
Aye, although I don't believe you'd need to shrink the partition if using Clonezilla - it doesn't clone unused space.

---

### Post by Ghost_Mazal on 2012-03-02
Clonezilla won't restore to a smaller partition (even if the data is smaller than the partition size) A very bad limitation that I wish they would fix

That's why I think the suggestion to shrink the original partition first.

---

### Post by darkzu on 2012-03-02
Thanks for the replies, i came across this:
[http://geekyprojects.com/storage/how-to-clone-hard-drive-to-smaller-drive/](http://geekyprojects.com/storage/how-to-clone-hard-drive-to-smaller-drive/)

So i will try using gparted to shrink and then use clonezilla, just one thing the above tutorial shows cloning the image to an external drive, is it possible to clone the system direct to the new internal drive?

---

### Post by mastablasta on 2012-03-02
yes it is.

---

