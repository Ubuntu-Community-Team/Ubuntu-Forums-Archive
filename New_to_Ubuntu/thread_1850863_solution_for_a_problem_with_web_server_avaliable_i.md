---
title: "solution for a problem with web server avaliable in LAN network..."
date: 2011-09-27
forum: New to Ubuntu
---

### Post by jpjohnj on 2011-09-27
hi.

below image show the network setup..

i have some problem in port forwarding option...

(i.e) i can forward the port 80 with below setup.

consider here adsl wireless router has some firewall setting ... i set the port forwarding option for that web server ..it work fine

image1: 


for below setup it wont work...
here i am applying port forwarding only in wireless router.
and i am not getting acces to the web server..


image2:



i need to know....

consider in image 2..

1.  when pc1 send a request for accessing webserver , how the request process upto the web server..


2. what do i need to do to get a access with the setup shown in image 2.

---

### Post by LinuxRocks713 on 2011-09-30
> **jpjohnj said:**
> hi.

below image show the network setup..

i have some problem in port forwarding option...

(i.e) i can forward the port 80 with below setup.

consider here adsl wireless router has some firewall setting ... i set the port forwarding option for that web server ..it work fine

image1: 


for below setup it wont work...
here i am applying port forwarding only in wireless router.
and i am not getting acces to the web server..


image2:



i need to know....

consider in image 2..

1.  when pc1 send a request for accessing webserver , how the request process upto the web server..


2. what do i need to do to get a access with the setup shown in image 2.

In Image 2:

With the second diagram's "Wireless Router", add a port 80 forwarding to the IP address of your web server. Now on the "ADSL wireless router" add a port forward/DMZ to port 80 of the "Wireless Router". Now when you receive a request from Internet, it will forward through the gateways and end up at your server.

---

