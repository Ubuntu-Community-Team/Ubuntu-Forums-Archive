---
title: "vinoi server issue - cant connect xp to hardy"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by mielie007 on 2008-04-26
hopefully someone can help

i have recently upgrade my server from feisty to hardy. i had just got the vnc working with vino under localhost connection and then i did the upgrade and now i can get it working again. i have looked on the net, i can't find anything that can tell me how to resolve the problem.

i tried this command to activate vncviewer

```
vncviewer localhost:0
```

then i get the following error :confused:

[HTML]VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Sun Apr 27 00:49:08 2008
 main:        unable to connect to host: Connection refused (111)
[/HTML]

i have gone to system >> preferences >>remote desktop and enabled 
[LIST]
[*] Allow other users to view your desktop
[*]A Allow other users to control your desktop
[/LIST]


please can someone give me some guidance to resolve this issue

---

### Post by NigO on 2013-02-20
You can run ```
sudo lsof -i -n
``` to see what ports are available, there should be something on port 5900 for VNC.

It's likely that the server isn't running

---

### Post by oldos2er on 2013-02-20
Old thread closed, please don't bump old threads.

---

