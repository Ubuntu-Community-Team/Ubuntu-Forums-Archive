---
title: "PPTP VPN server not accesible"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by luisjone on 2012-11-19
Hello hello,


      I recently setup an Ubuntu home server running Ubuntu server 12.04 LTS x64. On it I made 2 virtual machines with Virtual box, one MEDIA server and another one as LAMP server (both running Ubuntu server 12.04 LTS x64 as well). Both with Bridge adapter on eth0 as Network adapter 1.


      On the LAMP server I installed the apache web server with a ddclient to track my IP pointing to my domain and an ftp server with VSFTPD. I also tried to install a PPTP server  as I just wanted something quick…well it turn out not quick at all.


      For some reason when I tried to connect to it (windows laptop, iPhone, android, etc.) from inside the LAN it won’t work (Obviously doenst work outside either). The error I’m getting when trying to connect:


> 

“The network connection between your computer and the VPN server could not be established because the remote server is not responding.” 



  The modem is set up to allow the 1723 port connection forwarded to my server (it has a pre-configuration itself for PPTP that I assume opens the GRE protocol too). However since is inside the LAN that shouldn’t be a problem (I also tried DMZ just to make sure).


  So the addresses at the bottom of /etc/pptd.conf are:


> localip 192.168.2.23
  remoteip 192.168.2.5,192.168.2.6
[B][FONT=&quot]
[/FONT][/B]
  And I made sure that both of the remotes fall out of the pool of DHCP addresses that starts at “192.168.2.7”


   In the /etc/ppp/pptpd-options:


> ##refuse-pap
  ##refuse-chap
  ##refuse-mschap


  ms-dns 8.8.8.8
  ms-dns 8.8.4.4
[FONT=&quot]
[/FONT]
  Then specified the account in /etc/ppp/chap-secrets:


> # client            server         secret                   IP addresses
  PeterParker      pptpd          ImSpiderMan        192.168.2.5
[FONT=&quot]
[/FONT]
  Then setup a ip-masquerading on /etc/rc.local (before exit 0 and making sure is eth0 interface ):


> # PPTP Forwarding
  iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
[FONT=&quot]
[/FONT]
  Uncommented “[FONT=Calibri]net.ipv4.ip_forward=1” in[/FONT]    /etc/sysctl.conf


  Edited "/etc/default/ufw" and changed the option "DEFAULT_FORWARD_POLICY" from "DROP" to "ACCEPT"


  And last in /etc/ufw/before.rules” added just before "*filter":


> ## NAT table rules
  *nat
  :POSTROUTING ACCEPT [0:0]


  ## Allow forward traffic to eth0
  -A POSTROUTING -s 10.99.99.0/24 -o eth0 -j MASQUERADE


  ## Process the NAT table rules
  COMMIT
[FONT=&quot]
[/FONT]
  Then of course several reboots, ”sudo sysctl –p", "[FONT=Calibri]sudo /etc/init.d/pptpd restart”, [/FONT]and[FONT=Calibri] “sudo /etc/init.d/networking restart”. [/FONT]
  
  When I run[FONT=Calibri] “sudo netstat –atnp” [/FONT]it seems to be listening:
  


> Active Internet connections (servers and established):
[FONT=Calibri]Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name[/FONT]
  [FONT=Calibri]tcp        0      0 0.0.0.0:1723            0.0.0.0:*               LISTEN      1136/pptpd 
[/FONT]

  So I think it must be something related with iptables or ufw, but I’m clueless. I went over and over, it doesn’t look so complicated and I got it working in the past in no more than 30min…This time I already spent a few days searching and trying everything I could find…So I would greatly appreciate any suggestion any of you might have.


  Thanks in advance.

---

