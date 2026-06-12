---
title: "how to enter a lang (like telgu or tamil) in gtk application?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by gaurav12345 on 2008-08-18
hi,
 i am new to gtk programming.
i want to design a application that would have entries in the language i desire like telgu or kanada etc. (mainly indic language).
i have learnt to display stored message in different languages or button captions using gettext utility and even to enter different languages using xkb and scim on terminal or gedit. but now i am stuck if i design a application using gtk text widgets like gtktextview than  how to let user chose a language of his choice.
for entry and enter. i have read gtkmulticontext etc. could be useful but i not finding any example of how to use it.
if anybody could help me in this...
thanx in advance.

regards
gaurav12345

---

### Post by Pro-reason on 2008-08-18
You should probably install SCIM.

---

### Post by gaurav12345 on 2008-08-18
i have used scim in gedit but i am not getting how to get it in my gtk programme.
gaurav12345

---

### Post by Pro-reason on 2008-09-11
Gedit is a Gtk program.

---

### Post by SivaneshR on 2008-10-01
To type in any indic languages using SCIM you must install additional tables for SCIM with all dependencies. Even then if SCIM is not Working in OO or similiar apps then visit [https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM) to do additional configurations required to make it work:guitar:

---

