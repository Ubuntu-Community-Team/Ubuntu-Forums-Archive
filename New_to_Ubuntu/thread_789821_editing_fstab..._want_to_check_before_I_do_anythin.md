---
title: "editing fstab... want to check before I do anything."
date: 2008-05-10
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-05-10
Hi folks, 

So I'm going to try to edit fstab... planning on adding this line to the end of it to auto-mount my documents partition at boot. It's an NTFS partition. Just want to double-check the code (So I don't hose anything):

```
/dev/sda5	/media/mydocs	ntfs	auto,rw	0	0
```

Following the tuXfile tutorial... 

Thanks, 

-'Mage

---

### Post by macaholic on 2008-05-10
Looks good to me, I would back up the old one just to be safe, in case you need to revert back to it for any reason.

---

### Post by Rocket2DMn on 2008-05-10
I typically use
```
/dev/sda5	/media/mydocs	ntfs-3g	defaults,locale=en_US.utf8	0	0
```
ntfs or ntfs-3g both suffice.  You can change your locale based on where you actually are and the type of text used in filenames.  You can see what's available on your system with
```
locale -a
```
though you probably don't need to change it.

---

### Post by UnWarierMage224 on 2008-05-10
so

```
 /dev/sda5 /media/mydocs ntfs defaults 0 0 
```

will still allow read-write access?

-'Mage

---

### Post by Rocket2DMn on 2008-05-10
> **UnWarierMage224 said:**
> so

```
 /dev/sda5 /media/mydocs ntfs defaults 0 0 
```

will still allow read-write access?

-'Mage

yes, rw is part of defaults.

---

### Post by Ptero-4 on 2008-05-10
> **UnWarierMage224 said:**
> so

```
 /dev/sda5 /media/mydocs ntfs defaults 0 0 
```

will still allow read-write access?

-'Mage

Not AFAIK. ntfs uses the kernel ntfs driver which is read-only. ntfs-3g uses the fuse-based driver which does read-write.

---

### Post by Rocket2DMn on 2008-05-10
> **Ptero-4 said:**
> Not AFAIK. ntfs uses the kernel ntfs driver which is read-only. ntfs-3g uses the fuse-based driver which does read-write.

I think this used to be the case, but since Gutsy they act the same.  I just tested in Hardy for my windows partition and I have r/w permissions either way.

---

