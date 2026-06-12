---
title: "running makedev at startup..."
date: 2009-01-09
forum: Programming Talk
---

### Post by hardyn on 2009-01-09
I have been playing with a sensoray IO board, which comes with its own kernel driver.  after a small fight compiles, installs etc... seems to work.

as a part of the makefile is an install script with runs a MAKEDEV command, which installs the device.  thing is, its definition in the /dev directory is gone after a restart; the kernel module is still present.

the definitions in /dev can be reinstated by re-runing 'make install' but this is a little silly... how might i keep the device definition in /dev, or at least run the MAKEDEV script at boot?

Thanks

makefile can be found here:
[http://www.sensoray.com/downloads/sdk626.zip](http://www.sensoray.com/downloads/sdk626.zip)

---

### Post by krzysz00 on 2009-01-11
add the makedev command to /etc/rc.local BEFORE the "exit 0" line and chmod a+x /etc/rc.local now the command will be run at the end of the boot process

---

