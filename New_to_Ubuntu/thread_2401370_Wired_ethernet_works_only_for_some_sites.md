---
title: "Wired ethernet works only for some sites"
date: 2018-09-17
forum: New to Ubuntu
---

### Post by thomasthefourth on 2018-09-17
I have a fresh install of Ubuntu desktop 16.04. Its using ethernet directly into my router. I noticed the issue initially when attempting to use Chrome or Firefox. I can reach google no problem, as well as some other sites, but most sites I try to navigate to are unreachable. From the terminal I can ping google.com with no issues, but sites such as digitalocean.com time out. I did my due diligence and searched the forums for a solution. From that research, I have tried lowering my mtu, and using the google dns in my resolv.confg (8.8.8.8) and rebooting, but I'm still not able to reach some sites.

Thanks in advance for any help,

Thomas

---

### Post by TheFu on 2018-09-17
Welcome to the forums.

Occasionally, routes to different parts of the internet fail.  It depends on where you are in the world. Just a possibility. It happens here about 2-3 times a year.

I'd also check the system logs for network issues.
And try some different ethernet cables and different ports on the switch and PC. Router/switch ports can fail and sometimes they fail due to a short somewhere.

---

### Post by thomasthefourth on 2018-09-17
> **TheFu said:**
> Welcome to the forums.

Occasionally, routes to different parts of the internet fail.  It depends on where you are in the world. Just a possibility. It happens here about 2-3 times a year.

I'd also check the system logs for network issues.
And try some different ethernet cables and different ports on the switch and PC. Router/switch ports can fail and sometimes they fail due to a short somewhere.

I tried swapping out the cable and the ports. No luck. Any particular log I should be looking at for issues? I tailed the sys log (var/log/syslog) but didn't see any of concern when trying to ping digitalocean.com.

---

### Post by Tadaen_Sylvermane on 2018-09-17
Probably not helping but an idea. Occasionally I switch my laptop between wireless and wired. The wireless connection is connected while the wire is plugged in. Occasionally for some random reason it uses the wireless when the wire is faster. It seems random to me why it does this, some stuff uses the wire, others the wireless. Results in wildly different lan transfer speeds and on occasion just seems to confuse my laptop and it can't get anywhere. Doesn't happen often enough that I've looked into it beyond figuring that it was having trouble picking which to use though.

---

### Post by thomasthefourth on 2018-09-17
> **Tadaen_Sylvermane said:**
> Probably not helping but an idea. Occasionally I switch my laptop between wireless and wired. The wireless connection is connected while the wire is plugged in. Occasionally for some random reason it uses the wireless when the wire is faster. It seems random to me why it does this, some stuff uses the wire, others the wireless. Results in wildly different lan transfer speeds and on occasion just seems to confuse my laptop and it can't get anywhere. Doesn't happen often enough that I've looked into it beyond figuring that it was having trouble picking which to use though.

Thanks for the suggestion, unfortunately this is a desktop and it only has ethernet.

---

### Post by TheFu on 2018-09-17
> **thomasthefourth said:**
> I tried swapping out the cable and the ports. No luck. Any particular log I should be looking at for issues? I tailed the sys log (var/log/syslog) but didn't see any of concern when trying to ping digitalocean.com.

I would check them all using **egrep**.

---

### Post by oldrocker99 on 2018-09-17
Try another DNS. Google's are free:
[https://developers.google.com/speed/public-dns/](https://developers.google.com/speed/public-dns/)

---

### Post by TheFu on 2018-09-18
> **oldrocker99 said:**
> Try another DNS. Google's are free:
[https://developers.google.com/speed/public-dns/](https://developers.google.com/speed/public-dns/)

Already using Google's DNS according to the OP.

Might want to try 1.1.1.1 which is a privacy-based DNS sponsored by Cloudflare and APNIC.  Cloudflare are the guys behind many unpopular websites due to their belief in Freedom of Speech. They promise: 
> Privacy First: Guaranteed.
We will never sell your data or use it to target ads. Period.

We will never log your IP address (the way other companies identify you). And we’re not just saying that. We’ve retained KPMG to audit our systems annually to ensure that we're doing what we say.

---

### Post by thomasthefourth on 2018-09-20
> **TheFu said:**
> Already using Google's DNS according to the OP.

Might want to try 1.1.1.1 which is a privacy-based DNS sponsored by Cloudflare and APNIC.  Cloudflare are the guys behind many unpopular websites due to their belief in Freedom of Speech. They promise:

Thanks. I tried it but still no luck. I just decided to bite the bullet and order a wifi adaptor.

---

### Post by TheFu on 2018-09-20
> **thomasthefourth said:**
> Thanks. I tried it but still no luck. I just decided to bite the bullet and order a wifi adaptor.

That's too bad.  wifi is always a poor choice, especially for desktops, but also for laptops and chromebooks as well.  An intel PRO/1000 NIC would have been my recommendation if you think the networking on the motherboard is broken.  $25.  

We didn't even look at the drivers for issues and never heard back about the log files.  There's a bunch of network troubleshooting that could have been done too. Lots of other posts in these forums have network troubleshooting steps.

```
lshw -C network
ifconfig
route -n
ping the router by IP
ping 1.1.1.1
ping google.com
```
All standard techniques.

But DNS is commonly the issue when things in a browser aren't working, but all other networking is.

I only do server-style networking myself, so my desktop networking skills are weak.  I don't know what GUI programs are used. Never touch those myself.

---

