---
title: "How do i add myself to netdev?"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by phillip69 on 2012-06-08
When i try to connect to wicd it says that Im not in the netdev group i was just wondering how i could do that.
                                     Thanks

---

### Post by steeldriver on 2012-06-08
```
sudo usermod -aG netdev *username*
```You can check the updated group list with

```
groups *username*
```although I *think* you will need to logout / login for the change to take effect

---

### Post by phillip69 on 2012-06-09
I added myself to netdev and found out that I had to be root but its still not letting me connect to any networks wireless or wired

---

