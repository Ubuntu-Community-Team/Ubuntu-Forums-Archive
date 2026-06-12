---
title: "[SOLVED] Surfing in administrator mode"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by cn108 on 2008-07-20
Hi friends,

Having recently switched from Windows to Ubuntu, I am wondering if it is safe to surf the internet in "administrator mode" (I mean as a user who can ¨Administer the system¨), or is it preferable to surf as a limited user (as in Windows)?

Thank you very much

---

### Post by HokeyFry on 2008-07-20
In linux, you can think of every user who is not root as a limited user. So if you are surfing the internet as your own username, you will be safe, because in order to modyfy sensitive files you would have to run commands with the sudo command, which I doubt you are doing with your browser.

---

### Post by jimrz on 2008-07-20
> **cn108 said:**
> Hi friends,

Having recently switched from Windows to Ubuntu, I am wondering if it is safe to surf the internet in "administrator mode" (I mean as a user who can ¨Administer the system¨), or is it preferable to surf as a limited user (as in Windows)?

Thank you very much

If by "administrator mode" you mean using your normal user with sudo priviledges, you should be fine as you would still need to enter your password in order to perform any actions "as root". On the other hand, surfing "as root"(ie: using gksudo firefox, for example) would be a no-no.

---

### Post by cn108 on 2008-07-21
Hi HokeyFry and jimrz

Thank you very much for your kind help.

---

