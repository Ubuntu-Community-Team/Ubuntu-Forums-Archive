---
title: "How can I change mono web runing port from 8080 ?"
date: 2009-05-17
forum: Programming Talk
---

### Post by hoboy on 2009-05-17
I have made a mono-web but when I run it I get the following errors.

xsp2
Adding applications '/:.'...
Registering application:
    Host:          any
    Port:          any
    Virtual path:  /
    Physical path: /home/luc/Mono/webTest1/webTest1
Listening on address: 127.0.0.1
Root directory: /home/test/Mono/webTest1/webTest1
Error: Address already in use

The application was terminated by a signal: SIGHUP

Then I found this link
[http://www.debianadmin.com/running-aspnet-applications-in-debian-and-ubuntu-using-xsp-and-mono.html](http://www.debianadmin.com/running-aspnet-applications-in-debian-and-ubuntu-using-xsp-and-mono.html)

I have checked oracle db is running on 8080 on my machine.
How can I configure mono to run on different port ?

---

### Post by directhex on 2009-05-17
--port PORT
    Changes the default port where the XSP server will listen to requests. By default XSP listens on port 8080 and mod-mono-server has no default. AppSettings key name: MonoServerPort

---

### Post by hoboy on 2009-05-17
> **directhex said:**
> --port PORT
    Changes the default port where the XSP server will listen to requests. By default XSP listens on port 8080 and mod-mono-server has no default. AppSettings key name: MonoServerPort

please give me path to the port.

---

### Post by directhex on 2009-05-17
> **hoboy said:**
> please give me path to the port.

erm... wut?

It's a flag, taken from the xsp manpage. i.e. run "xsp --port 8181" instead of "xsp"

The global configuration is defined in /etc/default/mono-xsp{2} if you're using the /etc/init.d daemon script.

---

