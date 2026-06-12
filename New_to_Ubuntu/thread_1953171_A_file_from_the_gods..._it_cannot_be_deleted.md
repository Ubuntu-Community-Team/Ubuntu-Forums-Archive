---
title: "A file from the gods... it cannot be deleted"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by Gizim on 2012-04-05
Under a folder I have a file called .fuse_hidden00000d200000000d

-rw-r--r-x 1 root root 4266925124 Dec 16  2009 .fuse_hidden00000d200000000d*

 chattr -i .fuse_hidden00000d200000000d
chattr: Function not implemented while reading flags on .fuse_hidden00000d200000000d


Nothing... i got nothing...

---

### Post by dniMretsaM on 2012-04-05
Use this:
```
sudo rmdir /path/to/dir
```

If that doesn't work, try this:
```
sudo rm -rf /path/to/dir
```

---

### Post by HeroOfCanton on 2012-04-05
Or try "gksudo nautilus" (GUI) to delete it. The owner is listed as root.

... Or maybe you just need to run .lighter_hidden to burn the fuse. :D

---

### Post by Gizim on 2012-04-05
> **HeroOfCanton said:**
> Have you tried sudo rm or "gksudo nautilus" (GUI) to delete it? The owner is listed as root.

... Or maybe you just need to run lighter_hidden to burn the fuse. :D

Yup, rm -rf or rm none of it worked :)

---

### Post by wildmanne39 on 2012-04-05
Hi, please know that this is a very dangerous command:
```
rm -rf
```
if you use it and give the wrong path you could delete your entire system.
Thanks

---

### Post by HeroOfCanton on 2012-04-05
You can try rebooting. Maybe there is some sort of temp access lock on it.

Also you could give the GUI a try through gksudo . For reasons I can't explain sometimes it works when the CLI doesn't.

Just be sure you really want/need the file gone. If it's locked down like that perhaps the system needs or expects it? Maybe best to let it be if it's small and not taking up resources.

---

### Post by jerome1232 on 2012-04-05
Fuse usually has to do with mounting partitions via the user ie if mount a network share, it get's placed under a .gvfs folder in your home, which can't be deleted by root, it sounds like the same kinda thing with your fuse_hidden folder

---

### Post by Gizim on 2012-04-05
> **jerome1232 said:**
> Fuse usually has to do with mounting partitions via the user ie if mount a network share, it get's placed under a .gvfs folder in your home, which can't be deleted by root, it sounds like the same kinda thing with your fuse_hidden folder

Okay here is the thing I had a bunch of movies on a Seagate External drive I plugged them into my Unraid media server and copied everything over and then unplugged the drive. So the file is no longer on the external drive. 

I don't get it if I am root why can't i delete the file?

I know unraid isn't Ubuntu but this is about the only linux forum I know that has a good community.. it's a crap shoot.

---

