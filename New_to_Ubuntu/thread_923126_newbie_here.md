---
title: "newbie here"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by wizardslovak on 2008-09-18
HEllo people
well i am new to ubuntu linux , i have it on virtualbox,and soon i would like to make ubuntu file server at home.
And here i got my questions,Can anyone tell me how to set up Ubuntu server as file server(i got 1 linux pc and 2 xp pcs in my network) ,How to set up linksys router (dd-wrt micro version) so i can share files?
i did read lot of how to's but i didnt find nowhere about setting up router.If anyone can help i will really appreciated 

\thank you in advance 
WS

---

### Post by bobnutfield on 2008-09-18
Have a look at this.  This will probably tell you all you need:

[https://wiki.ubuntu.com/ComprehensiveSambaGuide]("https://wiki.ubuntu.com/ComprehensiveSambaGuide")

---

### Post by wizardslovak on 2008-09-18
> **bobnutfield said:**
> Have a look at this.  This will probably tell you all you need:

[https://wiki.ubuntu.com/ComprehensiveSambaGuide]("https://wiki.ubuntu.com/ComprehensiveSambaGuide")

good guide but still there is nothing about routers 
but thank you anyways

---

### Post by hellion0 on 2008-09-18
I'm not 100% sure on that type of router, but I don't think you need to mess with it if you want to make one machine a local fileserver to the others on the same router. Just make sure you set up a static IP on the Ubuntu machine (that should be possible on the Linux machine itself).

---

### Post by bobnutfield on 2008-09-18
I don't understand what you need about routers.  You don't need to set up a router.  Typically, a router simply acts as a central hub to connect your computers.  If it is a ADSL modem/router, then it is your connection to the internet, as well as the hub for other computers on the network.  If you are setting up encryption for your network, then that process is specific to the router manufacturer and should be include on the router setup page, an IP address on your network which connects to the router setup in your browser (something like 192.168.2.0. for example.)  

So, you simply connect your pc's to the router, and set up each machine for the network, not the router.

---

### Post by bobnutfield on 2008-09-18
One additional point, hellion0 is correct.  If you want a continuous file server, then the server machine must be a static IP address, and your manufacturer's instructions for you router will tell you how to set that up.

---

### Post by amac777 on 2008-09-18
> **wizardslovak said:**
> Can anyone tell me how to set up Ubuntu server as file server(i got 1 linux pc and 2 xp pcs in my network)

I think the samba guide posted above would work. 

Or, if you want to just try a simple shared folder between xp and your ubuntu box, just right click on the folder you want to share on the ubuntu box (in nautilus) and chose "Share". (You can select if you want it readonly/writeable etc) Then follow the prompts to make it shareable using Samba for windows and it will install the necessary programs. So it's pretty easy and has a gui built in already.

I think the only thing you have to do after that is add a samba user / password so you can access that shared folder from xp. The command to do this is:

sudo smbpasswd -a <username>

where <username> is your login user name on ubuntu and you can set the same or a different password for your samba password.

> **wizardslovak said:**
> How to set up linksys router (dd-wrt micro version) so i can share files?

I think a server for a local LAN would not need any kind of configuration on your router. It should just work as all your computers will be on the same local lan. If this is not what you are trying to do, maybe explain what you are trying to do and it will be easier to help with this part.

---

### Post by y@w on 2008-09-18
Did you want to share files across the web? If not then Samba without tweaking the firewall will do just fine, but if so then we can help find an alternative.

---

### Post by amac777 on 2008-09-18
Sorry, I forgot that Samba has to be restarted after you add the new user / password so that the changes will take effect. Open a terminal window and type in the following:

sudo /etc/init.d/samba restart

---

