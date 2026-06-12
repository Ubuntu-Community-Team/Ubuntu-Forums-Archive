---
title: "Change encrypted disk passphrase"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by androssofer on 2012-11-19
Hi Guys!

So I installed 12.10.. and during the install I choose to encrypt the SSD.

However my house mate likes to borrow my computer every now and again. And the password I choose is one he has trouble remembering..

Is it possible to change it? So I could make it more memorable... 

Thanks..

---

### Post by Cheesemill on 2012-11-19
```
cryptsetup luksChangeKey /dev/sdx
```
where sdx is your encrypted partition.

---

### Post by androssofer on 2012-11-19
Awesome!

Thanks

---

