---
title: "PHP and Apache Need Help"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Zeck on 2008-05-13
Hi all,
I have a problem for php and apache. When my internet broken, my apache didn't work. How to solve this problem. Help me !!!!!!!!!!!!

---

### Post by nowshining on 2008-05-13
what do u mean? are u using dyndns? did u update the hosting domain site with ur new url?

if it's not hat in the terminal:

sudo /etc/init.d/apache2 restart

---

### Post by Zeck on 2008-05-13
Sorry I make mistake. When my internet disconnect, my php or apache didn't work. My webroot located in /var/wwww/....... How to solve this problem ? Should i explain my problem with picture ?

---

### Post by superprash2003 on 2008-05-13
are you trying to access your apache server from outside your network? or within your computer? do you use any service like dyndns or noip .. which ip do you see to connect to the internet

---

### Post by nowshining on 2008-05-13
ah it was late last night for me- i meant ip in my question/post.. :) not url...

u can use ddclient in the repositories for auto-updating the ip when ur ip changes. ie: when u get a blackout from ur modem,etc..and then get re-connected, etc..

---

