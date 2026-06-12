---
title: "Setting up a home file/web server"
date: 2014-06-17
forum: New to Ubuntu
---

### Post by agonus on 2014-06-17
Hi all.

This has probably been asked a million times but what the hell.

I'm trying to set up a file and web server on my Ubuntu box (I'm running Desktop, not Server - it won't work) and I'm completely stuck. I've tried several do-it-yourself guides and so far nothing doing. Basically, I want to be able to host a web site from the computer as well as have the ability to access my files on it from my Windows PC (as well as transfer files back and forth). I'm running a wireless network. I've installed Apache on the Linux box and so far I can get the webpage to load on my Windows PC's browser from the Linux box's local IP but that's about it. My knowledge of networking, TCP/IP, etc. is pretty minimal. I can't access the website from the Internet (i.e. outside the local network) and I can't even get the Linux box to show up on my Windows PC's network. I've tried what is supposedly the computer's public IP in my Windows browser but that just takes me to the modem's configuration page.

I'm completely at a loss as to what to do next. I've tried my ISP's tech support but that got me nowhere. I'm thinking about consulting some local web design/networking firms but I'm hoping I can just do this myself for free.

I'd be enormously grateful for any suggestions at all.

-Ben

---

### Post by CharlesA on 2014-06-17
You would probably have to set up Samba to share with Windows machines.

See here: [http://charlesauer.net/tutorials/ubuntu/samba3-ubuntu.php](http://charlesauer.net/tutorials/ubuntu/samba3-ubuntu.php)

As far as serving a web site off your home connection, it is unlikely to be ideal. Most residential ISPs block port 80 and port 25 to prevent people from running servers on their connections and to "limit spam."

My suggestion would be to play around with it locally and see how it goes before trying to put anything into the big bad interwebz.

---

### Post by mastablasta on 2014-06-17
you need to forward the port on your router to your webserver. check what ports you webserver uses and also how to forward them on your router: [http://portforward.com/](http://portforward.com/)

as for sharing with Windows Samba or sFTP Will do. again you need to have all ports open on router as well as on your firewall.

it might be easier for your to administer the server using something like Zentyal, Webmin or similar GUI

---

