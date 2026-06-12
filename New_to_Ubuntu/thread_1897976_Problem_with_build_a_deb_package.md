---
title: "Problem with build a deb package"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by redpower1989 on 2011-12-20
I try to build a deb package with this command > sudo dpkg --build namefile  and i have this error
> dpkg-deb: error: script `postinst 'has wrong permits 664 (need> = 0755 and <= 0775)How can i solve that?

---

### Post by matt_symes on 2011-12-25
Hi

Open a terminal and type

[CODE]chmod 755 /path/to/postint/CODE]

Then build again

Kind regards

---

