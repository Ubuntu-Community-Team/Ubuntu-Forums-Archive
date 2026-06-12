---
title: "sudo service ufw status"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by Celegorm77 on 2012-05-25
I noticed in Ubuntu 12.04 there are 2 different kind of ufw are running at the same time

sudo ufw status

sudo service ufw status

Now if I disable the first one, the second one will be running, if I stop the second one, it is fine but after restarting it keeps starting the ufw service, it is not possible to stop it by booting.

Any ideas?

---

### Post by nothingspecial on 2012-05-29
Question moved to it's own thread.

---

### Post by stmiller on 2012-05-29
There's only one running. Those commands are two different things.


One outputs the current firewall configuration:
```

$ sudo ufw status
[sudo] password for stmiller: 
Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
22                         ALLOW       Anywhere (v6)

```

The other tells you if the service is running or not:
```

$ sudo service ufw status
Firewall is running...done.

```

```

$ sudo service apache2 status
Apache is running (pid 17386).

```

---

