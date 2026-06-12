---
title: "Simple Scan - No scanners detected ..."
date: 2012-08-16
forum: New to Ubuntu
---

### Post by cwmoser on 2012-08-16
I've had my MFC-440CN printer scanner working with several
prior Ubuntu releases - but 12.04 just will not recognize the
driver.  The driver installs without error.  There also are
numerous posts that other folks are seeing this same problem.

When I start Simple Scan, I get "No scanners detected".

Running sane-find-scanner does not detect my scanner.
It is a network printer scanner using IP 192.168.0.221
Worked fine in prior releases of Ubuntu.

Is there a fix for this???

Thanks

Carl

---

### Post by cwmoser on 2012-08-16
Got it working now.
Looks like with 64-bit Ubuntu you have to copy /usr/lib64/sane to /usr/lib/sane for it to work.

Carl

---

### Post by kurt18947 on 2012-08-16
> **cwmoser said:**
> Got it working now.
Looks like with 64-bit Ubuntu you have to copy /usr/lib64/sane to /usr/lib/sane for it to work.

Carl

That's true.  I've seen that problem with other manufacturers as well.  I read it might be a problem with alias, a program used to convert .rpm packages to .deb packages.  Guessing the drivers are developed as .rpm then alias is used to produce the .deb package.  Do you have the scanner working for non-sudo users?  There's an edit available if you need it.

---

