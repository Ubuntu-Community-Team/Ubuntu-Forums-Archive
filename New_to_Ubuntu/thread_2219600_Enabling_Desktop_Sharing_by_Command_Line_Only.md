---
title: "Enabling Desktop Sharing by Command Line Only"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by CelticWhisper on 2014-04-24
I just upgraded to 14.04 last night and while I can SSH into my system, it seems my desktop sharing (vino?) configuration was reset and the host is not responding to VNC connections.

I found this thread:
[http://ubuntuforums.org/showthread.php?t=266981&highlight=vnc](http://ubuntuforums.org/showthread.php?t=266981&highlight=vnc)

which details configuring screen sharing via CLI, but it requires some degree of GUI access to the system either by remote X session (which I will readily admit is outside my realm of experience) or by physically having access to the keyboard and mouse.  As I'm trying to do this over a TeamViewer connection to a Windows PC on my home LAN (Office PC--(TeamViewer)-->Home Win7 PC--(SSH)-->Ubuntu HTPC) that's not an option.

Yes, I could, and most likely will, wait until I get home and configure it the old-fashioned way, but in the interest of community support, how would one go about switching on desktop sharing from an out-of-the-box "factory"-original state if one was not able in any way to interact with the Ubuntu system graphically?

I read through the linked thread until the discussion turned to base64 hashed VNC passwords, at which point I thought there must be a simpler way.

Help?

---

### Post by steeldriver on 2014-04-24
AFAIK vino-server has used a base64 encrypted VNC password since at least 12.04, I think it's more likely you're bumping up against the recent change in the default value of the require-encryption parameter, which some clients can't handle - or that the vino-server simply got disabled

Regardless, yes you should be able to configure over SSH using gsettings - the trick (which works for 12.04 at least) is to set the DISPLAY environment variable so that gsettings can hook into the active desktop session e.g.

```

DISPLAY=:0 gsettings get org.gnome.Vino enabled

DISPLAY=:0 gsettings get org.gnome.Vino require-encryption

```
then if/as necessary
```

DISPLAY=:0 gsettings set org.gnome.Vino enabled true

DISPLAY=:0 gsettings set org.gnome.Vino require-encryption false

```

Please make sure you are tunneling the connection over SSH though - by setting the network-interface value to 'lo' and/or firewalling the VNC port(s)

---

