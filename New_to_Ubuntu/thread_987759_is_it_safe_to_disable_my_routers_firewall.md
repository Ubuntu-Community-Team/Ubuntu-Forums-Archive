---
title: "is it safe to disable my routers firewall?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by jeromey on 2008-11-19
i have always had my routers firewall set to medium

(that means i have to manually forward ports for alot of apps like transmission, and any multiplayer games, and even for my xbox360)

so its beginning to become a real pain

(sometimes it just doesnt work, and sometimes i just cant figure out which ports i need to forward,)

also i have figured out that i am not able to forward the same ports to more than one machine, which really screws things up for me

and since i dont actually have fileservers or anything on my network i figure it cant be that much of a security risk to disable it


so my question is...

if i disable my routers firewall, is ubuntu's firewall by default enough to protect my machines?

---

### Post by Keen101 on 2008-11-19
It all depends on your definition of safe.

I'd say no it's not safe per say. But, given that Linux is a lot more secure than windows i'll say you probably don't have much to worry about. It all comes down to whether you think you will be attacked.

If you are having to forward that much stuff, then just disable it. But, realize that it is slightly risky. I personally wouldn't worry, but that's me.

Are all your machines running ubuntu? If yes, then I'd say don't worry about it unless it's a windows machine. 

That's just my take on it. Others might have different views.

---

### Post by bodhi.zazen on 2008-11-19
> **jeromey said:**
> i have always had my routers firewall set to medium

(that means i have to manually forward ports for alot of apps like transmission, and any multiplayer games, and even for my xbox360)

so its beginning to become a real pain

(sometimes it just doesnt work, and sometimes i just cant figure out which ports i need to forward,)

Well, part of this is because you are using peer-to-peer sharware , which is often configured to use a random port so that IP provides can not block the activity as easily.

In general, your firewall should not be blocking connections you initiate ...

> also i have figured out that i am not able to forward the same ports to more than one machine, which really screws things up for me

This is often the case with most routers, and is not necessarily a problem with the firewall.

> and since i dont actually have fileservers or anything on my network i figure it cant be that much of a security risk to disable it

so my question is...

if i disable my routers firewall, is ubuntu's firewall by default enough to protect my machines?

If you are not running any servers you should be "OK". I suggest you take a look at UFW or GUFW ;)

---

### Post by jeromey on 2008-11-19
yes, all my machines are running ubuntu, except for the xbox360 obviously

---

### Post by handydan918 on 2008-11-19
If you are talking about Local Area Network traffic, it may be best to invest in a hub, in addition to your existing router. The router provdes network address translation (NAT) which is a valuable firewalling function. Internall, you probably don't need it. If you simply plug in a ethernet hub (about 20 usd) behind (or "inside") the NAT router, you will be able to freely use your lan.

This approach won't have any effect on external traffic, so if I have misunderstood your issue, disregard.

---

### Post by handydan918 on 2008-11-19
> **jeromey said:**
> yes, all my machines are running ubuntu, except for the xbox360 obviously

BTW, that isn't necessarily obvious. Linux can be installed on an xbox....;)

---

### Post by jeromey on 2008-11-19
> BTW, that isn't necessarily obvious. Linux can be installed on an xbox....

hmm, interesting....

---

