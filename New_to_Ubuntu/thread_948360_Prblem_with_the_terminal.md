---
title: "Prblem with the terminal"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by joyson20 on 2008-10-15
when i start the terminal it comes as [email]myname@elcot-laptop:-$....if[/email] i give any command it says unable to resolve host elcot-laptop....the thing is i had the adminstrative rights under the account elcot...but i deleted that account and created a new account in my name and gave the admi rights to that account ...can anyone help me with this please

---

### Post by beercz on 2008-10-15
Create a file: /etc/hosts

In that file put in:

127.0.0.1    localhost
127.0.1.1    elcot-laptop

If elcot-laptop is not the correct name, type hostname in terminal and use that name instead.

---

### Post by hyper_ch on 2008-10-15
you need to reboot in recovery mode and apply those changes to /etc/hosts.

---

### Post by beercz on 2008-10-15
> **hyper_ch said:**
> you need to reboot in recovery mode and apply those changes to /etc/hosts.
yep - quite right, forgot that bit!! (Phone rang).

Thanks hyper_ch

---

