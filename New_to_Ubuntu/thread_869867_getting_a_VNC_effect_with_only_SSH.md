---
title: "getting a VNC effect with only SSH"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Til_Valhall_vi_drar! on 2008-07-25
Hi, i don't even know if this is possible, but im wondering: is it possible to connect to a server that's running a X server or gdm or something, then start an empty X server locally (i mean just type "sudo Xorg :1 >/dev/null &). it is possible to tunnel a connection from the remote X server to your new local X server without VNC and so your local X server is show exactly whats showing on the remote X server, like cloning the remote X server, with only SSH?

---

### Post by jtniehof on 2008-07-25
No, but it's possible to run an X program on the remote machine and have it display locally...the program runs elsewhere, but uses your local X server. Use "ssh -X *servername*" and then type in the name of the program you want to run, e.g.:
```
local:~$ ssh -X remote
Last login: Thu Jul 24 14:10:27 2008
remote:~$ emacs
```
and the emacs window displays on the local machine.

Slow as snot, however.

---

### Post by gimlithedwarf on 2008-07-25
if you want your whole desktop over ssh, you should follow this guide [http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html) for setting it up over vnc, and then type ```
vncviewer --via user@host localhost:1
``` where host is the machine you want to connect to and user is the user you want to login as

---

### Post by The Cog on 2008-07-25
Actually, it is possible to **ssh -X** to a remote server and then run **startx** which puts a full X desktop on your machine. It causes some confusion with the gnome taskbar though. It seems to be pot luck as to whether your local tskbar or the remote taskbar appears on top.

---

### Post by Til_Valhall_vi_drar! on 2008-07-25
> **jtniehof said:**
> No, but it's possible to run an X program on the remote machine and have it display locally...the program runs elsewhere, but uses your local X server. Use "ssh -X *servername*" and then type in the name of the program you want to run, e.g.:
```
local:~$ ssh -X remote
Last login: Thu Jul 24 14:10:27 2008
remote:~$ emacs
```
and the emacs window displays on the local machine.

Slow as snot, however.
ok, but if i want to launch a program on the remote machine, and have it still running when im disconnecting from the server, will that be possible?

---

### Post by jtniehof on 2008-07-29
> **Til_Valhall_vi_drar! said:**
> ok, but if i want to launch a program on the remote machine, and have it still running when im disconnecting from the server, will that be possible?
Nope, that's pretty much what VNC is for. There's some weirdness like Xnest, and there's somebody working on something that will let you move applications from one X server to another, but that's probably at least five years out.

What exactly are you trying to do, and is there a reason VNC can't be part of the solution?

---

### Post by Tteddo on 2008-07-29
> **The Cog said:**
> Actually, it is possible to **ssh -X** to a remote server and then run **startx** which puts a full X desktop on your machine. It causes some confusion with the gnome taskbar though. It seems to be pot luck as to whether your local tskbar or the remote taskbar appears on top.

What's the command to do this if there is already an X server on display 0? This could come in real handy!!

---

