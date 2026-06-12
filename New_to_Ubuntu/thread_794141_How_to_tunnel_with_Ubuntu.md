---
title: "How to tunnel with Ubuntu"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by kc5hwb on 2008-05-14
Is there a program, or a cmd line string, that would allow you to SSH Tunnel, similar to what can be done in Putty with Windows?

---

### Post by Het Irv on 2008-05-14
Putty....
It has a Linux port

```
sudo apt-get install putty
```

---

### Post by SunnyRabbiera on 2008-05-14
putty is available in linux too, so you know

---

### Post by jimv on 2008-05-14
YOu want Gnome SSH Tunnel Manager
[http://www.ubuntugeek.com/manage-ssh-tunnels-with-gnome-ssh-tunnel-manager.html](http://www.ubuntugeek.com/manage-ssh-tunnels-with-gnome-ssh-tunnel-manager.html)

You CAN do it with SSH, and it's pretty easy, but the gui is more funner.  HEre's the instructions for using just SSH in the command line:
[http://wiki.freaks-unidos.net/weblogs/azul/firefox-ssh-tunnel](http://wiki.freaks-unidos.net/weblogs/azul/firefox-ssh-tunnel)

EDIT:
I just set this up the other day so I can browse around my work proxy.  Another nice tool to have after you set up Gnome SSH Tunnel Manager is AllTray.  AllTray lets you click on any open Window and dock it in the task tray...and it automatically saves that info so the next time you open whatever program you docked before, it also opens in the task tray.  Gnome SSH Tunnel Manager has to be open to be managing your connections, but minimizing it is a bit annoying...so using AllTray solves that problem.

---

### Post by jimv on 2008-05-14
You don't need Putty in Ubuntu.  There's already a command line SSH client aptly called "SSH".  You just type 'ssh yourservernameorIP' and that's it.

---

### Post by bodhi.zazen on 2008-05-14
If you like you may use putty, it is a nice interface and offers advanced features. More important, if you have putty keys you can use them with putty on linux.

If you want to use the command line you can as well. see this link, which reviews port forwarding as well.

[uwiki]SSHHowto[/uwiki]

And 

[uwiki]VNCOverSSH[/uwiki]

---

### Post by kc5hwb on 2008-05-14
thanks, those all sound great.  I didn't know there was a Putty in Ubuntu, but I will install that now.

---

