---
title: "[ubutnu server] Got myself into a weird situation with apache and ports"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by Rifts on 2013-07-16
Hey everyone,

I'm new to ubuntu and linux but here is the situation:

I'm running ubuntu 12.04.2 LTS. My ISP is blocking port 80 so I can't access my apache server unless i'm on my local network. I changed the port to 8010 for apache and the port redirect is working fine.

If I go to xx.xx.xx.xx:8010 of my ip I can see the default "Its working" screen.

Now my question is how do I change this so someone can just go to my IP or even an actual url and it will redirect to the correct port but without showing that?

---

### Post by theDaveTheRave on 2013-07-16
Rifts,

you should be able to use a redirect that goes to the IP address you have used, just append the port details to the end, as you have done.

However if your ISP is blocking port 80 you wouldn't be able to browse the web !

So your issue is more likely that port forwarding on you box is not configured to forward requests on your local network.

Go into the configuration of your box (normally accessed via 192.168.0.1 or similar) and find the page that enables the firewall and port forwarding rules. You probably also want to set your server to a fixed IP, normally available from the same screen.

you will obviously need to access your box with the admin login / password.

David

---

### Post by SeijiSensei on 2013-07-16
The short answer is that you cannot do so easily.

You could use a URL-shortening site like TinyURL or bitly.  I believe some of them let you include port numbers in the original URL specification.

---

### Post by Rifts on 2013-07-16
Thanks for the replies. I can forward any other port fine, just not 80. That's why I believe it's my ISP, I read a lot of the major ISPs do this. It's OK though i've decided I will only be accessing this server through code so I can use port 8010.

---

