---
title: "Using Ubuntu VNC app to Windows 7 VNC Server"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by clovisdecruz on 2013-02-20
Has anyone been able to successfully connect to a Windows 7 Home Edition VNC server via an Ubuntu VNC client application? Been trying for hours disabled all firewalls, tried various apps but still not able to.

However, I think I am not able to traceroute/ping from the windows machine to the ubuntu machine and vice versa... Any ideas on what could be causing this?

---

### Post by albandy on 2013-02-20
You need to know if you can see the port 5900 of your windows machine from your Ubuntu machine.
So open a terminal and type:

telnet windows_ip 5900

You should see something like the image attached.

---

