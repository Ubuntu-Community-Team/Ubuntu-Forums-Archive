---
title: "Some questions about execute a shell program when startup"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by amazingjxq on 2008-11-27
I added that program to the session. But i wonder can i add a program that need to be root to execute to the session? You know,in the terminal we are asked for the password.

---

### Post by kpkeerthi on 2008-11-27
You can add it to /etc/rc.local

Commands or script files added to /etc/rc.local will be run with root privilege.

---

### Post by Dedoimedo on 2008-11-27
Yes you can.

On non-debian systems, simply add it to rc.local.

On Debian-based distros, see this:
[http://www.debian.org/doc/FAQ/ch-customizing.en.html](http://www.debian.org/doc/FAQ/ch-customizing.en.html)

Under:
11.6 It looks as if Debian does not use rc.local to customize the boot process; what facilities are provided?

To do this, you need to sudo, so you'll be able to add those things that require sudo normally ...

Dedoimedo

---

