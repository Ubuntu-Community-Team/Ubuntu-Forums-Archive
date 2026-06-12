---
title: "LVM drive can't recognized"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by Unewbeginner on 2012-11-11
Hi there, I got some trouble when I tried to upgrade to 12.04. Now I try to save my data on my HD before I format it and re-install a new system. I have a laptop with Ubuntu too but when I plug my HD to my laptop, I can't find the drive.

I tried the command 
```
lvdisplay /dev/localhost
```

and I got the information below:

```
  --- Logical volume ---
  LV Name                /dev/localhost/root
  VG Name                localhost
  LV UUID                v6gYKs-BwVf-cSo2-tSgC-hh61-61ce-qi4E08
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                446.60 GiB
  Current LE             114329
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
   
  --- Logical volume ---
  LV Name                /dev/localhost/swap_1
  VG Name                localhost
  LV UUID                joDEne-sSc4-OfrT-WHo1-CAvu-KSDC-yOHcM2
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                18.87 GiB
  Current LE             4831
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
```

And then I tried:

```
mount /dev/localhost/root /mnt
```

but I got the message:

```
mount: special device /dev/localhost/root does not exist
```

---

