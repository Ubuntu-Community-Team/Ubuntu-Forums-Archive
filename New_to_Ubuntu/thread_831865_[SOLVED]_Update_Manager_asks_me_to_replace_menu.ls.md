---
title: "[SOLVED] Update Manager asks me to replace menu.lst"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Dani Filth on 2008-06-17
Hi all,

When the Update Manager performs updating and it asks me if I want to replace the current menu.lst with a new one, I chose to keep the current one. But recently, I notice that if I choose to keep the old current menu.lst, it doesn't update the latest version of kernel. For instance, there are several different versions such as 2.6.24-16, 2.6.24-17, 2.6.24-18, 2.6.24-19 but in menu.lst, only the kernel 2.6.24-16 is used. 

So I wonder is it "safe" for me to manually edit the file and use the 2.6.24-19 version (this is supposed to be the latest version, am I right?) or just wait till the next update then choose to replace menu.lst with the new one.

Thanks! :D

---

### Post by kpkeerthi on 2008-06-17
I choose "packager's version" when prompted. All my customizations remained intact.

---

### Post by chunchengch on 2008-06-17
> **Dani Filth said:**
> ...So I wonder is it "safe" for me to manually edit the file and use the 2.6.24-19 version...

yes, it is safe to edit the menu.lst manually, just be sure the UUID is correct.

---

