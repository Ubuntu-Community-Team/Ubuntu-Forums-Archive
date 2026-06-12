---
title: "[SOLVED] root"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Toliot on 2008-08-12
i am confused so all linux systems have a root user?
how do i log into this user if the password wasnt changed?
thx in advance :)

---

### Post by sandysandy on 2008-08-12
u do not need to log in as root.

use command [COLOR="Blue"]sudo[/COLOR] instead for temporary root privileges.

password will be same as ur user password.

regards

---

### Post by Toliot on 2008-08-12
> **sandysandy said:**
> u do not need to log in as root.

use sudo instead

but tell me how do i login root

---

### Post by kk0sse54 on 2008-08-12
You can't login in as root since it's disabled by default in Ubuntu. Like the previous post use sudo in order to gain root privileges.

---

### Post by Toliot on 2008-08-12
> **C!oud said:**
> You can't login in as root since it's disabled by default in Ubuntu

can i un-disable it?
and if i can how?

---

### Post by finer recliner on 2008-08-12
> **Toliot said:**
> can i un-disable it?
and if i can how?

[https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account](https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account)

---

### Post by sandysandy on 2008-08-12
why do u want to log in as root, if i may ask.

regards

---

### Post by kk0sse54 on 2008-08-12
Why would you want to undisable it? It's disabled for a reason in order to protect you. It's a really really bad idea to login as root due to security reasons which is why you only log in temporarily using sudo

---

### Post by iaculallad on 2008-08-12
> **Toliot said:**
> can i un-disable it?
and if i can how?

To become get your root privilege, you could just input the command below on your terminal using your own password:

```
sudo -i
```

---

### Post by Toliot on 2008-08-12
> **C!oud said:**
> Why would you want to undisable it? It's disabled for a reason in order to protect you. It's a really really bad idea to login as root due to security reasons which is why you only log in temporarily using sudo

ok it worked im trying to edit local purge (if thats it ^o) ) but anyways i got it to work thx :)

---

