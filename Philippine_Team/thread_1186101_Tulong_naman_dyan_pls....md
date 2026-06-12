---
title: "Tulong naman dyan pls..."
date: 2009-06-13
forum: Philippine Team
---

### Post by edibanez on 2009-06-13
Mga bossing patulong po cross post ko na lang po ito...

[http://ubuntuforums.org/showthread.php?t=1166963]("http://ubuntuforums.org/showthread.php?t=1166963")

---

### Post by Script Warlock on 2009-06-13
sudo ufw <port number>
or
sudo ufw allow from 10.0.0.0/24 to any port 22

sudo ufw status...

check the port with canyouseeme.org

---

### Post by badrra on 2009-06-13
Naka connect ka na ba sa using SSH without the firewall? 

I assume initialized yung SSH server mo kasi "cannot connect to localhost" ang otherwise ang error msg will be "connection is refused".

I just tried it now and i am not getting any problems connecting to SSH server. Possible problem would be the settings of you SSH server. Kasi from the looks of it, the firewall allowed incoming connection to port 22. Pag dating sa SSH server parang authentication issue. 

I had the same problem before without iptables turned on. Ginawa ko uninstall and reinstall ko ung OpenSSH. Left all settings to default. Yun gumana. Now, I did the same thing you did and am still able to connect to my server thru SSH.

Edit: I noticed this sa iptables -L output mo

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh

this is mine: 

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
[COLOR="Sienna"]ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh[/COLOR] 

I am not sure if the one in red makes a difference.

---

### Post by edibanez on 2009-06-13
ayaw pa rin sir eh..
eto reply ng canyouseeme.org 
   [I]Error: I could not see your service on 203.177.91.194 on port (22)
Reason: Connection timed out[/I]

eto po output ng sudo ufw status verbose:
```

Status: active
Logging: on (low)
Default: deny
New profiles: allow

To                         Action  From
--                         ------  ----
22                         ALLOW   10.0.0.0/24


```

---

### Post by badrra on 2009-06-13
> **edibanez said:**
> ayaw pa rin sir eh..
eto reply ng canyouseeme.org 
   [I]Error: I could not see your service on 203.177.91.194 on port (22)
Reason: Connection timed out[/I]

eto po output ng sudo ufw status verbose:
```

Status: active
Logging: on (low)
Default: deny
New profiles: allow

To                         Action  From
--                         ------  ----
22                         ALLOW   10.0.0.0/24


```

Baka di naka Port forward sa router mo ung PORT 22

---

### Post by edibanez on 2009-06-13
ok na po sir thanks sa tulong, I just removed and reinstalled openssh from launchpad repo and it worked di kasi gumana dati when i only used the standard repos eh.. thanks ulit ng marami...

---

### Post by badrra on 2009-06-13
There you go. Thats great. ;)

---

