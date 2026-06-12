---
title: "MS Shares via Ubuntu VPN Tunnel - HELP!"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by CrouxL on 2012-10-30
This is my 2nd attempt, I hope to explain it better this time around. 
I have an Ubuntu Command Line Server, 12.04. It started out to be just a file server, with backup. 2 Weeks later I was informed that I need to setup a connection to Head Office, a Microsoft Exchange Server, to access shares. 
[ATTACH]226381[/ATTACH]
From the local site, Windows workstations(WS) need to connect to the shares on the MS Server. (Outlook on the WS's also connects to the MS Exchange Server via internet). 
With Windows, a VPN connection to MS Server is no problem, but then each WS needs to be connected. 

I have setup my Ubuntu server, as a PPTP VPN client, to connect to the MS Server, and then give access to the MS Server shares for each WS. The PPTP VPN tunnel is up and running. (In theory then, just one VPN connection). I can ping both the MS Server IP and name from the Ubuntu Server.

I have created samba shares and cifs mounts on my Ubuntu Server, via the VPN tunnel. From any WS, I can then access the samba shares, but I only have access to the files in the root of the share, all the subfolders are displayed as files with 0 size.

Accoring to my limitted knowleadge, my routing works, but I might have to change the way it works (not sure what to do?). 
Even with the mounting and samba shares disabled, I cannot ping the MS Sever IP, 10.0.0.2 from a WS. I have even added to the Host file, on one of the WS pc's, 10.0.0.2 MSServerName. But that did not help either.

I have searched the internet and followed guidelines as well. [http://pptpclient.sourceforge.net/routing.phtml](http://pptpclient.sourceforge.net/routing.phtml)

Am I setting it up the wrong way, or is there a chance that I might have to reconfigure my whole network layout?


Regards

---

