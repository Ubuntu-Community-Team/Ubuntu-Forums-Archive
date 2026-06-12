---
title: "dnsmasq: failed to create listening socket for port 53: Address already in use"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by Ram2012 on 2012-09-21
Hi experts.....
i was trying to setup DNS/DCHP server from the link- 
 [https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)

i got n error sayin...
 dnsmasq: failed to create listening socket for port 53: Address already in use 
how to fix this..?

this is what i tried....
root@user-desktop:/etc/init.d# sudo apt-get install dnsmasq
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dnsmasq
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/15.4 kB of archives.
After this operation, 120 kB of additional disk space will be used.
Selecting previously unselected package dnsmasq.
(Reading database ... 146283 files and directories currently installed.)
Unpacking dnsmasq (from .../dnsmasq_2.59-4_all.deb) ...
Processing triggers for ureadahead ...
Setting up dnsmasq (2.59-4) ...
 * Starting DNS forwarder and DHCP server dnsmasq                                                                                                                                                            
dnsmasq: failed to create listening socket for port 53: Address already in use
                                                                                                                                                                                                      [fail]
invoke-rc.d: initscript dnsmasq, action "start" failed.



how to solve this.....

---

### Post by termvrl on 2012-09-21
hi 
maybe u can use netstat to list out the open port on your machine. =D

---

### Post by Ram2012 on 2012-09-21
even after i uninstall dnsmasq using 
 sudo apt-get remove dnsmasq


it is being displayed in the netstat...

tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      5960/rpcbind    
tcp        0      0 0.0.0.0:56658           0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      **963/dnsmasq **    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      815/cupsd       
tcp        0      0 0.0.0.0:40381           0.0.0.0:*               LISTEN      6495/rpc.mountd 
tcp        0      0 0.0.0.0:35167           0.0.0.0:*               LISTEN      6495/rpc.mountd 
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:48165           0.0.0.0:*               LISTEN      6194/rpc.statd  
tcp        0      0 0.0.0.0:41160           0.0.0.0:*               LISTEN      6495/rpc.mountd 
tcp6       0      0 :::36526                :::*                    LISTEN      -               
tcp6       0      0 :::111                  :::*                    LISTEN      5960/rpcbind    
tcp6       0      0 :::38224                :::*                    LISTEN      6194/rpc.statd  
tcp6       0      0 ::1:631                 :::*                    LISTEN      815/cupsd       
tcp6       0      0 :::50107                :::*                    LISTEN      6495/rpc.mountd 
tcp6       0      0 :::57500                :::*                    LISTEN      6495/rpc.mountd 
tcp6       0      0 :::44127                :::*                    LISTEN      6495/rpc.mountd 
tcp6       0      0 :::2049                 :::*                    LISTEN      -

---

### Post by Ram2012 on 2012-09-21
luks like Network Manager is running dnsmasq, even though  dnsmasq is n0t installed on port 53...........

---

