---
title: "[HOWTO] Set the new Daylight Savings for Perth, Australia"
date: 2006-12-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Josh1 on 2006-12-05
Hi everyone,
I have found a small patch to set the new daylight savings for Perth, Australia. I have uploaded it to my site and you can download and install it easily.

Simply fire up terminal (Applications -> Accessories -> Terminal) and type in:
```

wget http://josh-taylor.com/ubuntu/Perth
sudo cp Perth /usr/share/zoneinfo/Australia/
sudo cp Perth /etc/localtime

```

Now restart Ubuntu, and it should now have daylight savings! :).

---

### Post by tormentum on 2006-12-16
Thanks for this one mate, big help :)

---

