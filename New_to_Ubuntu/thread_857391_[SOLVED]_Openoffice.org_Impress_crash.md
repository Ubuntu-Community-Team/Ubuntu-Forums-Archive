---
title: "[SOLVED] Openoffice.org Impress crash"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by aimpau on 2008-07-12
Whenever I start Impress or open a file (*.odp), my whole system crashes that needs to be manually restarted. How come?

---

### Post by red_Marvin on 2008-07-12
You could always try to run it in the terminal and create a log of what it outputs using
*ooimpress > ooimpress.log*
Hopefully you will get som data that can help identify the problem.

Note: If you get a "no java runtime environment" kind of error, it's probably not that, since I get that too and it works fine for me.

---

### Post by aimpau on 2008-07-12
Tried a rather different approach. I tried:

```

dpkg-reconfigure xserver-xorg

```

and enabled the kernel frame buffer something. Seems to be ok. I think I might have enabled the OpenGL / Use Hardware acceleration option in ooimpress which my SIS760 Mirage can't handle.

---

### Post by aimpau on 2008-07-12
Yep. I think it's solved. It even fixed my Abiword crash.

---

