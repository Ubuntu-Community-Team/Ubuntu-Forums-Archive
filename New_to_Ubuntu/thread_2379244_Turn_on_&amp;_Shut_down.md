---
title: "Turn on &amp; Shut down"
date: 2017-12-02
forum: New to Ubuntu
---

### Post by santoshbadolan on 2017-12-02
Hi friends I want to know when I turn on my pc it is checking all the drives and give OK(in green colour) and same give when I shut down  it.[ATTACH=CONFIG]277718[/ATTACH][ATTACH=CONFIG]277719[/ATTACH]
I want to know what is this and what are the commands for it.
Thank you

---

### Post by DuckHook on 2017-12-03
Welcome to the forums, santoshbadolan.

Those are all of the different services that collectively make up what you think of as a simple computing session. The green "OK" means that the services were all started properly or stopped properly. 

If you want to see these same services in log format, open a terminal and type:```
dmesg
```

---

### Post by Yellow Pasque on 2017-12-03
[https://www.freedesktop.org/wiki/Software/systemd/](https://www.freedesktop.org/wiki/Software/systemd/)

---

