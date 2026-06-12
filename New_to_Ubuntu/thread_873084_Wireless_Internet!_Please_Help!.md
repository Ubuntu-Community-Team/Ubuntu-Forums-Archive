---
title: "Wireless Internet! Please Help!"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by liquidphilosopher on 2008-07-28
Hi! I have a pc that is running Ubuntu Hardy via a wireless router (Westell VersaLink Model 327W). The problem is that I have just bought a laptop that runs vista and although I can connect to the router, I cannot access the internet. Is there something that I should have done on Ubuntu's end to allow the laptop the rights to access the internet. Thank You in Advance!!

---

### Post by tamoneya on 2008-07-28
the PC will not affect how your laptop interacts with your router.  Most likely there is something odd in your vista configuration.  If ubuntu is able to connect to the internet fine through the router like you say then the router is working fine so i would investigate vista.

---

### Post by stevoo on 2008-07-28
well , if you connect to the router then you are ok. 
try this commands in the terminal
ping [www.google.com](www.google.com) -c 4
ifconfig

and post us the results please :)

---

### Post by mikewhatever on 2008-07-28
Is there a problem connecting with Ubuntu or with Vista?

---

### Post by liquidphilosopher on 2008-07-28
sorry it took me soooo lomg to get back... my router is on a linux pc. no problems with connection. my laptop runs vista and cannot connect to the internet via the wireless router on the linux pc...

---

### Post by geekygirl on 2008-07-28
Sounds more like a Vista problem, sometimes it can be a pain in the glutes to get it working with wifi! (it can be temperamental!)

Did you open the Network Connections window in Vista and click on the red 'x' that will be appearing between the router image and the greyed out image of the globe? 

Vista should go and automatically repair the connection and clear out the DNS cache, and DCHP server resets..etc etc and should fix the problem, beleive it or not its pretty good at it!

Failing that, delete any settings you may have entered into the Network Settings window about your wifi connection and let Vista discover them for itself and see how you go.

---

### Post by ready4thebreak on 2008-07-28
You may just have to look for the ealier drivers. You have to look around and find out exactly which drivers you need to get it to work. Then you can use the Add/Remove Application to get the ndiswapper tool, which allows you to use that Windows driver in Ubuntu. I took me a while to figure it out, so I'll pass along any info I can to help.

---

### Post by tamoneya on 2008-07-28
> **liquidphilosopher said:**
> sorry it took me soooo lomg to get back... my router is on a linux pc. no problems with connection. my laptop runs vista and cannot connect to the internet via the wireless router on the linux pc...

what do you mean by "the router is on the linux PC".  arent they different physical devices?

---

### Post by liquidphilosopher on 2008-07-28
I have just dual booted with Ubuntu and have no prob. on that end. so it is a vista problem. I have troubleshooted with some of the drivers and have connected 2 out of 4 attempts, and it seems slow. I'm gonna go head and check with conflicted applications since the laptop is still new and possible drivers. Thank you for putting me on the right track.

---

