---
title: "Can't mount 160 GB Ipod in Hardy."
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Jackfrost123 on 2008-07-08
I get "invalid mount option when attempting to mount the volume 'ipod'" Any takers? Btw what should be my anti-itunes, should I use rhythmbox?

---

### Post by Inxsible on 2008-07-08
I am not sure if the latest versions are being supported by Linux yet due to some DRM stuff Apple installed on their iPods. I may be wrong though.

Try "safely remove" in Windows or Mac and then try to mount in Linux again.

You anti-Tunes could be any of : Rhythmbox, Amarok, Exaile gtkpod or many others I don't remember right now. Its your choice

---

### Post by ptn107 on 2008-07-08
Mine mounts fine.  Here's the command it mounts with:

```
/dev/sdc2 /media/PHIL'S\040IPOD vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
```

---

### Post by kennster on 2008-07-08
> **Jackfrost123 said:**
> I get "invalid mount option when attempting to mount the volume 'ipod'" Any takers? Btw what should be my anti-itunes, should I use rhythmbox?

I had kinda the same problem took my ipod outta the box and pluged it in and it woudnt take songs pluged it into the macbook i have regstered it "safely reomved" it and then it worked fine with ubuntu hardy and i use rhythmbox it seems to work fine for uploading songs onto it :D just drag and drop them to the ipod and its done

---

### Post by Jackfrost123 on 2008-07-10
Hey guys thanks for the great help, let me try out what you suggested!

---

