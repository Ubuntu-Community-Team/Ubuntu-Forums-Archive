---
title: "[SOLVED] How do you remove sudo from Damn Small Linux?"
date: 2008-03-20
forum: Other OS Talk
---

### Post by Erwin Criddle on 2008-03-20
Hi, I'm bringing an old pc back to life and was wondering how to remove sudo off the linux distro?

Any ideas?

---

### Post by 67GTA on 2008-03-20
What are you trying to do? It is compiled into the distro, so removing it will probably break a lot of stuff.

---

### Post by Bungo Pony on 2008-03-20
Why on earth would you want to remove it?

If it's to run everything as root, you could go with Puppy :)

---

### Post by kerry_s on 2008-03-20
it would be better if you asked robert on the dsl forums, after all he built it and would know better if you can or cannot.
[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi)

i would recommend you use sudo it's safer. running as root you cut the security in half and stand more of a chance of screwing up your system.

if you tell us what your trying to do, we can tell you how to do it the right way without compromising security.

---

### Post by Erwin Criddle on 2008-03-20
The truth is, that I need to specify which users can use sudo.
Is there any way of specifying this?

---

### Post by notwen on 2008-03-20
> **Erwin Criddle said:**
> The truth is, that I need to specify which users can use sudo.
Is there any way of specifying this?

Don't tell the certain users the sudo password?

---

### Post by LaRoza on 2008-03-20
> **Erwin Criddle said:**
> The truth is, that I need to specify which users can use sudo.
Is there any way of specifying this?
```

visudo

```

You can.

---

### Post by TheOrangePeanut on 2008-03-20
Take a look at this link

[http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/](http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/)

---

### Post by Erwin Criddle on 2008-03-21
Thanks a lot!
This has answered my question!!  :)

---

