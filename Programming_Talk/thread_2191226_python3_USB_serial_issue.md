---
title: "python3 USB serial issue"
date: 2013-12-01
forum: Programming Talk
---

### Post by schmidtbag on 2013-12-01
I am working on a program meant to be cross-platform in both a hardware and software perspective, which makes python an easy choice.  This software utilizes serial ports, so I have something that involves serial.tools list_ports.  Anyway, I have a x86-64 Arch setup that runs python 3.3.3 and the following command:
```
available=[port[0] for port in list_ports.comports()]
```
works great - it lists all serial devices.  However, I have an Ubuntu Saucy setup on an armhf platform.  Running the same command will work, as long as I don't have any USB serial devices plugged in.  Otherwise, I get the error "can't use a string pattern on a bytes-like object".

I tried google searching the problem but the only solutions available didn't explain exactly what I need to do.  I get the impression I have to modify the pyserial library itself, but I can't do that if I expect other people to use this.  Besides, I'm using the same pyserial library as I am on my Arch setup.


So really, the only major difference is the architecture (which I don't think is the issue because aside from that 1 line of code, the rest of the application works fine), the distro, and the python version.  Ubuntu uses python 3.3.2.

Debian jessie uses a slightly newer version of python 3 but I'm not sure if that'll help, and I'd rather not have people depend on another distro's package.  Any suggestions?

---

