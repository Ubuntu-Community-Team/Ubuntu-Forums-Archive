---
title: "offline patch process"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by simonmcnair on 2008-11-11
I installed ubuntu 8.10 on my Dell 1510.  I'm trying to keep it up to date with patches etc but I only have a 3 mobile USB dongle (which worked first time !) which is very slow.  I also have a Macbook Pro VMware fusion and Ubuntu 8.10 installed on it too.  Is there an easy way for me to d/l all the updates in the VM then apply them to the Dell in an offline scenario ?

I was thinking of doing something using /var/cache/apt archives and storing them, but I really don't have a clue how to do it.

Is there an easy way around this ?

cheers
Simon

---

### Post by iponeverything on 2008-11-11
not sure..  

You could try to copy over:

/var/lib/apt/lists
/var/cache/apt/archives

then run update manager and see what it tells you.

---

### Post by simonmcnair on 2008-11-11
I'll give it a go and let you know later.  Thanks !

---

### Post by simonmcnair on 2008-11-11
Thanks very much.  It worked beautifully.  I'm typing my thanks over a slow mobile broadband connection.

All I need now is to fix the volume control cos it's quiet for some reason (there are posts on this in the wild) and try and figure out why the typematic rate seems weird.

thanks again !

---

