---
title: "Volume greater on Vista"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Baldemar on 2008-09-01
I have run both vista and ubuntu. When I bought the computer I installed ubuntu and never used vista. Yesterday I logged in vista and noticed that volume is extremely louder than in ubuntu. Any suggestion on what to do to get better volume on ubuntu.

---

### Post by porchrat on 2008-09-01
it is not that the volume is BIGGER...it is that Vista and Ubuntu measure them differently...

one uses blocks (Ubuntu) which is more accurate, but makes the drive seem smaller as it uses units of 1024 as opposed to Vista which measures it in units of 1000 (makes it seem bigger).

---

### Post by shae on 2008-09-01
I believe he is referring to sound volume.  Open a console and type:
```
alsamixer
```

and check to see that the appropriate channels are turned up.

---

### Post by porchrat on 2008-09-01
oh LOUDER...I read it as bigger...](*,)

silly me

---

### Post by Baldemar on 2008-09-01
> **shae said:**
> I believe he is referring to sound volume.  Open a console and type:
```
alsamixer
```

and check to see that the appropriate channels are turned up.

Worked great!!! many thanks

---

