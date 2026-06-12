---
title: "Take control on new HDD"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Jr. on 2008-08-25
Hey guys, new to linux/ubuntu (installed yesterday), first post. I've been getting along pretty well but I've hit a snag. I installed a new HDD and I used gparted to partition it (1 partition, formatted in ext3). Now it won't let me save anything to it. I want to use it as a drive to store all my recordings from Mythbuntu, but I'm not sure if it will write. The properties say that it is owned by root. How do I take control? I've been messing around with the authorizations with no luck. Help? Thanks.

---

### Post by crispy_420 on 2008-08-25
You just need to change permissions. How do you have it set up in your fstab?

---

### Post by BGFG on 2008-08-26
I had this same prob a while back. First check Places>>Computer>>Filesystem>>media
(this is where you can view your mounted systems)
Your new harddrive may be disk or disk-2 or disk-3, something like that. you can check by right clicking and checking the properties>>permissions tab. to take ownership of the mount execute :
```

sudo chown username:username /media/'your mount folder name'

```
so in my terminal it looks like this :
```

sudo chown reyn:reyn /media/disk-2

```

You can then go back into the permissions tab of the folder and change the rights.

---

### Post by Jr. on 2008-08-26
> **BGFG said:**
> 
```

sudo chown username:username /media/'your mount folder name'

```
so in my terminal it looks like this :
```

sudo chown reyn:reyn /media/disk-2

```

Is the first username who has ownership and the second who transfer it to?
For me:```
sudo chown root:me /media/disk
```

---

### Post by BGFG on 2008-08-26
Sorry for the late reply,
Actually when i executed it, both were my username. Try that.

---

### Post by Jr. on 2008-08-26
Thanks. I got it

---

