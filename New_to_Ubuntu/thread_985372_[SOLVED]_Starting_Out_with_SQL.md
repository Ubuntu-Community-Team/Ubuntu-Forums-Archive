---
title: "[SOLVED] Starting Out with SQL"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by nixforme on 2008-11-17
HI,

Can come one tell me a good way to get started with MySQL. I installed it but I cant get it to work. Maybe I didn't install it right. I did:

```
sudo apt-get install mysql
```

Also can someone recommend me a good guide that can help me learn mysql?

Thanks!

---

### Post by LowSky on 2008-11-17
this will give you a GUI and admin access for SQL

```
sudo apt-get install mysql-gui-tools-common mysql-admin
```

---

### Post by bgervasi on 2008-11-17
yes once the installation is done, than you can run mysql-admin and enter the root password you setup during the mysql install.

In terms of guides, you can google search mysql tutorials or go the the mysql.com and use the reference manual.

---

### Post by nixforme on 2008-11-17
Thanks for the info. I was doing some digging and I found XAMPP. Would this be a good place to start out? WHat can you tell me about this? is it worth it?

---

### Post by WorldTripping on 2008-11-17
The easiest way to install a LAMP stack is to open Synaptic, and choose Edit | Mark Packages By Task.

Then tick the LAMP Server box.

Cheers

---

### Post by WorldTripping on 2008-11-17
Oh, and after that you might want to install phpmyadmin to administer the SQL tables etc.

---

