---
title: "Does mkdir supports chmod without -m?"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by rraj.be on 2012-08-27
Hi, Is it possible to create a Directory using mkdir and change its mode and user?

Will this work in ubuntu?

```
mkdir /data/misc/bluetoothd 0770 bluetooth bluetooth
```

Thanks in advance.

---

### Post by Cheesemill on 2012-08-27
You can set the mode, but not the user.
```
mkdir -m 0770 /data/misc/bluetoothd
```For more info:
```
man mkdir
```

Edit - Just realised you asked about using mkdir without the -m switch, any particular reason why?

---

### Post by rraj.be on 2012-08-29
Thank you. :)

---

