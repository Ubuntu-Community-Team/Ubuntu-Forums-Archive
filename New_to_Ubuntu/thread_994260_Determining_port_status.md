---
title: "Determining port status"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Cysten on 2008-11-26
I need to determine which ports are open and which are closed from within the system. I'm sure there is a command to do this. Also I need to determine in particular if my ftp port is open or not. If it is closed how do I open it?

---

### Post by adult swim on 2008-11-26
from a terminal
start out with ```
sudo ufw enable
```
open ports with ```
sudo ufw allow xxxx
``` where xxxx is the port number
close open ports with ```
sudo ufw delete allow xxxx
```
check the firewall status with ```
sudo ufw status
```

---

### Post by Cysten on 2008-11-26
Cool. How do I get a listing of all the ports on my system and their status and associated protocol?

---

### Post by jemate18 on 2008-11-26
> **Cysten said:**
> Cool. How do I get a listing of all the ports on my system and their status and associated protocol?

you can check out services for the list of ports and their service name
```
sudo less /etc/services
```

for the list of open ports
```
netstat -ap
```

---

### Post by Strega on 2010-11-22
Hi,

Is there also a way to look at only 1 port? I want to make a script that checks the status of port 27015 and then uses an if statement to do some stuff.
Is this possible?

Regards,
Strega

---

### Post by alhaines on 2011-06-30
for a single port use grep

sudo netstat -ap |grep 6600

this returns:

tcp6       0      0 [::]:6600               [::]:*                  LISTEN      21711/mpd 

use awk if you want to parse the line

---

