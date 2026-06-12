---
title: "Setting up SFTP on Ubuntu Desktop"
date: 2015-02-08
forum: New to Ubuntu
---

### Post by Joe_Durham on 2015-02-08
I have recently installed Ubuntu 14.04 Desktop. I am pretty new to both Linux and Ubuntu a while back I purchased a domain name as well. 

I would like to combine these two facts and try to setup an SFTP which is accessible over the internet and uses my domain name to access. I would really appreciate some help with being able to acheive this. I believe I will also need to get to grips with DynDNS as my external IP (which I assume I will need to use to access the SFTP server externally) is changed on a semi-regular basis by my ISP. 

Thanks for reading please feel free to make suggestions, as previously stated I'm new to this. 

Thanks,
Joe

---

### Post by Lars Noodén on 2015-02-08
First set up the package openssh-server and be sure you can log in with SFTP over the LAN.  

Then set up the router's port forwarding to forward an external port to port 22 of your SFTP server.  You can pick a very high numbered port or stick with 22.  You'll probably also want to set the router so that your SFTP machine always gets the same address on the LAN.  

Test that you can connect to you external IP number on the designated port.  Depending on the model of router, you might have to test this from outside your LAN.  

When those steps are working, then get an account with a dynamic DNS service and use your router's built-in dynamic DNS support to track the name.  There are others besides DynDNS.

---

### Post by Joe_Durham on 2015-02-08
Okay I have got this working. I changed the A-record for domain to point to my current External IP. This is fine for now but when external IP changes I will have an issue. Any tips on how to setup dynamic DNS and also the cheapest way of doing it?

Thanks.

---

### Post by Lars Noodén on 2015-02-08
The way it usually works is that you sign up for a service like no-ip.com or one of the other [servies](https://help.ubuntu.com/community/DynamicDNS).  Then you run a program on your server or router that automatically, periodically checks in with the service and updates their DNS record.  On your server that would be ddclient.  On your router, that would be whatever the firmware has preinstalled.  That way, the DNS record gets updated.

*If* I recall correctly that takes care of the A record for your IP and then you can point a permanent CNAME at that short-lived A record.  However, it's been a while since I've use that.

---

### Post by Lars Noodén on 2015-02-08
The way it usually works is that you sign up for a service like no-ip.com or one of the other [servies](https://help.ubuntu.com/community/DynamicDNS).  Then you run a program on your server or router that automatically, periodically checks in with the service and updates their DNS record.  On your server that would be ddclient.  On your router, that would be whatever the firmware has preinstalled.  That way, the DNS record gets updated.

*If* I recall correctly that takes care of the A record for your IP and then you can point a permanent CNAME at that short-lived A record.  However, it's been a while since I've use that.

---

### Post by Joe_Durham on 2015-02-08
I bought the domain from godaddy, would this work with no-ip?

---

### Post by Lars Noodén on 2015-02-08
Yes.  Point the dynamic DNS domain at your router using ddclient or the router's built-in capabilities.  Then use GoDaddy's DNS to point a CNAME at the dynamic DNS name, if I understand correctly.

---

### Post by Joe_Durham on 2015-02-08
Thanks I configured the router to work with dlinkddns and all is tested and working. Many thanks again.

---

### Post by sandyd on 2015-02-08
Hi, if you have found a solution to your problem, please mark this thread as solved using Thread Tools -> Mark Thread as Solved.

Thanks!

---

