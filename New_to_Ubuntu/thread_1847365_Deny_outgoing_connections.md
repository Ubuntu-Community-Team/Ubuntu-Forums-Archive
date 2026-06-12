---
title: "Deny outgoing connections"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by Johnny3 on 2011-09-20
I use this young man site to set up my firewall. 
[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
I get the first two right sudo ufw enable and sudo ufw default deny. But when it comes to Deny outgoing connections if I do that it will not let Thunderbird get on. Thunderbird uses popmail server port 995 and SMTP port 465. It looks like Mail = protocol tcp port 25 I need to change to ether 995 or 465. But which one. The only ports I want open is what Ubuntu 11.04 needs, Firefox, and Thunderbird.Maybe Chrome. Hope some could tell me what to do.
Deny outgoing connections

This is a bit harder as you need to know the services you wish to allow and write rules for outbound traffic you wish to allow. Common services you may wish to allow (and their ports) include:

Basic services:
DNS (Domain Name Service) = protocol udp port 53.
Web browsing = http protocol tcp port 80.
Secure web browsing = https protocol tcp port 443.
Mail = protocol tcp port 25.
FTP = protocol tcp port 20 and 21.
SSH = protocol tcp port 22.
VNC = protocol tcp port 5900.
Samba uses multiple ports , protocol udp ports 137 and 138 as well as tcp ports 139, and 445.
IRC protocol tcp , Ubuntu Servers defaults to 8001.

A listing of ports can be found here.(I don't known enough to use) 

UFW will block outbound traffic based on the destination port on the server. To allow the outbound traffic listed above use:

sudo ufw allow out 53,137,138/udp
sudo ufw allow out 20,21,22,25,80,139,443,5900,8001/tcp

Then block all other outbound traffic with:

sudo ufw deny out to any 

Thanks and God Bless Johnny3
65++ and still ticking.

---

### Post by Dangertux on 2011-09-20
You need to add both. 

Port 25 is the standard SMTP service port
Port 110 is the standard POP3 service port.

So if your mail client is using both you would add both port 465 and port 995.

I don't think that tutorial has a reference for port 110 so you're not really replacing anything. You could remove port 25 though if you're not using it. You can also remove 20,21,22,139,5900,445 if you're not using any of the following, FTP , VNC, SSH or Samba

---

### Post by Johnny3 on 2011-09-20
Thank you so much. Not much of a Ubuntu user. The firewall is about the only time I use the terminal. Install everything with package manager and software center. Used to install temperature program. But with X sensors don't have to use the terminal for that. I just use Ubuntu after that. And as long I don't mess it up works great.
Thanks and God Bless Johnny3

---

### Post by Dangertux on 2011-09-20
Glad it helped :-)

---

