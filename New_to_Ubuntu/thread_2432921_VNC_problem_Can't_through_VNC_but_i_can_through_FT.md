---
title: "VNC problem: Can't through VNC but i can through FTP and SSH"
date: 2019-12-11
forum: New to Ubuntu
---

### Post by sleep1 on 2019-12-11
As the title says. I'm not able to connect through VNC but i can connect through FTP and SSH. 

The FTP uses port :22 to connect and through the SSH i don't need to specify the port when i connect. 

I have enabled Ubuntus screen share function

Using the command: netstat -ntlp
tcp        0      0 127.0.0.1:5900          0.0.0.0:*               LISTEN      1760/vino-server  
tcp6       0      0 ::1:5900                :::*                    LISTEN      1760/vino-server 

I really don't know what information to relay to you guys so you can help me.

---

### Post by TheFu on 2019-12-12
On the same subnet, I'd just use X11 forwarding that ssh supports. Any GUI program should work this way, but here's a way to get a remote terminal, then you can run any GUI inside that terminal and have it display on your local X11 workstation:
```
$ uxterm  -sb -geometry 80x25+760+355   -e ssh -X romulus &
```
If you want to just directly run an application, say libreoffice, use:
```
$ ssh -X romulus /usr/bin/libreoffice  &
```

romulus is the name of the remote system. If ssh-keys have been setup and already unlocked recently, then the window with the program will be displayed in a few seconds.  It works fine over any 100 base-tx network or faster.  Some high speed internet connections work well too and with ssh, you don't need to worry about encrypted connections too much. This assumes you don't use passwords alone for authentication.

Plain FTP doesn't only use port 20, BTW.  sftp will use port 22, if that is what you mean. Please be accurate in saying which is being used.

VNC and RDP are known to have terrible security. If you absolutely must use either of these outside a trusted LAN, please use an ssh-tunnel for that traffic.
```
$ ssh -L 5901:localhost:5901 REMOTE_IP
``` 

Tell VNC to connect to localhost:5901 and that connection will tunnel through ssh and connect to 5901 where VNC typically runs. No firewall ports beyond ssh need to be open.

If you want an easier, faster, solutions, check out x2go. It feels 2-3x faster than VNC or RDP on Linux. x2go uses the NX protocol that uses ssh so only the ssh port needs to be open for x2go remote desktops.

But when on the same LAN, I just use that stuff at the top with **ssh -X**. Fast, easy, no mess.

---

