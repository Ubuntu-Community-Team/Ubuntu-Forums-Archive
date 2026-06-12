---
title: "Can't get the &quot;make&quot; command"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Ritho on 2008-04-24
Am trying to compile a small program I have just downloaded but everytime I key the "make" command I get a reply "command not found"! What could be the problem? Someone help please.:confused:

---

### Post by cubeist on 2008-04-24
Do you have the build-essential package installed?

---

### Post by lizzard on 2008-04-24
You need the "build-essential" package installed which contains the necessary programs for compiling from source. 
```
sudo aptitude install build-essential
```

---

### Post by rustutzman on 2008-04-24
Have you installed the build-essential package through synaptic?

Russ

---

### Post by Ritho on 2008-04-24
Not as yet.:) Let me get them installed. Will post by progress. Thank you.

---

### Post by swoll1980 on 2008-04-24
While doing the make you will likely get errors about packages missing just keep installing the the missing packages(dependencies) until make finishes with out errors

---

