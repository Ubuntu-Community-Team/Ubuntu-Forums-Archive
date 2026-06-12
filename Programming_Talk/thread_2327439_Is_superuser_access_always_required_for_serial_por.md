---
title: "Is superuser access always required for serial port communications?"
date: 2016-06-10
forum: Programming Talk
---

### Post by john_ladasky on 2016-06-10
Hi there,

It has been a long time since I've posted here.  Did you miss me? :D

I am developing an application for my Ubuntu desktop PC, which communicates with a peripheral connected to a USB port.  I'm using Ubuntu 15.04, Python 3.4 with PySerial, and PyQt5.4 for the GUI.

In order to execute my application, I have to invoke python3 with sudo.  Otherwise, my access to the serial ports is denied by the OS.  This has nothing to do with Python.  If I want to use gtkterm, I must also use sudo.

I don't mind running as root. Unfortunately, running as root is also messing up certain visual aspects of my PyQt5 interface.  The styles of objects and fonts rendered by PyQt5 differ.  Worse, some GUI objects don't render at all!  I don't know why this happens, but debugging it does not sound appealing.  Also: any files that my program saves are owned by root, and I have to change ownership before I can edit them.

Alternately, I would like to allow unrestricted access to my serial ports.  How can that be accomplished?

There is probably some important security reason that Ubuntu locks regular users out of the serial interface.  If you know the reason, please enlighten me.

Ultimately, I will hand my finished application over to a Windows user.  It's Python, it's supposed to be portable.  I don't know Windows' policy regarding serial ports, but if access is lenient, all this fuss may not matter in the end.

Thanks for your help!

---

### Post by steeldriver on 2016-06-10
Have you tried adding your user to the dialout group?

---

### Post by john_ladasky on 2016-06-10
> **steeldriver said:**
> Have you tried adding your user to the dialout group?

That worked, thank you! I can run gtkterm and my application now, both without sudo, and they can both see the serial ports!

In case anyone needs directions:

```
sudo adduser <user name> dialout
```

Then reboot.

---

