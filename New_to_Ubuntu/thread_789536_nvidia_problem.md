---
title: "nvidia problem?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Benbow on 2008-05-10
My graphics are running slowish and jerky. I have received the following, how do I process it?
My card is a GeForce 7300 LE

The message is:
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by dorkdork777 on 2008-05-10
I'm not too knowledgeable with that particular problem, but what the message is telling you to do is to run this command in the Terminal:
```
sudo nvidia-xconfig
```
("sudo" means "super user do", and "super user" basically means "root", so it means "root do" - "do as root".)
And once that's done, do a Control-Alt-Backspace (not Ctrl-Alt-Del). This is the key combo to restart the X server.

---

### Post by grannyw on 2008-05-10
Get "Envy",and find there nvidia drivers to install,maybe its a drivers issue

---

### Post by Nythain on 2008-05-10
or dont get envy and risk fubaring everything and just use synaptic and get the
nvidia-glx-new
package, then in a terminal type the above, wich will change teh driver in xorg.conf from the free and crappy nv to the proprietary and awesome nvidia

---

