---
title: "Serial port to TCP redirect"
date: 2009-03-02
forum: Programming Talk
---

### Post by nunojpg on 2009-03-02
I have a app that is designed to talk via serial port with a device.
The new device can be connected directly to the network but the software is not capable.
Modding the app is not trivial so I would prefer to do a little program that would redirect the TCP socket comm to a virtual serial port where the app would connect.

Is there anything already available for this?

Nuno

---

### Post by dwhitney67 on 2009-03-02
For the last few weeks I have been working on porting VS C++ apps to support UDP, in lieu of being strictly serial-port dependent.

After my modifications were made (which btw were somewhat extensive, but not daunting), I still needed to re-test the application's serial interface.  So I relied on the "COM/IP Redirector" from Tactical Software.  It handles two-way comm between serial port(s) and TCP port(s).  It was easy to install and configure.

If you are on a *nix-only platform, then I do not know if there is an equivalent app.  I'm sure there is.

---

### Post by supirman on 2009-03-02
I've not tried it, but see [http://linux.die.net/man/8/ser2net](http://linux.die.net/man/8/ser2net)

---

### Post by supirman on 2009-03-02
Also perhaps [http://freshmeat.net/projects/socat/](http://freshmeat.net/projects/socat/)

---

