---
title: "how to upgrade 8.04 server to 8.10 server"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by LRT on 2008-11-14
how can i upgrade 8.04 server to 8.10 server??? this would not be done through update manager... this would be done all on the command line. how can i do this?

---

### Post by LRT on 2008-11-14
found this:

[http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-server-to-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-server-to-ubuntu-810-intrepid-ibex.html)

giving it a try....

---

### Post by cariboo on 2008-11-14
If your server is running with no problems, there is no compelling reason to upgrade. If there is something that you need that is in Intrepid, but not hardy, the way to upgrade is to edit /etc/apt/sources.list and change all instances of Hardy to Intrepid, and save the file, then at the prompt type:

```
sudo aptitude update
```

then use either:

```
sudo aptitude safe-upgrade
```

or

```
sudo aptitude full-upgrade
```

I prefer aptitude to apt-get as aptitude seems to be a bet safer than apt-get.

Jim

---

