---
title: "Authentication Required Apache site over internet"
date: 2014-09-15
forum: New to Ubuntu
---

### Post by nyo2 on 2014-09-15
Hello im new to ubuntu i installed apache 2.4 

 I can't seem to access my site via typing my IP address over the net. It asks for authentication in which i dont know the user and pass/ But on localhost it shows up fine (it works page).

 I have tried making an .htaccess file and it works for my localhost but still the different authentication over the internet.

 How do I modify/remove the authentication?

---

### Post by Lars Noodén on 2014-09-15
First, you should remove or rename the .htaccess file.  You don't need or want it if you have access to the configuration of the server yourself.  It will just add confusion, either now or later. 

Next, how are you trying to access the web server from a second machine, on the same LAN or from across the Internet?  The details will be quite different if you are going over the net and need to set port forwarding on your router than if you are just going over the LAN.

---

### Post by nyo2 on 2014-09-15
The router was sent to us by our ISP and I can't really do much other than change the WiFi name. I think this is the case. Ill see if i can change my router.

On the default install of apache does it really require authentication if you access your site over the internet?

---

### Post by Lars Noodén on 2014-09-15
No, Apache itself would not require authentication if you are accessing it over the Internet.  But if you are trying to access it via the Internet and have not set up your modem/router for port forwarding of ports 80 and 443 then you are not connecting to your Apache server but instead to the modem/router itself.  That will ask for authentication.  What is the exact wording in the authentication dialog?  It may have a clue about what you are really connecting to.

---

### Post by nyo2 on 2014-09-15
Yep, I was connecting to the router itself.

My router is a Prolink h50004n and i tried following this guide to port forwarding 

[http://portforward.com/english/routers/port_forwarding/Prolink/H5004N/Apache.htm](http://portforward.com/english/routers/port_forwarding/Prolink/H5004N/Apache.htm)

However it still connects me to my router.

---

### Post by Lars Noodén on 2014-09-15
I notice that in the example, the field for LAN IP Address was left blank.  That has to be filled in with your Apache machine's address.  That in turn leads to the question of how the router can set a fixed LAN IP address for your Apache machine.

---

### Post by nyo2 on 2014-09-15
I checked my LAN IP it returned something like 192.168.... but at the time it was still dynamic. I thought it would work. 

Do i really need to set my lan IP to static?

---

### Post by yancek on 2014-09-15
The IP addresses in the range 192.168.* are reserved for local machines.  You can connect to it from another machine on a local network however.  You need to set the Listen directive to accept connections from an IP range.  There are several settings which you need to change in the apache configuration files.  On Ubuntu 12.04 these file are in /etc/apache2 although the location may be different in 14.04.

---

### Post by Lars Noodén on 2014-09-16
> **nyo2 said:**
> I checked my LAN IP it returned something like 192.168.... but at the time it was still dynamic. I thought it would work. 

Do i really need to set my lan IP to static?

Forwarding from the router will work as long as it forwards to an address which is used by your Apache machine.

If you set up the router so that machine always gets the same address then forwarding will always work.  Otherwise, if one day you reboot the Apache machine and it gets a new LAN address then you will have to go back into the router and tune forwarding to the new LAN address.  The router only forwards to a designated LAN IP, it's not smart enough to find the right macnine using other methods.

---

### Post by nyo2 on 2014-09-16
Thank you for the info! However it still directs me to my wifi even though LAN ip matches.

Here is my ports.conf

> Listen 80
Listen 443

<IfModule ssl_module>
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

netstat -tulpn | grep :80
Results:
tcp6       0      0 :::80                   :::*                    LISTEN      1189/apache2    
grep 443
tcp6       0      0 :::443                  :::*                    LISTEN      2671/apache2 


is it possible that this is a firewall problem?

---

### Post by Lars Noodén on 2014-09-16
Do you have a second machine on the same LAN?  If so, then  you can try connecting using a web browser from that second machine.  However, that will probably work and there is probably something still missing from the router configuration and how it is doing forwarding.  Maybe the router's admin access needs to be turned off for the external address.  It's probably a good idea to allow router configuration only from the LAN anyway.

---

### Post by nyo2 on 2014-09-16
I appreciate the help Lars. I think it all goes down on my router. I cant figure out how to disable remote access on it. 

I really think its something around here.
[ATTACH=CONFIG]256479[/ATTACH]
[ATTACH=CONFIG]256480[/ATTACH]

---

### Post by Lars Noodén on 2014-09-16
The picture did not come through.  But there is probably a check box, or similar, somewhere which can restrict the router's admin access to just the LAN.  Time to maybe start systematically perusing the menus and see where that option is hidden.

---

### Post by nyo2 on 2014-09-16
I reupped the image. Ill try to find that button through the manual.

---

### Post by nerdtron on 2014-09-16
There are two key things to make you webpage accessible from the web outside your network.

1. Set a dedicated/static IP on the web server. Something like 192.168.1.10
Checking:
a. On your web server, open a browser and type 192.168.1.10 and you should see your web page. CHECK?
b. On another machine on your local network, open a browser and type 192.168.1.10 and you should see your web page. CHECK?

2. Setup port forwarding on the router to forward port 80 to your web server IP 192.168.1.10
Checking:
a. Outside your network, or on the internet, open a browser and type the public IP your ISP have given you and you should see your web page.

If number 1 works, then you can proceed to 2. If not, then we should make sure that step 1 is working.

---

### Post by nyo2 on 2014-09-16
Number 1 works. Thing is my router can be accessed remotely so when i type my ip this is the one that shows up. Also this router was given by PLDT if that info helps.

---

### Post by nerdtron on 2014-09-16
> **nyo2 said:**
> Number 1 works. Thing is my router can be accessed remotely so when i type my ip this is the one that shows up. Also this router was given by PLDT if that info helps.

That it, login to the router and then look at settings on port forwarding. You can also post screenshots here for us to see the settings.

"PLDC este PLDT pa la yan" :)

---

### Post by nyo2 on 2014-09-16
Yun nga eh.

Things I did

Set the port forwarding in the router
Connected to my Server using 192.168..... via the same network (works)
Connected to my router (expecting it to be my server) using my ip over the same network

Ill try to connect to it by using a device thats not over my network.

---

### Post by nyo2 on 2014-09-17
Thanks guys it works now.

If anyone will have this problem years from now. After setting the port forwarding on your router and disabling remote web access, make sure that you test it on another machine on another network. In my case I tried to access the ip (whatsmyip.com) over the same network as my server, I didnt know it still classifies as LAN on my router thats why it redirects me there. 

Thank you for the support community!

---

