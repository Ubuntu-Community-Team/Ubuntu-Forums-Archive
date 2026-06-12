---
title: "[SOLVED] virtual Drive in ubuntu"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by burmanabhay88 on 2008-11-13
Is there some software I can use to mount Iso's, by creating a virtual drive, like PowerISO in Windows???

---

### Post by stephanvaningen on 2008-11-13
It is standard in Ubuntu as far as I know: right-click the iso-file and select 'Open with' -> 'Archive mounter'

---

### Post by Steve1961 on 2008-11-13
Gmountiso is also a nice application for mounting iso files, and really easy to use.

---

### Post by hyper_ch on 2008-11-13
very simple:

```

sudo mount -o loop image.iso /media/XXXX

```

Just make sure, that the mountpoint exists.

---

### Post by binbash on 2008-11-13
actoneISO2 ;)

---

### Post by burmanabhay88 on 2008-11-13
> **hyper_ch said:**
> very simple:

```

sudo mount -o loop image.iso /media/XXXX

```

Just make sure, that the mountpoint exists.

that's what the error said. no mountpoint exists. how do I make a mount point????

---

### Post by burmanabhay88 on 2008-11-13
> **stephanvaningen said:**
> It is standard in Ubuntu as far as I know: right-click the iso-file and select 'Open with' -> 'Archive mounter'

nope. option not there. thanks neways.

---

### Post by burmanabhay88 on 2008-11-13
> **Steve1961 said:**
> Gmountiso is also a nice application for mounting iso files, and really easy to use.

thanks. just what i needed.

---

### Post by hyper_ch on 2008-11-13
> **burmanabhay88 said:**
> that's what the error said. no mountpoint exists. how do I make a mount point????

create the directory :) then you have the mountpoint.

---

### Post by Fileburner on 2008-11-24
seems that Archive mounter does not work !! I tried to mount an Iso file but nautilus crashes whenever I try to access the mounted drive

---

