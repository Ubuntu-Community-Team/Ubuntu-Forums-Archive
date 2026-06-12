---
title: "Flash player still not installing"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by anotherghost on 2008-05-19
Hi guys,

I'm running 7.10 on a 4gb Eee PC.  I'm trying to get flash installed but it's not working.  When I go to youtube, it brings up the install missing plugins window, and I go to install flash, but it gives me the message that the flashplugin-nonfree package is already installed.  But, flash stuff still won't play, even after I've restarted firefox/ubuntu.

It's possible that I installed this package earlier and forgot about it, but I don't see why flash stuff wouldn't still play if that was the case.  Anybody have any ideas on what I could do?

Danke.

---

### Post by quelx on 2008-05-19
Open a terminal window (ALT-F2>gnome-terminal)

and type

```
sudo apt-get --reinstall install flashplugin-nonfree
```

and try youtube again.

---

