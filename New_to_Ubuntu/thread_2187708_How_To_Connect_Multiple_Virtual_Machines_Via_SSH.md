---
title: "How To Connect Multiple Virtual Machines Via SSH"
date: 2013-11-13
forum: New to Ubuntu
---

### Post by benynug on 2013-11-13
First of all, I am using Windows 7 as a host. Then I install Ubuntu 12.04 Guest under VirtualBox.
  Then I get an access to the other four virtual machines (also Ubuntu  12.04 Guest) via ssh by running the following command in my Ubuntu  Guest' terminal: 

```
ssh user@ipaddress
```


Then I want to connect those four virtual machines in an Internal  Network, is there any ways to connect them under my Ubuntu Guest?  I'm confused since I can only access those four virtual machines via ssh  on my Ubuntu's terminal.
  I appreciate any help.


  Thank you.

---

### Post by TheFu on 2013-11-13
If you use bridged networking for each, then any ssh client on the network should have access provided no firewalls get in the way.  When I say "on the network" I mean any other device ... other computer, tablet, wifi-connected cell phone ... nice.

I'm probably over thinking your question.  From windows, you can use putty or winscp to access ssh/scp/sftp on Ubuntu servers.

There are many, many other ways to connect to computers. There are 65,000 ports, so any one of them can run a service that allows connectivity.  samba/cifs, nfs, http, https, openvpn, ssh, scp , sftp, IMAP, POP, SMTP, SNMP, RDP, NX, VNC lots of ways. Each has a specific purpose.  For more of a list, look at /etc/services ... this is just a list and does not mean any specific service is available.

If you are more interested in running remote GUI apps, [this article]("http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications") might shed some light?

---

### Post by benynug on 2013-11-14
> **TheFu said:**
> If you use bridged networking for each, then any ssh client on the network should have access provided no firewalls get in the way.  When I say "on the network" I mean any other device ... other computer, tablet, wifi-connected cell phone ... nice.

I'm probably over thinking your question.  From windows, you can use putty or winscp to access ssh/scp/sftp on Ubuntu servers.

There are many, many other ways to connect to computers. There are 65,000 ports, so any one of them can run a service that allows connectivity.  samba/cifs, nfs, http, https, openvpn, ssh, scp , sftp, IMAP, POP, SMTP, SNMP, RDP, NX, VNC lots of ways. Each has a specific purpose.  For more of a list, look at /etc/services ... this is just a list and does not mean any specific service is available.

If you are more interested in running remote GUI apps, [this article]("http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications") might shed some light?

Thank you for your answer. I tried to ping all of them and they can send/receive packets. But what I mean by "connect" is to physically connect them using their  ethernet. For example, VM1 connect to VM2 by using eth1 on VM1 and eth2  on VM2. I can do this in virtualbox, just add network adapter "Internal Network"  for both of them. But as I said, I can only access those VMs via my Ubuntu's terminal, I  don't have any access on their virtualbox. 

I tried to run command ```
ifconfig
``` on all of them, but the ethernet that they have are only eth0 and lo.

---

### Post by jdeca57 on 2013-11-14
> **benynug said:**
> Thank you for your answer. I tried to ping all of them and they can send/receive packets. But what I mean by "connect" is to physically connect them using their  ethernet. For example, VM1 connect to VM2 by using eth1 on VM1 and eth2  on VM2. I can do this in virtualbox, just add network adapter "Internal Network"  for both of them. But as I said, I can only access those VMs via my Ubuntu's terminal, I  don't have any access on their virtualbox. 

I tried to run command ```
ifconfig
``` on all of them, but the ethernet that they have are only eth0 and lo.

From the view of a virtual machine it is a stand-alone system and they all can use their eth0 without conflict. A nice posting about virtualbox networking is here: [https://blogs.oracle.com/fatbloke/entry/networking_in_virtualbox1](https://blogs.oracle.com/fatbloke/entry/networking_in_virtualbox1) so in order to reach them from Windows or the external world you need bridged networking, else they connect only internally.

---

### Post by benynug on 2013-11-14
> **jdeca57 said:**
> From the view of a virtual machine it is a stand-alone system and they all can use their eth0 without conflict. A nice posting about virtualbox networking is here: [https://blogs.oracle.com/fatbloke/entry/networking_in_virtualbox1](https://blogs.oracle.com/fatbloke/entry/networking_in_virtualbox1) so in order to reach them from Windows or the external world you need bridged networking, else they connect only internally.

Is there any way to configure the network using commands in the terminal? I don't have access on each VM's virtualbox. :(

---

### Post by TheFu on 2013-11-14
You need to change the VM settings for each VM. That can only be done from the hostOS.
It needs to be in bridge mode and there is no need for "internal networking" at all.

You can manage virtualbox using the CLI command ... sorry, I don't remember the exact name - something like vmmanage or vboxmanage .... on windows it is not case sensitive, however it is NOT in the PATH either.

Every clientOS will use eth0 internally. It is best to use the 1st adapter for each inside the VM settings.  Every VM in virtualbox can have 4 virtual-NICs, but when you are a beginner, it is best to use the 1st one only and avoid wifi connections on the hostOS.  The actual network hardware does not matter to the clientOSes at all.

For posts with VirtualBox, I always include a performance tuning link: [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) Hope it helps.

---

