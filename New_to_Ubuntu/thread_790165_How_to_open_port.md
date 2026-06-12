---
title: "How to open port?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-11
hi guys,

Im trying to open port in ubuntu.

---

### Post by HunterThomson on 2008-05-11
if you don't have fierstarter or gauarddag installed all ports are open. If you are using fierstarter then it will aromaticity open the port it if the connection start form you computer.

---

### Post by HunterThomson on 2008-05-11
You see iptables is your fierwall and it is built into your kernel. Firestarter and guarddog are GUI's to help you configure it. I would suggest fierstarter because it dose all the work for you. In guarddog all ports are closed and you have to open them it is EZ to figure it out... you just check the box. If the port you want to open is not listed you have to create it and then go back to the tab with all the program ports check and then check the box of the port entry you created. You do have to start guarddog as root in gnome with the comand.

sudo '/usr/bin/guarddog'

You can find both programs in add/remove

---

### Post by appoloin on 2008-05-11
Thanx, i downloaded firestarter and it seems to do the trick

---

### Post by HunterThomson on 2008-05-11
Ya, that is the one I use:) Guarddog was a pain in the ***

---

