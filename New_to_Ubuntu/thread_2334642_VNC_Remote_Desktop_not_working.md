---
title: "VNC Remote Desktop not working"
date: 2016-08-21
forum: New to Ubuntu
---

### Post by noorquacker on 2016-08-21
I have a Ubuntu 16.04 Desktop computer made of scrap currently being used as a file server, Minecraft server, and is about to also be a web server. Unfortunately, with the lack of monitors and HDMI cables, I can only access it with a VNC viewer. After trial and error over and over a few months ago, I got the VNC built into Ubuntu to work perfectly and it would work on boot, even if there was an unexpected power outage. However, just recently, it has stopped working. The file server and Minecraft server are still working without any problem but when I connect to the computer with VNC is says The connection was refused by the host computer(using VNC Viewer). There was no restarts or reboots otherwise the Minecraft server wouldn't work anymore, and if the VNC server isn't working but the Minecraft server is, since it needs to be manually started, this must mean that the VNC stopped while it was running. Running vino-preferences in an SSH terminal returns the following:
```

Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused

(vino-preferences:26521): Gtk-WARNING **: cannot open display:

```
Running tightvncserver does start it, but creates a new desktop(with a grey screen) which is useless since I cannot access the running terminal hosting the Minecraft server. Can someone tell me how to re-enable vino or another VNC server without duplicating a desktop?

EDIT: Restarting does work, but the Minecraft server is at risk of corruption. I just need vino to start back up again.

---

### Post by steeldriver on 2016-08-21
You could try toggling the state via dconf

```

dconf write /org/gnome/desktop/remote-access/enabled 'false'
dconf write /org/gnome/desktop/remote-access/enabled 'true'

```

If you're accessing from outside the desktop session that's being shared (SSH for example), you may need to prepend the target display

```

DISPLAY=:0 dconf write /org/gnome/desktop/remote-access/enabled 'false'
DISPLAY=:0 dconf write /org/gnome/desktop/remote-access/enabled 'true'

```

BTW is VNC running on a port that's open to the outside world? if it is, that may be why it's dying (under a barrage of unauthorized access attempts)

---

### Post by MartyBuntu on 2016-08-22
Seriously, do yourself a favour and look into TeamViewer (unless you have some objection to closed-source applications).

I banged my head against the wall with VNC solutions for years...until I gave TeamViewer a shot.

---

### Post by dcpifhq on 2016-09-19
Why tightvnc?
I know it is the easiest to install and all, but there are other programs like this guy above me! ^^^
You can try RealVNC, simply download it from the internet!

---

