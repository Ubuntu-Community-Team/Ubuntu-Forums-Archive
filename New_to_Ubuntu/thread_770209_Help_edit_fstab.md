---
title: "Help edit fstab"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by djwilson303 on 2008-04-27
Can someone help me mount a ntfs drive at startup please, thanks.. it is /dev/sda1 and the dir is /media/laptop

---

### Post by LaRoza on 2008-04-27
> **djwilson303 said:**
> Can someone help me mount a ntfs drive at startup please, thanks.. it is /dev/sda1 and the dir is /media/laptop
Several ways:
Edit your fstab:

```

gksudo gedit /etc/fstab

```

And add the following line:

To get the UUID:
```

ls -lF /dev/disk/by-uuid/

```

Get the UUID, or use the /dev/sda1 if it will stay that way.

```

/dev/sda1           /media/laptop     ntfs    defaults,umask=007,gid=46   0   1

```
OR
```

UUID=<insert UUID given by command> /media/laptop      ntfs    defaults,umask=007,gid=46   0   1

```

---

### Post by ajgreeny on 2008-04-27
I suspect it should be possible with System Tools>>NTFS Configuration Manager, which I think is installed by default and should be able to do this for you; just follow the prompts when you start it.  Interestingly, gutsy and hardy usually install with NTFS partitions mounting automatically; in fact I had to edit my fstab to stop that happening because I like to keep my OSs completely separate.

---

### Post by djwilson303 on 2008-04-27
where are these system tools?

---

### Post by hackle577 on 2008-04-27
Go into Add/Remove Programs and search for "NTFS", that should bring up the NTFS Configuration Tool. Install it and use it as ajgreeny described.

---

