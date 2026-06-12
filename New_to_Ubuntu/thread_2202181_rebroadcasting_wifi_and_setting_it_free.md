---
title: "rebroadcasting wifi and setting it free"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by cholby on 2014-01-27
Hi there.  My apartment's internet is my only option, and they give you a code once a month which allows you to log in ONE (1) Mac/Hardware address at a time.  Logging in another device boots the original device.

So I got a cheap old laptop and put on Ubuntu Server.  I also bought a cheap wifi NIC.  I'd like this laptop to log into the apartment's network with its MAC address and run a DHCP server on the other end.  The antenna is hanging from my window in a tree, so the SSID is "treenet"

I'm hoping somebody can give me a step-by-step on the command line.  It looks like Ubuntu recognized both NICs immediately (yay).

Thank you,
Emma

---

### Post by Iowan on 2014-01-27
The apartment doesn't allow routers (which would present one MAC address to the service)?
Network Manager has a sharing option... but the Server version doesn't come with NM.

A few ICS (internet connection sharing) articles I found:
[http://www.webupd8.org/2009/02/ubuntu-internet-connection-sharing.html](http://www.webupd8.org/2009/02/ubuntu-internet-connection-sharing.html)
[http://askubuntu.com/questions/295418/ubuntu-server-as-an-internet-server](http://askubuntu.com/questions/295418/ubuntu-server-as-an-internet-server)
[http://ubuntuforums.org/showthread.php?t=2171522](http://ubuntuforums.org/showthread.php?t=2171522)

---

### Post by cholby on 2014-01-27
Thanks for the resources.  Routers are designed for ethernet in ---> wifi AP out.  I need wifi in ---> new ssid/private network out

I think I'll try the desktop version and see if the GUI can make it happen.  That would be a dream come true.

-Emma

---

### Post by Iowan on 2014-01-27
I was still confused as to why a router wouldn't work, until I finally realized that your apartment is providing a wireless signal - not a wired connection.

---

