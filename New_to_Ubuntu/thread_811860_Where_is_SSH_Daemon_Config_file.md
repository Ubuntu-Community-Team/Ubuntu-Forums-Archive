---
title: "Where is SSH Daemon Config file?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by sysopl on 2008-05-29
> Firstly on the server we must configure the ssh daemon to accept and forward incoming connections from other hosts than localhosts. This is done  by setting the GatewayPorts configuration directive to “yes”.
>  Include the line:

GatewayPorts yes


I want to do this but I cannot find the sshd_config file

In FreeBSD it is here:
/etc/ssh/sshd_config

Where is it in ubuntu h.heron?

---

### Post by quelx on 2008-05-29
> **sysopl said:**
> I want to do this but I cannot find the sshd_config file

In FreeBSD it is here:
/etc/ssh/sshd_config

Where is it in ubuntu h.heron?

make sure it's installed ```
sudo apt-get install openssh-server
``` and you should find it at the same spot **/etc/ssh/sshd_config**

---

### Post by sysopl on 2008-05-29
lol it was there all along.

Thanks.

---

### Post by sysopl on 2008-05-29
And how can I kill SSHD now? It needs to be restarted

I just know in FreeBSD it's
```
killall –HUP sshd
```

---

### Post by amingv on 2008-05-29
Try:

```
sudo /ect/init.d/ssh stop
```

or
```
sudo killall sshd
```

---

### Post by finer recliner on 2008-05-29
```
sudo /etc/init.d/ssh restart
```

---

### Post by Flare183 on 2008-05-29
~/.ssh/  Somewhere in there.

---

