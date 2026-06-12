---
title: "Installing VNC on a headless system"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by dolphin194 on 2013-10-23
I know this kind of sounds pointless, but I want to install VNC on a headless system running Ubuntu 12.04. There is no X server installed on the system, and I want my VNC to display what's on the monitor remotely.

Also, I know that I can do this all through SSH (in fact it would probably be easier), but I want to know if there actually is a VNC server for a headless system without X.

Again, I do not want to install any X server nor do I plan to run any X applications. I just want to be able to access only the terminal through VNC.

---

### Post by ian-weisser on 2013-10-23
Try the *linuxvnc* package.

```
Description-en: VNC server to allow remote access to a tty
 linuxvnc can export your currently running text sessions to any VNC client.
 It can be useful if you want to move to another computer without having to
 log out or to help a distant colleague solve a problem.
```

---

### Post by dolphin194 on 2013-10-24
Thank you. That is exactly what I was looking for

---

