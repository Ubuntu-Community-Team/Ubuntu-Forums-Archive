---
title: "how do I SSH from outside my network"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by marineco on 2012-03-18
Hi all,
I have googled the heck out of this, and can't find an answer that has enough newb language. I have just recently set up a server running ubuntu 10.04 with zentyal. I use SSH for the most part to access it while inside the office, (server is headless) but Google as I might, I can't sort out how to get into it from home. I use Putty for my SSH program, since I usually am on a windows machine. I did find a how to mentioning that a good idea is to change the port in my sshd_config filefrom the default 22 to 443. apparently this is the port used by the https protocol. 

ok, tried it. The SSH part works fine in the building, but I still need to sort out how to do it elsewhere. However, my web interface for zentyal stops letting me in when I do that.

I made an attempt at forwarding the port in my router, as mentioned in the how to I found, but not sure if I had the settings right on that. So there we have it.. settings inside the building done (I think) but what do I do on the other end? I just need to be able to pull up my terminal, and if possible my zentyal web interface, from a remote location. 

In case it matters, we are currently only wanting to use this basically as a NAS. No website or anything else attached to it for now, but I may play with some additional stuff for learning purposes. Also, I need my guys to be able to access some of the files remotely, so I plan to set up a VPN once I figure out how. Not sure if any of that is relevant or not, but there you have it, just in case.

---

### Post by HeroOfCanton on 2012-03-18
Check your settings for porting from the router to the server again. Also be sure your router is set to allow incoming requests to that port.

For clarification, are you getting to the log in screen and being denied, or not reaching the server at all via the internet?

Basic checks:
1) Your server is accepting connections (We know this because you can connect in-house)
2) You can reach the log in screen via your external IP address, aka the routers internet IP. (If not, you're not making it to the server from the router)
3) You can log in successfully from the log in screen.

Suggestion: If you can't find anything on google for your router and  sentyal look for your router and setting up for online gaming. Games  often require direct access from the router and will produce better  results on the same topic.

---

### Post by marineco on 2012-03-18
Not reaching the server at all. I've made some attempts, but not even sure I had client side info entered properly. I know I use the router address, but unsure how to make sure it goes to the server from there.  I set up a forward in the router, using port 443, telling it to forward that to the server IP.  Can't remember if I set it to TCP or UDP. I think UDP. That's about as far as I've gotten.

---

### Post by HeroOfCanton on 2012-03-18
22 is the default port for SSH. 443 is normally for SSL (HTTPS). Not sure if that is having an effect on you. It should also be TCP.

[Common Port List]("http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#Well-known_ports")

Unfortunately different routers all have different ways to setup the forwarding so I can't really help on that without asking for more info than you should probably give for your office router. Just look for a good tutorial for your equipment (preferably the manual if you have one or can download it) and get that port forwarding working correctly. I'm fairly certain that's where your problem lies.

Security tip: If you're not already, consider using an ssh key rather than password for logins since this will be accessible to the outside world.

---

### Post by marineco on 2012-03-20
Been a super busy week, but I finally got some time, I'm as sure as I can be that my port forwarding is set up properly. But I still get nothing trying to connect. I took my best guesses, but I think I just don't know how to set up the client side properly.

I may have made it easier, or added a degree of difficulty, but I set up a DDNS account. That means I just put in *myaccount.ddnssite.com *for the hostnameand the port number that I have forwarded (the same one I am listening for on the server) 

Correct?

Edit - changed some font formatting

---

