---
title: "how to encrypt the home directory in Ubuntu 19.10?"
date: 2019-10-26
forum: New to Ubuntu
---

### Post by ronjjjg8885 on 2019-10-26
on mint it is easy to do upon installation of the os.

how can i do it in ubuntu?

thanks!!

---

### Post by ronjjjg8885 on 2019-10-26
is this the way to go?
[https://www.linuxuprising.com/2018/04/how-to-encrypt-home-folder-in-ubuntu.html](https://www.linuxuprising.com/2018/04/how-to-encrypt-home-folder-in-ubuntu.html)

is it simple for a simple user?

---

### Post by oldrocker99 on 2019-10-27
You do have to add another user account, with sudo privileges, to enable your own /home folder to be encrypted.

It is all terminal commands, so here it is:[https://phoenixnap.com/kb/how-to-create-sudo-user-on-ubuntu](https://phoenixnap.com/kb/how-to-create-sudo-user-on-ubuntu)

---

### Post by TheFu on 2019-10-27
> **ronjjjg8885 said:**
> is this the way to go?
[https://www.linuxuprising.com/2018/04/how-to-encrypt-home-folder-in-ubuntu.html](https://www.linuxuprising.com/2018/04/how-to-encrypt-home-folder-in-ubuntu.html)

is it simple for a simple user?

**Warning:**
> This option was removed from the Ubuntu installer because it uses eCryptfs, which is considered "buggy, under-maintained", and the recommended alternative is a full disk encryption using LUKS.

I would say this is a bad idea.

---

