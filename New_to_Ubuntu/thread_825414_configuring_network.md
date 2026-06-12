---
title: "configuring network"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by hungryOrb on 2008-06-11
Hello!
IS there a way to configure the network, to a hard line, after installing ubuntu server edition? Only got the CLI, and am wondering whether it's just easier to re-install and configure the network inside the install!
Thanks for considering!

---

### Post by bluepowder7 on 2008-06-11
do you mean to set a static IP on the server box?  the "ubuntu server guide" steps you through that, i think.  at least that's what i recall using when i set my server IP to static.

---

### Post by sam_delta on 2008-06-11
try using this tool```

ifconfig
```

to read the manual ```
man ifconfig
```
also, you might find this tutorial usefull (configuring ethernet interface from command line)
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html#more-98](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html#more-98) <<<<--- this is good
[http://news.softpedia.com/news/Configuring-the-Ethernet-interface-from-the-command-line-33262.shtml](http://news.softpedia.com/news/Configuring-the-Ethernet-interface-from-the-command-line-33262.shtml)

sam

---

