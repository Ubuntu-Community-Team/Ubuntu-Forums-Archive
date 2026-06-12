---
title: "How to update Ubuntu manually?"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by albertgrain on 2008-06-16
I have just setup a Ubuntu server. But I was informed that that server is prohited from visit other servers, i.e., it can only provide services for other machine.

So it is impossible to update Ubuntu manually by CDROM? Or, is there some services that can do the update passively (update by answering a update request from Ubuntu FTP servers)

Thank you!

---

### Post by imneo on 2008-06-16
You shuld look for apt souecr list for your dist (google)
modify your /etc/apt/source.list

then do :
```

apt-get update
apt-get upgrade
apt-get dist-upgrade

```

there are full guides for this at [http://www.scripts-net.com]("http://www.scripts-net.com")

---

### Post by cariboo on 2008-06-16
How have you got your server connected to the internet?

Jim

---

### Post by imneo on 2008-06-16
you need to edit your /etc/network/interfaces file

---

