---
title: "trouble setting up vnc"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by egil_g on 2008-05-17
I have two computers in a wireless network. a laptop running xp and   desktop running ubuntu 8.04. im trying to control the desktop from the xp-laptop.

-i run vncserver from the terminal-window and it says: starting applications as specified in .vnc/xstartup
-when i run realvnc from the laptop it says: connection refused.

i know there is a matter of ports, but how do I find out/configure the ports the ubuntu-machine is listening on?

the ip-address i found from using traceroute under network tools(the first address). 

thanks in advance,
jan egil

---

### Post by Monicker on 2008-05-17
The default port for vnc is 5900. How did you specify the connection from xp?  You should be able to just enter the ip address.  Verify which port your vnc session is listening on.

```
sudo netstat -anltp|grep vnc
```

Also, make sure you are not running any 3rd party firewalls on xp which might be blocking an outbound vnc connection.

---

### Post by egil_g on 2008-05-17
thank you for  respons.

When i used the netstat it produced this:

[PHP]

tcp        0      0 0.0.0.0:5901            0.0.0.0:*               LISTEN      6893/Xvnc      

tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN      6893/Xvnc      

tcp6       0      0 :::6001                 :::*                    LISTEN      6893/Xvnc      
[/PHP]

so I assume its listening on port 5901? could that be the problem. And the ip-address is the only thing im specifying when I run vnc-viewer from xp, yes.

I dont think im running a third party firewall. im not quite sure what that is. i do have avg free virus could that be the problem?

---

### Post by Monicker on 2008-05-17
Yes, it is listening on port 5901 and 6001.  To connect to the session on port 5901, you would specify "<ip address>:1".

```
192.168.1.100:1
```

for example.

---

### Post by egil_g on 2008-05-17
yes, now it works. sort of. i can log on to the remote machine, but all i see is a terminal window. But im sure i can figure it out from here on.

---

