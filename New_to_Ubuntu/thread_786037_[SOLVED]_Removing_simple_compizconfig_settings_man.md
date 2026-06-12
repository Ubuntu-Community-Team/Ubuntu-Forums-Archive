---
title: "[SOLVED] Removing simple compizconfig settings manager?"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-07
I installed simple compizconfig settings manager a while ago and I've found that i have no more use for it anymore, how do i remove it?:confused:

thanks in advance

---

### Post by aktiwers on 2008-05-07
```
sudo aptitude remove simple-ccsm
```

Edit: Sorry didn't see the "simple" in the name..  I fixed the command

---

### Post by kamitsukai on 2008-05-07
oh that makes sense just like when i installed it with

```
sudo apt-get install compizconfig-settings-manager 
```

your just replacing install with remove:lolflag: ill remember that thanks

---

### Post by aktiwers on 2008-05-07
Yes exactly :)
Though I changed the command - but yeah.

I thought you where talking about this:
[http://www.ubuntugeek.com/simple-compizconfig-settings-manager-in-ubuntu-804hardy-heron.html](http://www.ubuntugeek.com/simple-compizconfig-settings-manager-in-ubuntu-804hardy-heron.html)

---

### Post by Joeb454 on 2008-05-07
You can either do this through Add/Remove or Synaptic Package Manager.

Or if you want to use the terminal - you can use ```
sudo aptitude remove compizconfig-settings-manager
```

---

