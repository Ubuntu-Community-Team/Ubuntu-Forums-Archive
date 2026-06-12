---
title: "apt-key add error"
date: 2016-11-05
forum: New to Ubuntu
---

### Post by axiantor on 2016-11-05
Hi I have this version installed:

1604xenial 64 minimal

I'm trying this command 
wget -qO - [https://apt.z.cash/zcash.asc](https://apt.z.cash/zcash.asc) | sudo apt-key add -

But I'm getting 

gpg: no valid OpenPGP data found.

Anyone can help me?

Thanks

---

### Post by oldos2er on 2016-11-06
Try ```
wget -qO [https://apt.z.cash/zcash.asc](https://apt.z.cash/zcash.asc) && sudo apt-key add zcash.asc
```

---

