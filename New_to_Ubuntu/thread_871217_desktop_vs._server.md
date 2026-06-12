---
title: "desktop vs. server"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by murrayE on 2008-07-26
Do I understand correctly that, unlike some other distributions, the server version of Ubuntu does NOT contain everything that the desktop version contains?

I ask because I'm not sure which version, desktop or server, to install. I do want everything in the desktop version. However, I also want to set up, strictly for prototyping use -- via localhost -- Apache HTTP server, PHP, and My SQL (along with WordPress and MediaWiki plus LaTeX plugins).

---

### Post by Flyingjester on 2008-07-26
well, you could get the desktop version and then download all the packages for the things that you need.

---

### Post by Ryadt on 2008-07-26
You have to bear in mind that the server version is CLI.

---

### Post by murrayE on 2008-07-26
> **Flyingjester said:**
> well, you could get the desktop version and then download all the packages for the things that you need.

Does your answer imply that the server version does *not* include the desktop packages?

Are the kernels the same, and if not, do I need the server version kernel in order to get the needed functionality of Apache?

---

### Post by Growbag on 2008-07-26
The server version has no graphical desktop, and no "user" stuff like openoffice and the like.

The kernel is also configured more for network throughput as well.

It's not really necessary for the "hobby server" or home server.

---

### Post by murrayE on 2008-07-26
> **Growbag said:**
> The server version has no graphical desktop, and no "user" stuff like openoffice and the like.

The kernel is also configured more for network throughput as well.

It's not really necessary for the "hobby server" or home server.

Thanks! That makes it quite clear now.

---

### Post by Ryadt on 2008-07-26
> **murrayE said:**
> However, I also want to set up, strictly for prototyping use -- via localhost -- Apache HTTP server, PHP, and My SQL (along with WordPress and MediaWiki plus LaTeX plugins).

You can install the LAMP server on the desktop version to act as a webserver.

---

