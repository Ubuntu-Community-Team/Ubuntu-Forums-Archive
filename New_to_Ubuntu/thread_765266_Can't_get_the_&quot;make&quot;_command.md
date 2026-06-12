---
title: "Can't get the &quot;make&quot; command"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Ritho on 2008-04-24
Am trying to compile a small program I have just downloaded but everytime I key the "make" command I get a reply "command not found"! What could be the problem? Someone help please.:confused:

---

### Post by jocko on 2008-04-24
> **Ritho said:**
> Am trying to compile a small program I have just downloaded but everytime I key the "make" command I get a reply "command not found"! What could be the problem? Someone help please.:confused:

You'll need to install build-essential. Find it in synaptic or type:
```
sudo apt-get install build-essential
```in a terminal.

---

