---
title: "Installed Ubuntu 14.10 on laptop with hybrid SSD"
date: 2015-02-08
forum: New to Ubuntu
---

### Post by shirike on 2015-02-08
Hi all,

I've had a quiet morning at work so I've installed Ubuntu on my personal laptop (Asus N55SL) and got it set up just fine but then I realised I'd not given any thought to the issue of my hybrid SSD.

I have run the command:

```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```

which results in:

[IMG]http://i.imgur.com/DdquRsG.png[/IMG]

The SSD on the hybrid is 8GB in size so the above suggests it is currently being used as the SWAP area.

what is the most optimal setup?

---

