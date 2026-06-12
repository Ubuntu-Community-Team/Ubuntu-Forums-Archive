---
title: "serial console enablement- upstart to systemd"
date: 2019-04-01
forum: New to Ubuntu
---

### Post by boletosumya on 2019-04-01
Hi, 
I am new to ubuntu & systemd capabilities. 
I am trying to set the systemd service for bring up of serial tty console on 18.04 version of ubuntu. 

Earlier I had following init script that used to work well with upstart on 14.04 version. 

/etc/init/ttyS0: 
--------------------------------------------
# ttyS0 - getty
# 
# This service maintains a Getty on ttyS0

start on stopped rc RUNLEVEL=[2345] and (
         not-container or
         container CONTAINER=lxc or 
         container CONTAINER=lxc-libvert)

stop on run level [!2345]

respawn
exec /sbin/getty -L 9600 ttyS0 vt102
--------------------------------------------

To convert above upstart script into systemd function, I tried modifying ExecStart line in serial-getty@service. However the console is getting hung for the ubuntu VM after I restart it.

Can you please guide me to get above upstart script converted in right manner in systemd function? 

Thank you in advance,
Sumant

---

