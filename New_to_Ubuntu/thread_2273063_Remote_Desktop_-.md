---
title: "Remote Desktop -"
date: 2015-04-10
forum: New to Ubuntu
---

### Post by Ravi_Shankar on 2015-04-10
I have so far been using chrome remote desktop.. and it's not fast enough. So now I'm trying to get VNC and Remmina to do the job. After reading around a bunch of random pages on the internet, I managed to install Remmina on the client-side system (Ubuntu 14.04) and vnc4server on the remote desktop (also Ubuntu 14.04). Now I'm super confused as to what details to give in at the login. Remmina has these question:
1. Protocol: (I guess "VNC - Virtual Network Computing" is what I should select and NOT "VNC - Incoming connections")
2. Server (under 'Basic' tab): IP address and port. Well, at the remote end, my system which is connected to a wifi has only a local ip address - client side can't possibly use that to connect. If I give external ip address, how will Rummina know which remote local computer (of all the computers connected to the wifi) I'm talking about. And port?!

---

### Post by steeldriver on 2015-04-10
Hello and welcome to the forums

You will need to forward the appropriate port(s) across your router - you should refer to your router's documentation for exactly how to do that. The default VNC port is 5900 + the display number on which you started the vncserver.

**However before you do that you should note that VNC is insecure**: you should set up SSH and tunnel the VNC connection  over that in any situation where you want to run VNC over a public  network. Or use something like x2go that has built-in SSH tunneling.

---

