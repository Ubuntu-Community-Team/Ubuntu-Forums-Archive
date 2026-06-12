---
title: "size of swap?"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by Matrix01 on 2013-10-14
what is the size of swap in wubi?

---

### Post by deadflowr on 2013-10-14
What does the system monitor say.
or free -m.

If you want to try changing the size of swap, looky here
[https://wiki.ubuntu.com/WubiGuide#How_do_I_increase_my_swap_space.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_increase_my_swap_space.3F)

---

### Post by Matrix01 on 2013-10-16
mistake.

---

### Post by Bucky Ball on 2013-10-16
You made a typo. There is a space between 'free' and '-m'

```
free -m
```

Copy and paste or read carefully. ;)

PS: To all: Please use [code] tags for clarity. Thanks.

PPS: Just a note, Wubi is not considered a permanent solution and is intended to 'try' Ubuntu. It is also being phased out and will shortly be no longer. FYI.

---

### Post by elliotn on 2013-10-16
I never understand why I need swap while I have more than 4GB ram

---

### Post by heir4c on 2013-10-16
> **elliotn said:**
> I never understand why I need swap while I have more than 4GB ram


Sometimes it use the swap. When you use the hibernate it will write a little bit to swap.

---

### Post by philinux on 2013-10-16
> **elliotn said:**
> I never understand why I need swap while I have more than 4GB ram

It's a default on the auto install. But easily modified.  In a manual install you can just not create a swap partition. Unless you need hibernate.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

