---
title: "Listing all NTFS drives"
date: 2006-12-17
forum: Programming Talk
---

### Post by hadiriazi on 2006-12-17
Hi guys

Trying to write an app to list all my ntfs drives.
I'm using mono. Dont know where to start. Please help me.

Thanks

---

### Post by po0f on 2006-12-17
hadiriazi,

You can just parse the output of `mount` with `grep` and `sed`, will probably be easier.

---

### Post by hadiriazi on 2006-12-17
> **po0f said:**
> hadiriazi,

You can just parse the output of `mount` with `grep` and `sed`, will probably be easier.

Ok, Thanks
This is the command that I wil use:
```
sudo fdisk -l | grep NTFS
```

How do I do that inside mono. I mean how could I execute the command and get the esults?

---

### Post by po0f on 2006-12-17
hadiriazi,

```
[FONT="Courier New"]$ mount | grep ntfs | cut -f1 -d' '[/FONT]
```

I don't know how you would do it in C# or Boo or whatever Mono language you are using, maybe look in Gnome.Vfs?

---

