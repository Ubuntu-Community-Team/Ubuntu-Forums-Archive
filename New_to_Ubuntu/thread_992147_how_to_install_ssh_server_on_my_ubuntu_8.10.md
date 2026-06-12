---
title: "how to install ssh server on my ubuntu 8.10?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by legolas_w on 2008-11-24
I tried to connect from my laptop to my desktop using ssh command and it said connection refused, I think some kind of server is required to be running on the desktop machine, am i correct?

What should I install on the server to make it work?

---

### Post by unutbu on 2008-11-24
On the desktop run:```

sudo apt-get install openssh-server
```

On the laptop run:```

sudo apt-get install openssh-client
```

Then you should be able to ssh from the laptop to the desktop with a command such as:

```
ssh user@desktop
```
(Change 'user' to your username on the desktop,
and change 'desktop' to the ip address or network name for your desktop machine.)

---

