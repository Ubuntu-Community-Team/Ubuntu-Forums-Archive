---
title: "Can't connect to NX linux server from Windows"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by GXice on 2008-10-11
When trying to connect with NX Client For Windows to my Hardy box which has NX Client, Node and Server installed, I get this Connection Refused message in Windows:

```
NX> 203 NXSSH running with pid: 5764
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
ssh: connect to host 127.0.1.1 port 22: Connection refused
```

So I'm being refused connection with ssh, any idea why? It's not my Vista firewall, I've tried to turn it off and get the same result. OpenSSH-server is properly installed on the linux box. I've also forwarded port 22 in my router.

By the way, I have no knowledge of CLI so please don't ask me to use Putty, I would like to operate my headless box with a GUI. :(

Please help! :(

---

### Post by superprash2003 on 2008-10-11
ensure that the port is open using some online port scanner.. some isp's block port 22

---

