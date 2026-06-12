---
title: "[SOLVED] PC to Xbox"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by Glurf on 2008-11-30
Hey, I'm trying to sync my pc media (Music, videos, etc) with my xbox. I'm running Ubuntu 8.10, and I was wondering if there was an app for doing that, since I don't have access to windows media center. Does anyone here know of such an app?

---

### Post by SSTwinrova on 2008-11-30
MediaTomb should do what you want nicely

[http://packages.ubuntu.com/intrepid/mediatomb](http://packages.ubuntu.com/intrepid/mediatomb)

[http://mediatomb.cc/](http://mediatomb.cc/)

---

### Post by nhasian on 2008-11-30
i havent tried media tomb, but I highly recommend uShare.  it works great!  I've also tried fuppes which has more features, but also is more buggy.

---

### Post by kernel tom on 2008-12-03
completely agree with nhasian.  uShare is f*cking amazing... the only thing I don't like is how the 360 organizes my music...

I'm thinking of starting a post for that but the video playback works fine which is what i was going for.

kt

---

### Post by Glurf on 2008-12-03
Haven't been able to get uShare working, so anyone know another program?

---

### Post by nhasian on 2008-12-03
oops!  dont give up on ushare!  we'll help you get it up and running.  here's what my /etc/ushare.conf looks like if that helps you:

```
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=wlan0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49153

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=1337

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/nhasian/videos

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=yes

# Enable Web interface (yes/no)
ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=no

```

please note i'm using my wifi adaptor so its wlan0 if your using your ethernet it will be eth0 instead.

---

### Post by nakama85 on 2008-12-03
[HOW TO: The Ultimate XBOX 360 Multimedia Sharing Guide]("http://ubuntuforums.org/showthread.php?t=848144")

This is currently at the top of the list in Tutorials section of the forums

---

### Post by Glurf on 2008-12-05
Alright I got it working. Thanks

---

### Post by nakama85 on 2008-12-05
> **Glurf said:**
> Alright I got it working. Thanks

What was your solution?

Don't forget to thank (clicking the thanks ribbon) anyone who helped with the solution. Even if it was not me the others may deserve it.

---

### Post by Glurf on 2008-12-11
> **nakama85 said:**
> What was your solution?

Don't forget to thank (clicking the thanks ribbon) anyone who helped with the solution. Even if it was not me the others may deserve it.

Sorry for the late response, just a small user error... I figured out what I had to do. Also I thanked the appropriate people

---

