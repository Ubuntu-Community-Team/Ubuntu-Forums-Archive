---
title: "Reboot/Shutdown stopped working after latest update"
date: 2021-12-11
forum: New to Ubuntu
---

### Post by philly1ms on 2021-12-11
So it seems after every update I cannot restart or shutdown Ubunutu from the menu.  I also tried restarting or shutting down from terminal using shutdown -h, shutdown -H, shutdown -r.  Nothing happens.  It does come back after a few hard power offs but I know eventually the system will get corrupt doing this and I won't get back in at all.  Any suggestions?  Drivers maybe?  This last time my NIC driver didn't load until I did a hard shutdown.  Thank you

Ubunutu 20.04.3 LTS

---

### Post by ajgreeny on 2021-12-11
See what happens if you use Ctrl+Alt+F1 to get to a tty command line and from there use ```
sudo shutdown -h now
```
It's a long time since I used a command to shutdown and I can not remember if it really needs to run as root or not, but I think that may be your problem if you were doing so without the **sudo** prefix.

---

### Post by maketopsite on 2021-12-11
> **philly1ms said:**
> So it seems after every update I cannot restart or shutdown Ubunutu from the menu.  I also tried restarting or shutting down from terminal using shutdown -h, shutdown -H, shutdown -r.  Nothing happens.  It does come back after a few hard power offs but I know eventually the system will get corrupt doing this and I won't get back in at all.  Any suggestions?  Drivers maybe?  This last time my NIC driver didn't load until I did a hard shutdown.  Thank you

Ubunutu 20.04.3 LTS

Did you try 
```
reboot
```
command ?

Did you check logs ?

Did you try Alt + sysrq + REISUB  ?

---

### Post by maketopsite on 2021-12-11
> **ajgreeny said:**
> See what happens if you use Ctrl+Alt+F1 to get to a tty command line and from there use ```
sudo shutdown -h now
```
It's a long time since I used a command to shutdown and I can not remember if it really needs to run as root or not, but I think that may be your problem if you were doing so without the **sudo** prefix.

root privileges are required and there is warning message in case of insufficient privileges.

---

