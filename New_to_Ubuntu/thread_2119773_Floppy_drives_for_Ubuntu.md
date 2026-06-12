---
title: "Floppy drives for Ubuntu"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by Varsel on 2013-02-24
Can anyone recommend any **brand/model number** of floppy drives known to 'just work' with Ubuntu? Google turned up just about everything I never wanted to know, but will not give up any specific drives I can look into.

---

### Post by cariboo on 2013-02-24
Any generic floppy drive should work, be aware that the floppy drivers aren't installed by default, you have to install the driver manually using the following command:

```
sudo modprobe floppy
```

---

### Post by gordintoronto on 2013-02-28
Also note that nothing will show up until you have a floppy in the drive.

---

