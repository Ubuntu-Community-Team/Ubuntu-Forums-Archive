---
title: "Opening a port in Ubuntu"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by drbk563 on 2008-05-10
How do I open a port in Ubuntu? For example if I would like to ssh into my linux box, how can I open port 22?


Thank You

---

### Post by barbedsaber on 2008-05-10
if your running hardy, try```
ufw allow 22/tcp
```


I dont really know, I am guessing from the man page.

---

### Post by Monicker on 2008-05-10
> **drbk563 said:**
> How do I open a port in Ubuntu? For example if I would like to ssh into my linux box, how can I open port 22?


Thank You

By default no ports are blocked in Ubuntu.  Did you enable any firewalling rules?

If you are trying to ssh to your linux machine at home from an external site, then you may need to do port forwarding at your router.


Also, did you install the ssh server package?

```
sudo apt-get install openssh-server
```

---

### Post by drbk563 on 2008-05-10
I did not enable any firewall rules. I did not get the openssh-server package. I thought that by default Ubuntu was an SSH server?

Thank you

---

### Post by Monicker on 2008-05-10
No, for some reason it is not installed by default on Ubuntu.  I know that other distros such as RHEL/Fedora and Debian do install it by default.

---

### Post by drbk563 on 2008-05-10
Thank you it is working now. After I installed the package.

---

