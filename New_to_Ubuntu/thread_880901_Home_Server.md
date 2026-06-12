---
title: "Home Server"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Mauler5858 on 2008-08-05
Im working on my home server at the moment and I was wondering from people who have done the same, what do you reccomend or ideas for a home server that will make this little box more than i already have.  Currently i have:

Ubuntu 8.04 Server(and i plan to keep it CLI only)

is configured as LAMP

Samba(file sharing only right now....im still working on the DC part)

Squid(still tweaking out, but i havent made it invisible yet)

BIND is still in the works.

I also have webmin installed.

---

### Post by dca on 2008-08-05
My home server consists of nothing more than openSSH (connecting to it via CLI) to make changes or update and Samba (file sharing/storage).  It's just a mass file storage and back-up device so it doesn't need anything special.

 
...the more services you have installed, the more you have to monitor it.  If LAMP is installed and it faces the internet be careful of DDoS and hacking and etc etc.

---

