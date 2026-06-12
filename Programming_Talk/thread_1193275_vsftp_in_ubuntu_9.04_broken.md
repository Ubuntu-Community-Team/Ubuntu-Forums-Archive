---
title: "vsftp in ubuntu 9.04 broken?"
date: 2009-06-21
forum: Programming Talk
---

### Post by bcz on 2009-06-21
Hi All

Just tried  loading vsftp from repositories.  Unable to find files

Any recommendation on what repositories to use?

Thanks in advance

Rgds Bill C

---

### Post by Copernicus1234 on 2009-06-21
The below command is good for searching for things in the repositories. Here you see that the name is vsftpd, not vsftp.

**sudo apt-cache search vsftp**

```

vsftpd - The Very Secure FTP Daemon

```

---

### Post by bcz on 2009-06-21
Thanks again to the unseen heroes supporting Ubuntu

In my post, I ignored the d for daemon, assuming vsftp was the product name

My thought is that synaptic showed me vsftpd;  I marked it for installation and clicked apply.  The installation failed.


Tried it again.  It now works.  Nice one.  Thanks

Rgds Bill

---

### Post by soltanis on 2009-06-22
Also wrong forum. But I understand. If you posted in General you'd never get an answer.

---

