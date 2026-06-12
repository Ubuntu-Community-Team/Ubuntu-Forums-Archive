---
title: "proxy setting (config) file"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Makhi on 2008-07-24
Is there a (config) file that has the current proxy settings on ones machine, so that when i make a change i can see that it has been made?

---

### Post by The Cog on 2008-07-24
I don't know. What I do know is that there is a config file in /root/.synaptic that synaptic uses.

I also know that using a command like:
export http_proxy=http://1.2.3.4:8080
causes apt-get and aptitude to use that proxy when contacting the repositories.

---

