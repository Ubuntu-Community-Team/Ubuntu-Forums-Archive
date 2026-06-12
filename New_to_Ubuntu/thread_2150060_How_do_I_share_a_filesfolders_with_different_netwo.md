---
title: "How do I share a files/folders with different networks?"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by rom3lol on 2013-05-30
Is it possible to share files/folders with people on different networks? I need to share some files thanks.

---

### Post by papibe on 2013-05-30
Hi rom3lol.

The simplest way is to install openssh-server, and create an account for sharing files over sftp.

On the client side, they could use Filezilla or WinSCP on Windows, Filezilla or Nautilus on Ubuntu, and even a Firefox plugin called FireFTP for an platform independent option.

Note that one machine's ability to access the other, will depend on how well setup are your networks (well setup routes and proper local DNS services).

Let us know how it goes.
Regards.

---

### Post by siddharth007 on 2013-05-31
Adding to rom3lol question.Is it possible to setup Samba server for sharing files between different networks??

---

### Post by HiImTye on 2013-06-01
> **siddharth007 said:**
> Adding to rom3lol question.Is it possible to setup Samba server for sharing files between different networks??

you can set up an ssh tunnel, or set up a vpn
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

