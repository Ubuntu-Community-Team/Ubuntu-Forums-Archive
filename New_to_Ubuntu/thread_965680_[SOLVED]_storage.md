---
title: "[SOLVED] storage"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by johntravis on 2008-10-31
Put dvd movie on hdd, to put on dvd disk later, cannot find. Where can it be? How do I find what is on the hdd? Whithout formatting how can I clean hdd?

---

### Post by aeiah on 2008-10-31
do a file search?

---

### Post by johntravis on 2008-10-31
how do I do that, what is the command?

---

### Post by zvacet on 2008-10-31
You can find it by extension (avi,divx...) or by name.

For example 

```
locate divx*
```

```
sudo find / -name divx*
```

```
locate dvd name
```

```
sudo find / -name dvdname
```
[B]
 dvdname= name of your dvd[/B]

EDIT:What do you mean by cleaning HDD?Remove audio/video files or remove apps you installed?

---

### Post by johntravis on 2008-10-31
I need to remove audio/video files. Is there the possibility that these audio/video files would be temporary and be deleted upon reboot/ restart?

---

