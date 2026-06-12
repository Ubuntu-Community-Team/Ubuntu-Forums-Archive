---
title: "ubuntu server 11.10 DHCP server 2 nic's clients cant surf"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by crashdogy on 2012-03-17
Ok if I do ipconfig /all on the client's pc I get  my IP and it shows the DNS   but if try to surf no go ?

---

### Post by Gone fishing on 2012-03-17
I'm assuming the server is between the internet and the clients if so it's not supprising - unless the server allows port forwarding etc. To connect to the internet you will need to allow port forwarding or use a proxy server.

[https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3](https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3)

---

### Post by crashdogy on 2012-03-17
Ya that the tutorial I followed . also to start the dhcp3 server I have to type service isc-dhcp-server start or it will not run ?

---

### Post by Gone fishing on 2012-03-18
If you followed that tutorial it should be 

/etc/init.d/dhcp3-server start

and you can check the status with

/etc/init.d/dhcp3-server status

But are your clients getting address? If they are then the DHCP server is working the problem I would have thought is with the firewall rules and IP tables.

Let me plug Webmin which you may find makes it easier to set up the the system has Web based tools which makes it easy to switch services on and off set up the firewall etc. 

[http://www.webmin.com/](http://www.webmin.com/)

Edit if the service isn't starting on boot 

sudo update-rc.d dhcp3-server defaults

but have a look at Webmin.

---

### Post by crashdogy on 2012-03-18
this is what i have

---

### Post by Gone fishing on 2012-03-18
Have you enabled NAT?

> Enable NAT

Add a firewall rule to enable packet forwarding
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
(the forwarding)
This configuration will be lost on a reboot so we need to save it.
iptables-save > /etc/iptables.rules

From the Howto

Sorry Things have changed and service isc-dhcp-server start is right

[http://ubuntuforums.org/showthread.php?t=1765844&page=2](http://ubuntuforums.org/showthread.php?t=1765844&page=2)

---

### Post by crashdogy on 2012-03-18
yes i did that command you can see it in my post

---

### Post by Gone fishing on 2012-03-18
Sorry what happens if you try and ping an external IP address from the clients? As it seems the clients are getting IP addresses and you have enabled port forwarding and NAT, I'm wondering about a DNS problem.

---

### Post by crashdogy on 2012-03-18
Cant ping any thing on eth0.    69.138.104.182. Or [www.yahoo.com](www.yahoo.com)

---

### Post by crashdogy on 2012-03-18
I got man,  it was the DNS this what I did to fix it 

I add this to my /etc/network/interface   network 192.168.10.0 Then added 
the DNS IP addresses in my /etc/resolv.conf file to my /etc/dhcp/dhcpd.conf  and put them where it said option domain-name-servers  0.0.0.0,  0.0.0.0  and now iam surfing

Thanks for all your help.

---

### Post by Gone fishing on 2012-03-18
Well Done!

Please mark as solved

---

