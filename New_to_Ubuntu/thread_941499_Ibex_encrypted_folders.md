---
title: "Ibex encrypted folders"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Primefalcon on 2008-10-08
I just updated to Ubuntu Ibex and I went to have a look at the encrypted folders and I can't see them them in my home directly, nothing there, is there something I have to install to be able to use these?

---

### Post by Helios1276 on 2008-10-08
This was the the setup in alpha I think.

      sudo aptitude install ecryptfs-utils
    

      ecryptfs-setup-private

---

### Post by Primefalcon on 2008-10-08
thx :-)

---

### Post by Sycron on 2008-10-08
You're welcome! I'm glad you solved that but I don't have superpowers to solve my problem :| .

I have a question that is getting on my nerves because I installed ecryptfs and I don't know how to mount the Private folder. Can you help me ?

---

### Post by Helios1276 on 2008-10-08
> **Sycron said:**
> You're welcome!

Er..ya ..what he said??:):confused:

---

### Post by Sycron on 2008-10-10
I managed to mount my Private folder with ```
mount.ecryptfs_private
``` but I don't have write access. Please help me :|. I'm confused.

---

