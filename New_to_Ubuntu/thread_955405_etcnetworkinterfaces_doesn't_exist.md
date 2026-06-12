---
title: "\etc\network\interfaces doesn't exist"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by expza on 2008-10-22
as the topic says, if I type nano etc/network/interfaces , nothing is there. It just says "new file"

If I try make my own one, it wont write as it says "File name or directory doesn't exist"

I've tried reinstalling, no luck.

Ifconfig reports my network working fine, and i'm able to ping other computers.

PLEASE help as this is seriously frustrating me!
Thanks.

edit : I got the slashes wrong in the heading. My bad.

---

### Post by AndyCooll on 2008-10-22
That's because you need to type:
```
sudo nano /etc/network/interfaces
```
Note the extra slash _before_ the "etc"

:cool:

---

### Post by expza on 2008-10-22
I love you.
Marry me.

THANKS! You don't understand how confused I was! Working 100% yesterday, and then all of a sudden not!

:)

---

