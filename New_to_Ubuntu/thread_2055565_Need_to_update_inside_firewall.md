---
title: "Need to update inside firewall"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by z3nhakr on 2012-09-09
my machine is on a network with firewall/port filtering proxy (school *fp*). i think its fortinet. but things like torrents, BF3, and vpns don't work. coincidentally it also prevents me from updating or installing anything on ubuntu. Iv'e been nmappin' and looking for open ports from the inside and outside but none are showing up. btw skype does work but everything else besides http/s seems to be blocked. is there a way i can put a proxy on port 80? or another way to get my updates?

---

### Post by Cheesemill on 2012-09-09
> **z3nhakr said:**
> my machine is on a network with firewall/port filtering proxy (school *fp*). i think its fortinet. but things like torrents, BF3, and vpns don't work. coincidentally it also prevents me from updating or installing anything on ubuntu. Iv'e been nmappin' and looking for open ports from the inside and outside but none are showing up. btw skype does work but everything else besides http/s seems to be blocked. is there a way i can put a proxy on port 80? or another way to get my updates?

Ask the IT staff at school if they can help you.

Scanning your school network is a sure way to get in trouble.

---

### Post by z3nhakr on 2012-09-09
The IT at my school is outsourced so i cant really go and ask them(the web filtering part). the only IT related people in the school only know windows. besides since when has some anonymous port scanning ever gotten anyone into trouble?

---

### Post by Cheesemill on 2012-09-09
> **z3nhakr said:**
> The IT at my school is outsourced so i cant really go and ask them(the web filtering part). the only IT related people in the school only know windows. besides since when has some anonymous port scanning ever gotten anyone into trouble?

Well its against the IT Usage Policy that all of the students have to sign at a college I sometimes do work for.

If it's your machine then just take it home to update it, if it's the schools machine then you'll have to ask for the Ubuntu mirror you are using to be whitelisted (I've run outsourced IT before and it's the sort of thing that you expect clients to ask of you, after all that's what your school is paying for).

---

### Post by z3nhakr on 2012-09-09
its my machine and im stuck here for about a month so i cant just take it home and update it. besides if i get into trouble for updating my computer its on me not you so why not help?
btw the ports that are open are 21, 80, 113, 443, 1863, 5050, 5190, 8008, and 8010

---

### Post by Cheesemill on 2012-09-09
Without knowing your exact network setup and the filtering software being used it's impossible to answer.

---

### Post by d3v1150m471c on 2012-09-09
try using tor ;-)

tor can form circuits over ports 80 and 443, that should allow you to evade the firewall using something like polipo or socat
```

socat tcp4-listen:6667,bind=127.0.0.1,reuseaddr socks4a:127.0.0.1:irc.somebannedirc.net:6667,socksport=9050 &

irssi -c localhost -p 6667

```

---

### Post by mips on 2012-09-09
If you need to access via a proxy Synaptic->Preferences->Network for proxy config.

See also [https://answers.launchpad.net/ubuntu/+source/synaptic/+question/1320](https://answers.launchpad.net/ubuntu/+source/synaptic/+question/1320)

Synaptic/apt uses port 80 for http based downloads if I'm not mistaken.

---

### Post by bmdaily on 2012-09-12
I'm actually having this same problem right now. My school's university must have the port blocked that Ubuntu Software Center uses to update. So I'm thinking these are my options, any and all of which I need some help with to solve if any of you know the answer:

A.) I can figure out which port it does use and then try to talk to my school's IT department about unblocking it. Knowing my school, this isn't impossible but a sure to be hassle. 

B.) I can change the port that the software center wants to use to 80. I've found enough information online to assume that will work but not enough to know how to go about doing that. 

So if anyone can provide me with the info I need for one or both of these solutions, or has another solution, let me know. Thanks a bunch!

---

### Post by bmdaily on 2012-09-12
P.S.- I did find this blog post in which someone seemed to find a workaround for this problem but it doesn't seem to work for Precise Pangolin. I'm assuming that is would still work if some minor things in the instructions are changed. Either way, here's the link:

[http://www.omgubuntu.co.uk/2011/01/how-to-add-repositories-to-ubuntu-from-behind-a-firewall/](http://www.omgubuntu.co.uk/2011/01/how-to-add-repositories-to-ubuntu-from-behind-a-firewall/)

---

### Post by alphacrucis2 on 2012-09-13
> **bmdaily said:**
> I'm actually having this same problem right now. My school's university must have the port blocked that Ubuntu Software Center uses to update. So I'm thinking these are my options, any and all of which I need some help with to solve if any of you know the answer:

A.) I can figure out which port it does use and then try to talk to my school's IT department about unblocking it. Knowing my school, this isn't impossible but a sure to be hassle. 

B.) I can change the port that the software center wants to use to 80. I've found enough information online to assume that will work but not enough to know how to go about doing that. 

So if anyone can provide me with the info I need for one or both of these solutions, or has another solution, let me know. Thanks a bunch!


See this :

[https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

---

