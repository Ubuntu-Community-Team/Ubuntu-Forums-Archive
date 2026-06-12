---
title: "Ubuntu Server auto start program?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by strixbg on 2008-05-02
I have Shoutcast server on my Ubuntu 6.06.2 LTS Server (without X env.)
I want sc_serv to start every time when system boots. How to do that?

---

### Post by Oldsoldier2003 on 2008-05-02
> **strixbg said:**
> I have Shoutcast server on my Ubuntu 6.06.2 LTS Server (without X env.)
I want sc_serv to start every time when system boots. How to do that?

write a script that launches shoutcast and save it in /etc/init.d the use update-rc.d to set up the script to start/stop the server at boot and runlevel changes.
[http://ubuntujourney.wordpress.com/2008/04/18/starting-a-program-at-boot/](http://ubuntujourney.wordpress.com/2008/04/18/starting-a-program-at-boot/) is a tutorial that should help you understand the process.

---

