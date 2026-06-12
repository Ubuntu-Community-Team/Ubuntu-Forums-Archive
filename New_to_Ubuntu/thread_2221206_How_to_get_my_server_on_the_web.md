---
title: "How to get my server on the web"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by Richardc0077 on 2014-05-01
Hi to all

I have just setup my server 14.04 to run a computer aided dispatch. the system runs fine on intranet but i would like to now allow access to the data base from the web.

I have all the update and upgrades installed and _**lamp**_ is installed plus other files needed to run the program. including phpmysqladmin.

i have a static ip and a domain name. Whats next ??? Do I need to install any other components of Ubuntu. the modem is 3g modem and i think i am having trouble with the static ip and am thinking about changing it back to dhcp and running noip.

Any advise would be very helpful.

Many thanks

Richard C

---

### Post by TheFu on 2014-05-01
Can't tell what is wrong based on your description. [http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site](http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site) might help.  Whatever you do, do NOT allow phpmysqladmin to be reached from the internet. It is a commonly used method to take over web servers. 

If you can post the domain name, that would be helpful too.  Many cellular data providers do NOT allow inbound connections, however.

---

### Post by Richardc0077 on 2014-05-01
Hi Many thanks for that. I agree I may have mislead you in that i do not want phpmyadmin on the web. What i ment to say is that the 2 programs run fine onthe local net but now i want to allow others to be able to use the dispatch bookings on the web and to be able to get these bookings out to the cars.

Many thanks

Richard C

---

### Post by TheFu on 2014-05-01
What is the domainname?

---

### Post by lisati on 2014-05-01
Just for clarification, when you mention static IP, are you referring to one with your ISP or one on your router/modem?

Having a static IP address on your router can simplify setting up things like port forwarding on your router.

Having a static IP address with your ISP isn't always necessary. The PROs include avoiding the need to update your machine's IP address with your domain registrar. The CONs include the possibility of having to pay a little bit more each month.

---

### Post by drink1297 on 2014-05-02
Do you have a static Public IP, or are you only working with a LAN IP? 
You mentioned an intranet, are you connecting through a firewall?? You may need to open a path through the firewall

---

