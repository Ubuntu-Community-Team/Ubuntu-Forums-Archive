---
title: "Setting environment variables"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by NormR2 on 2008-05-01
How can I set environment variables so their values stick around.
The export command seems to only set them temporarily. I'd like to set them once (say in some profile) and have them stay set forever.

Thanks,
Norm

---

### Post by Monicker on 2008-05-01
> **NormR2 said:**
> How can I set environment variables so their values stick around.
The export command seems to only set them temporarily. I'd like to set them once (say in some profile) and have them stay set forever.

Thanks,
Norm


You can put it in /home/username/.bashrc, for that particular user. Or in /etc/profile for every user.

---

