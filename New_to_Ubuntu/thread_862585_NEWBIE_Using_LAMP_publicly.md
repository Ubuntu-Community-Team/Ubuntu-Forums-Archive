---
title: "NEWBIE: Using LAMP publicly"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by BigBadBaz on 2008-07-17
Hi. I'm a complete newbie to servers (and most of networking) in general. I just finished setting up an Ubuntu 8.04 LAMP server, and my boss wants me to make it available publicly.

First problem: I don't know how I would access the box privately, certainly not publicly, and I don't even know what I would use it for. Help?!

Second problem: How would I make the box accessible publicly?

Third problem: How could I set the box up publicly in such a way that my server and my whole network is not open for the world to play with?

Thanks in advance!

---

### Post by someonestolemyname on 2008-07-18
To make your server available publicly (as in HTTP? web server?), forward port 80 in your router to it. It is only accessible via IP address right now (run ifconfig to get that). Also, making your server publicly available *is* "open for the world to play with". 

If you just forward Port 80 (HTTP), than that is the only thing people would be able to get to. If you have no firewall, and are directly connected to the internet, anyone with your IP address can attempt to mess with it.

Please be more specific... What do you mean by 'publicly accessible'?

---

### Post by BigBadBaz on 2008-07-18
Sorry. As I said, I'm a real newbie. Although, to your credit you did understand what I meant. I want to make it into a web server.

I forwarded Port 80 to my server's IP address.

Question. My server is behind a seperate router. Is there any way to test if it's working from outside that router, bu still within the network?

Also, my network is set up Like this: Gateway > Router > Router > ... > LAMP box. Can I get to my server publicly in this case? If so, how would I do this? Keep forwarding Port 80?

Lastly, what do you mean by firewall? Do you mean a firewall on my LAMP box, or on my network? I didn't set up any security stuff on my LAMP box yet, so unless it sets stuff up automatically, it has nothing.

Thanks

---

### Post by halitech on 2008-07-18
to find out your public IP if you don't have access to your router, go to [http://IPchicken.com](http://IPchicken.com) and it should tell you the public ip. If it works externally it should still work internally.

I'm not sure on the dual router setup but I would think you would need to forward port 80 on both of them.

---

### Post by someonestolemyname on 2008-07-18
Forwarding port 80 multiple times should be fine to my knowledge. halitech's solution is correct, find your external IP and use that to see if the forwarding is working.

By firewall I meant a router, as most of them have built-in firewalls. You have several, so I'm sure 
it's fine. Although if you want a firewall on the server, try UFW [http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html"). That is much easier than the old way.

If you have any more questions, feel free to ask!

Daniel

---

### Post by BigBadBaz on 2008-07-23
Hi. Sorry I haven't posted back in a while, things just got really crazy in the office. 

My boss now wants to know something else. He has heard that it's possible to turn a LAMP box into a firewall. He's not sure if that means replacing the router with the box, using 2 NICs or what.

Do any of you know anything about this?

Thanks all.

---

### Post by halitech on 2008-07-23
You certainly can and there are several distros set up exactly for this purpose. Check here
[http://www.linux.org/dist/list.html](http://www.linux.org/dist/list.html)

I would say Ubuntu can probably do it as well but others like smoothwall (	[http://www.smoothwall.org/](http://www.smoothwall.org/) ) are designed just for the purpose you are talking about

---

### Post by BigBadBaz on 2008-07-23
Thanks a lot halitech, Smoothwall looks PERFECT!

Just a quick question, is it only usable as a GUI, or is there a command line? If there is a command line, is there any point in using it (like in Ubuntu)?

EDIT: Would i386 work on a 64-bit processor? Also, is there any difference between the two (besides, perhaps speed)?

---

### Post by halitech on 2008-07-23
generally the gui is just a front end to the command line so I would have to guess that if you don't want to use the gui you don't have to but will make certain things easier to configure.

i386 will work on 64bit but 64bit won't work on i386. I dont think there would even be much of a speed difference. I don't have a 64bit machien but from what I've read here, 32bit is(was?) more supported in the apps department then 64bit

---

### Post by BigBadBaz on 2008-07-23
OK. Thanks a lot. That's what I wanted to know. (I'll probably use i386 even thogh I have an AMD Athlon 64 on that machine.)

---

### Post by halitech on 2008-07-23
glad to help out :)

---

