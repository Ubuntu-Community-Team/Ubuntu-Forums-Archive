---
title: "Python - Daemon to launch X application"
date: 2008-12-24
forum: Programming Talk
---

### Post by msamson on 2008-12-24
Hi folks,

I'm trying to do the following:
User plug a Usb device, HAL launch a custom executable that will handle it.

hald is running as root, so it is possible to setuid() and setgid() to another user (the logged one.).

Right now, HAL does launch the executable successfully, what is left is to be able to launch an application from a console (hald is a daemon with no tty attached) as the user credentials and displayed in the X display. (Ex: f-spot photo manager).

I am using python 2.5/6 and cannot go with python 3000.

Normally when you want to launch an application from the console, you just have to set the DISPLAY environment variable.

i tried os.environ["DISPLAY"] = ":0" or any combination of displays to no avail.

What should i do?

short version:
HAL launch python code (launcher.py) as root with minimal env.
launcher.py must then change it's uid and gid to a user (let's simplify it right now, uid and gid 1000)
launch a X-based application (firefox, f-spot photo manager, etc.)

I am stuck at the last bit where the application complain it cannot find display :0 or display :0.0 or display 0 or display 0.0

---

### Post by Quikee on 2008-12-25
Why don't you just create a program that is started when the user session is started. The program must just register a callback via d-bus and sit there. Once the USB device is inserted HAL will then notify back that the event has happen and then just start your other program or whatever.

---

### Post by msamson on 2008-12-26
That might be a viable solution :)

I am developing for a somewhat limited platform in term of processing and memory.


But it might be the only solution as it seems ridiculously hard to make a daemon start a program for another user and have it displayed on that user X-session

---

### Post by msamson on 2008-12-26
Found the answer:

xhost +localhost or xhost + (warning, xhosts + will allow anyone from anywhere).

---

