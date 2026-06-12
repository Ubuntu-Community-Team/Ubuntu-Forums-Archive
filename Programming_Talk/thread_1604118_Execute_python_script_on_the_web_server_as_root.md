---
title: "Execute python script on the web server as root"
date: 2010-10-23
forum: Programming Talk
---

### Post by xszolik on 2010-10-23
Hy all,

  I work on project where client communicate with server, and the server communicate with usb device. 

  I have installed ubuntu 10.04, apache2, python 2.6.

  The communication is solved with python (I using pyusb library to usb communication). The problem is client cant start this project, because one of the python scripts on the server needs execute as root. 
  This problematic script is started like this: 

```
subprocess.Popen(["sudo","python", "getSend.py", str(input)], shell=False, stdin=PIPE ,stdout=PIPE,  stderr=STDOUT)
```

So getSend.py contains the command, which setup the USB device:

```
device.set_configuration()
```

This command doesnt works without sudo rights.
When I testing it locally in terminal everything works fine. 
So the main problem is run python script with root rights on the server.

Any idea?

Thanks,
xszolik

---

