---
title: "How can I mount a partition when booting 10.04?"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by tahitiwibble on 2011-10-29
Good day to one and all.

I have searched for the answer but must be using the wrong terminology or something because I haven't found anything to help me.

Would someone please tell me how I can mount a 'data' partition on my HD, preferably as soon as possible, when I boot into my 10.04 system?

Thanks very much for any help!

All the best,

Martin

---

### Post by Paqman on 2011-10-29
If you add an entry for it to the file [/etc/fstab]("https://help.ubuntu.com/community/Fstab"), it'll be automatically mounted on boot.

---

### Post by tahitiwibble on 2011-10-29
Thank you Paqman for your assistance.
I'm sorry but don't understand how to "add an entry". Would you be good enough to explain?

```
dad@dad-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4             20209928  12682232   6501088  67% /
none                   1526752       296   1526456   1% /dev
none                   1530996       168   1530828   1% /dev/shm
none                   1530996       300   1530696   1% /var/run
none                   1530996         0   1530996   0% /var/lock
none                   1530996         0   1530996   0% /lib/init/rw
/dev/sda5            232870200  85742564 147127636  37% /media/DATA
/dev/sda2             43807484  30613292  13194192  70% /media/OS
dad@dad-laptop:~$ 
```

/dev/sda5 is the partition I'd like to boot.

---

### Post by nogoodnamesleft on 2011-10-29
look at the file /etc/fstab and copy the format there to mount a partition

you will need to be root to edit it

This guide explains it
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Paqman on 2011-10-29
If you open the file /etc/fstab you'll see that it has lines for your existing partition(s). They're in the format:

(Partition blkid) (mount point) (filesystem) (options)

You don't have to use the blkid, and you can mount it wherever you like, so you could add a line that read:

```

/dev/sda5 /mount/point ext4 defaults 0 0

```
(Assuming it's an EXT4 partition)

You could use a blkid instead of /dev/sda5, to find out that partition's blkid, do:
```

sudo blkid

```

To modify the file you'll need to open it as root:
```

gksudo gedit /etc/fstab

```
I would advise making a backup of this file before editing it. After making any changes do:
```
sudo mount -a
```
If it doesn't spit out any errors you've done it right and it will mount itself automatically next boot.

There's tons more info on the page I linked to above, but that's the guts of it.

---

### Post by tahitiwibble on 2011-10-29
A thousand thanks Paqman. Have a good weekend. :)

---

