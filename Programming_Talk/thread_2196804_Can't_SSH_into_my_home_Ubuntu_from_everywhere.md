---
title: "Can't SSH into my home Ubuntu from everywhere"
date: 2013-12-31
forum: Programming Talk
---

### Post by achampsaur on 2013-12-31
Hello,
This is not directly related to programming, but I imagine people here might a better grasp on my problem. Thanks for reading.
I have Ubuntu set up on my home computer. I am able to SSH into it from my university server, and from any computer on my home LAN. However, when I am at say, a friend's house, or a coffee shop, I cannot SSH directly into my computer. I first have to go through my University server. This is quite frustrating.
Also, the problem is not specific to my Ubuntu machine. I also have a Mac at home, and when I try to SSH into it, I get the same results.

I have tried asking a number of people about this without luck. Thanks in advance for any help.

---

### Post by Iowan on 2013-12-31
Are you using keys or passwords?
I closed your previous thread:
[http://ubuntuforums.org/showthread.php?t=2185296](http://ubuntuforums.org/showthread.php?t=2185296)
From the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
> Do not cross post, or post the same thing in multiple locations.
You can use the Report Post button to request staff to move the thread to a different forum.

---

### Post by ofnuts on 2014-01-01
No related at all to programming... 

Normaly your computer is isolated from the Internet by a modem/router that uses [NAT]("http://en.wikipedia.org/wiki/NAT"), and incoming connections (like SSH from an outside computer) are rejected. You have to configure the router so that incoming connections to a given port are forwarded to some designated local address and port (DNAT). You may have such a thing already set up, but currently restricted to a range of acceptable addresses (your university Internet gateway) which is a good idea. If you open this up, make sure you have some very good passwords, and an up-to-date software. There are possible additional protections like ["port knocking"]("http://en.wikipedia.org/wiki/Port_knocking").

---

### Post by TheFu on 2014-03-26
Networking can be complex.
Different ISPs block different ports to "protect" end-users.
Any source and target can have completely different allowed ports. There is no way to know without testing and a month later, one of the network providers may change their filters.

So - first - what is the public IP for the target machine? Is it really public, non-bogon, and routable?
Many places like cafes and hotels block what they consider strange ports - like ssh.  To get around those and get through any proxy server they have, listen for ssh on port 443.

Some places block server access to DHCP subnets - like DSL and cable residential networks too. If they do this by domain, then be prepared with the IP address.

Also - don't forget that ~/.ssh/config is your friend for making ssh easier to use.  Strange ports, different userids, friendly names for the remote server instead of some funky name auto-generated.

Lastly - secure your ssh server. Do not allow passwords, only keys. Use **fail2ban** to block failed attempts.  ssh is one of those few tools that are easier, more convenient AND very secure.  I prefer to let the router do the port translation from 443 to 22 for me. Much easier that way and it is clear when I'm using the WAN interface or the LAN one - since 22 is only for internal use.

---

