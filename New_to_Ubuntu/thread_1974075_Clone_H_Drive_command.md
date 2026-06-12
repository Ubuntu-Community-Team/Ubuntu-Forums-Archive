---
title: "Clone H Drive command"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by Greg Mueller on 2012-05-05
My computer originally had one HD. I did an OS upgrade that I was not happy with and could not figure a way to go back to the previous version without complete data loss, so I installed a second HD and the ubuntu version I liked and transferred the data I needed from the original HD to the new HD. I can still see both HDs.
I am wondering if there is a terminal command (etc) that would allow me to clone the new HD to the original HD so I can use the new HD elsewhere.

Is there such a thing?

Thanks

---

### Post by westie457 on 2012-05-05
Hi the 'dd' command usually works very well.

See ```
man dd
```
for more information.

One example of the dd command is ```
dd if= /dev/sda of=/dev/sdb bs 1024
```
Where sda is the one you want to copy and sdb will be the clone. Make sure you get things the right way round otherwise you will very easily destroy the information on the wrong one.

The drive being copied to must be the same size or larger than the one being copied or it will fail.

If you are not feeling that brave then something like 'Clonezilla' would be a safer alternative.

[http://clonezilla.org/](http://clonezilla.org/) for more info.

---

### Post by Greg Mueller on 2012-05-06
Thank you

---

