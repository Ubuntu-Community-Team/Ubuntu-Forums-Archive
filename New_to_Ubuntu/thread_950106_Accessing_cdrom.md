---
title: "Accessing cdrom"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by ShadowGT on 2008-10-16
Hello everyone.  I had a cd that has a lot of pictures that a want to save to my computer.  When I try to access the cd, I can't.

I tried running this command:
> sudo mount /dev/cdrom /media/cdrom
but all I get in return is an error message stating that there is no medium found.

Any help is appreciated.

Thanks.

---

### Post by rraj.be on 2008-10-16
try this command

```
sudo mount /dev/scd0 /media/cdrom
```

---

### Post by ShadowGT on 2008-10-16
I received the same error message after running that command.

---

### Post by ShadowGT on 2008-10-16
Ok, well it must not like the cd.  I put in another cd and everything worked great.

---

