---
title: "Epoptes issue"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by ubon on 2012-11-25
Fresh Edubuntu 12.04 install
all updates completed
school network of 20 PCs
Ethernet cable network with Internet connection working fine. DHCP router working fine
Epoptes client on startup applications folder in all PCs
Epoptes server application started on teacher's PC
No LTSP installed

Epoptes application doesn't see any computer at all.
Epoptes window interface is very poor and documentation on the internet is even poorer or too specifical.

I don't really from where to start to fix this, I guess, stupid issue.

---

### Post by gato2707 on 2012-11-25
It looks like you missed change the profesor (server) computer name, or ip address (if it has a static ip address) in each client (student) conf file.

After that changes you must run a:

sudo epoptes-client -c

in each one client PC.

Take a look at my blog. It's wrote in spanish, but you can traslate it with Google. [http://elgatoconlinux.wordpress.com/](http://elgatoconlinux.wordpress.com/)

---

