---
title: "Synaptic issues with proxy servers"
date: 2005-02-05
forum: Repositories &amp; Backports
---

### Post by MYOB on 2005-02-05
As soon as I set a http or ftp proxy server in Synaptic, it becomes unable to show packages. I get the sectional listing, and can update the headers, etc, but package listings are not shown, at all.

Is this a known problem with synaptic in Ubuntu? Its not a problem with apt-get, as apt-get works perfectly with my proxy server.

---

### Post by drasko on 2005-02-13
I belive it's a firewall issue. Something's wrong there with synaptic, the settings doesn't seem to effect it - it just goes for the some locked port (and not to proxy port)...
I solved that problem by removing synaptic package and building it from the source.
Before that do apt-get build-dep synaptic to get all dependencies you need for build...

Drasko

---

