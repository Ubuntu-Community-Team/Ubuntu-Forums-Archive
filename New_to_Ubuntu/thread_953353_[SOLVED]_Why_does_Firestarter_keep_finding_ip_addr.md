---
title: "[SOLVED] Why does Firestarter keep finding ip addresses to block?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-10-20
Is it bad that Firestarter keeps blocking ip addresses.

Does this mean I am under attack by other people?

---

### Post by eentonig on 2008-10-20
> **pluckypigeon said:**
> Is it bad that Firestarter keeps blocking ip addresses.

No, it's what it's supposed to do. As long as you can keep doing the things that you want to do.

> **pluckypigeon said:**
> Does this mean I am under attack by other people?

Every pc that's connected on the internet is under attack by other people.

For example. Last 24 hours, my firewall registered 464 suspicious connection attempts (not individual packets). And I consider that to be extremely low.

---

### Post by pluckypigeon on 2008-10-20
> **eentonig said:**
> No, it's what it's supposed to do. As long as you can keep doing the things that you want to do.



Every pc that's connected on the internet is under attack by other people.

For example. Last 24 hours, my firewall registered 464 suspicious connection attempts (not individual packets). And I consider that to be extremely low.

So does this mean that without the firewall they'd get in?

---

### Post by sethvath on 2008-10-20
If you're using a closed ports system like ubuntu you have nothing much to worry about. Most malicious hackers or script kiddies start with a [port scan]("http://en.wikipedia.org/wiki/Portscanning") to seek out potential targets. Once they know know a particular port is open on a target computer they can proceed to infiltrate via that port.

---

### Post by pluckypigeon on 2008-10-20
> **sethvath said:**
> If you're using a closed ports system like ubuntu you have nothing much to worry about. Most malicious hackers or script kiddies start with a [port scan]("http://en.wikipedia.org/wiki/Portscanning") to seek out potential targets. Once they know know a particular port is open on a target computer they can proceed to infiltrate via that port.

thanks

Would it be easy for them to get in if they did find a port??

And what do you mean by "nothing much"?

---

### Post by sethvath on 2008-10-20
That depends on which port it is. If you look at the port scan link I added above, there are many types of scans. Port scans are just one of them. For instance the port 8080 is a popular alternative http port, and someone finds that particular port open on your system. The way to "hack" into your system would be to masquerade as a packet and make you install a backdoor and unload whatever payload it is sent to carry. An analogy would be sending a spy into your castle from a secret backdoor they discovered. With the spy inside, they can start to bring in more men, ammunition, explosives and cause all sorts of mayhem. 

With Ubuntu, all unused ports are closed by default. Say someone scanning for ports on your network will not be able to see them. Port scanning works like pinging everyone on your instant messenger list. If they reply it means they're available. No reply means they might be afk or does not exist. There is "nothing much" they can do if you choose not to reply to their ping.

---

### Post by pluckypigeon on 2008-10-20
> **sethvath said:**
> That depends on which port it is. If you look at the port scan link I added above, there are many types of scans. Port scans are just one of them. For instance the port 8080 is a popular alternative http port, and someone finds that particular port open on your system. The way to "hack" into your system would be to masquerade as a packet and make you install a backdoor and unload whatever payload it is sent to carry. An analogy would be sending a spy into your castle from a secret backdoor they discovered. With the spy inside, they can start to bring in more men, ammunition, explosives and cause all sorts of mayhem. 

With Ubuntu, all unused ports are closed by default. Say someone scanning for ports on your network will not be able to see them. Port scanning works like pinging everyone on your instant messenger list. If they reply it means they're available. No reply means they might be afk or does not exist. There is "nothing much" they can do if you choose not to reply to their ping.

Thank you. You have been really helpful. I was reading about security and I got paranoid. 

Also thanks for the interesting reading!

---

### Post by hyper_ch on 2008-10-20
normally, you don't have to worry about firewall on linux...

---

### Post by alphacrucis2 on 2008-10-20
> **pluckypigeon said:**
> thanks

Would it be easy for them to get in if they did find a port??

And what do you mean by "nothing much"?

Possibly. You could for example run an sshd to deliberately allow remote access to your PC from the internet so you can access it remotely yourself. Obviously if you were doing that you would want to make sure you are using strong passwords or  digital certs to keep unauthorised access at bay. Typically someone trying to break in via ssh will try using root as the usercode, which isn't normally going to get far on a Ubuntu machine. If you secure things properly they are no more than an annoyance. Some people use a firewall to drop certain country address ranges where these scans are most prevalent (I wont name any names here) just to get rid of of a big percentage of the annoyance. There is less overhead to reject them in netfilter, than let them get further up the protocol stack.

---

