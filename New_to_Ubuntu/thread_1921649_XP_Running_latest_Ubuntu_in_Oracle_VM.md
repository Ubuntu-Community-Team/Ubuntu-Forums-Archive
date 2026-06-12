---
title: "XP Running latest Ubuntu in Oracle VM"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by 12153369 on 2012-02-07
Set up and updates have gone very well, access to the Internet fine, but I can't work out how to access my Win network.
Ubuntu doesn't see it. Is it because my Win network and Ubuntu reside on the same machine? I was under the impression it was a no hassle network setup.
Thanks for any help.

---

### Post by sanderj on 2012-02-07
> **12153369 said:**
> Set up and updates have gone very well, access to the Internet fine, but I can't work out how to access my Win network.
Ubuntu doesn't see it. Is it because my Win network and Ubuntu reside on the same machine? I was under the impression it was a no hassle network setup.
Thanks for any help.

Probably because your guest (Ubuntu) is behind Virtualbox' NAT. Change it to "Network Bridge" in the Virtualbox VM Settings and it should work.

---

### Post by 12153369 on 2012-02-07
Thank you kindly, network appeared.

---

