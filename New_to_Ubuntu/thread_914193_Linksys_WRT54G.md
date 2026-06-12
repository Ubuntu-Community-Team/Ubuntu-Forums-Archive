---
title: "Linksys WRT54G"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by jbg on 2008-09-08
I have a linksys WRT54G router with a WMP54G wireless adapter. I opened the network manager and found my wireless network. I logged on and the machine says it is connected. I have "blue" bars and ranging from 65%-85%. When I open up Firefox it will not connect. We tried pinging thru the Termal and it will not ping [www.google.com](www.google.com) but will ping by putting the IP address in it....Help !!!!!!!!!!!

---

### Post by ggaaron on 2008-09-08
Looks like a dns problem.
Have you put any dns servers to your router?

---

### Post by dioltas on 2008-09-08
Ya could be dns alright. Try putting "http://64.233.169.103/" ([google.com](google.com)) into your address bar and see if it works.

Try typing "nslookup google.com" in a terminal and see if it resolves the hostname.

Is there any other computers on the network, can they access the internet? Then you'll know if the dns problem is with the router setup or your computer setup.

Also try going online with lynx or elinks maybe, to see if its just a problem with firefox.

---

### Post by dioltas on 2008-09-08
Check your dns server by typing "cat /etc/resolv.conf".
The output should be something like:
nameserver 192.168.1.254

192.168.1.254 is my dns server (my router - a netopia one). For me it was set up automatically when I connected to the router.

If you have other windows / linux machines on the network you could check what the dns server for them is if theyre working, in windows by clicking start -> run -> cmd and typing "ipconfig /all" or in linux, again by typing "cat /etc/resolv.conf".

Then change the one on your machine by typing "sudo pico /etc/resolv.conf"


Edit: You can also change / check your dns server by clicking System, Administration, Network, Unlock, DNS

[Here's a link I just found which might help]("http://www.dslreports.com/forum/remark,15143095"). I think the default dns server for the wrt54g is 192.168.1.1 (the router itself on your network). So adding 192.168.1.1 as your dns server might fix it.

Otherwise I would suggest trying the same thing except using the dns server given by your ISP, which should be given by typing [http://192.168.1.1](http://192.168.1.1) into firefox's address bar.
The external dns server should be listed on that page.

Sorry for all the edits and stuff, its late and I'm tired / mixed up :)

---

### Post by starcannon on 2008-09-08
what kind of modem is plugged into the router? If its a westell I just completed a guide to hooking those 2 units together and will send you a link. My website isn't officially "up" yet, but I can publish that page real quick.

---

### Post by jbg on 2008-09-09
Thank you to all that responded.....I feel like an idiot....In case someone else has the same problem...do this....

Power cycle (turn off) the modum. when you repower the modum it will "find" the right IP from the router.......then everything works fine.......

---

