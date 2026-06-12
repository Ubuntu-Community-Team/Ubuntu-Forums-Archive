---
title: "issues with apt-get install isc-dhcp-server &amp; sudo apt-get install update commands on"
date: 2013-09-20
forum: New to Ubuntu
---

### Post by ewPxkfp on 2013-09-20
i'm a newbie in the Ubuntu server environment. Installed Ubuntu 12 on our dell poweredge server at work. 
After successful installing ubuntu, went ahead to run command - sudo apt-get install isc-dhcp-server at command line 
to enable dhcp service. However each time i execute the command i keep getting the error message "unable to locate package isp-dhcp server ubuntu". 

Also the update command "sudo apt-get install update" (to install newest versions of packages) also comes up with error message "400 bad response from server" each time i run this command at command line.


Please can someone explain to me what i'm doing wrong and how to resolve these issues.



thanks
Tolu

---

### Post by TheFu on 2013-09-20
Your are close on the commands, but not quite right.
This should help get you started [http://www.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://www.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)
There is much more to running an internet facing server.

Sorry, I can't help with the DHCP server question. I let the router manage DHCP leases and static leases.

---

