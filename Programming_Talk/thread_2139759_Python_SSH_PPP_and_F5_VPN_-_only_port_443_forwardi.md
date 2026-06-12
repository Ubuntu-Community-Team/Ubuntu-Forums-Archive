---
title: "Python SSH PPP and F5 VPN - only port 443 forwarding"
date: 2013-04-27
forum: Programming Talk
---

### Post by john_navarro on 2013-04-27
I use the F5 SSL VPN to access work. I typically use Firefox to launch it as a plugin. This works but I'm looking for a CLI solution because the vendor doesn't support current versions of Firefox. I found this Python script and it sort of works:

[http://dnscoder.blogspot.com/2012/10/connect-to-vpn-on-linux.html]("http://dnscoder.blogspot.com/2012/10/connect-to-vpn-on-linux.html")

The problem is that it seems only traffic on port 443 is passed over the VPN. All the routes a defined correctly. HTTPS using a browser works great. But TELNET, SSH, PING all just sit there and do nothing. Even SSH'ing to a server where HTTPS works results in nothing. So I'm trying to figure out what might be the problem. This solution can help others if it can get fixed. I'm hoping someone might have some idea of things to check out. I don't have any firewall enabled. Nor are there multiple VPN's running. I don't know Python but I don't think it's a coding issue. My thinking is that it's a SSH or PPP config settings. I'm all for a better/different solution if there is one.

Things I've tried:
1) Tried under Ubuntu 12.04 64bit - shows same problem
2) Tried under Ubuntu 13.04 32 & 64bit - both exhibit the same problem

Thanks,
John

---

### Post by Bodsda on 2013-04-28
> **john_navarro said:**
> I use the F5 SSL VPN to access work. I typically use Firefox to launch it as a plugin. This works but I'm looking for a CLI solution because the vendor doesn't support current versions of Firefox. I found this Python script and it sort of works:

[http://dnscoder.blogspot.com/2012/10/connect-to-vpn-on-linux.html](http://dnscoder.blogspot.com/2012/10/connect-to-vpn-on-linux.html)

The problem is that it seems only traffic on port 443 is passed over the VPN. All the routes a defined correctly. HTTPS using a browser works great. But TELNET, SSH, PING all just sit there and do nothing. Even SSH'ing to a server where HTTPS works results in nothing. So I'm trying to figure out what might be the problem. This solution can help others if it can get fixed. I'm hoping someone might have some idea of things to check out. I don't have any firewall enabled. Nor are there multiple VPN's running. I don't know Python but I don't think it's a coding issue. My thinking is that it's a SSH or PPP config settings. I'm all for a better/different solution if there is one.

Things I've tried:
1) Tried under Ubuntu 12.04 64bit - shows same problem
2) Tried under Ubuntu 13.04 32 & 64bit - both exhibit the same problem

Thanks,
John

We'd need a lot more info, such as how the VPN is configured, what type of traffic it accepts, what you normally use it for. It would also be useful to see your routing table

Having said that, there is a function in the script called 'send_request' that hard codes port 443, but I don't know enough about F5 VPN to say if this is the issue (And I'm not gonna read all 1200 odd lines to see whats actually happening) although if this VPN just delivers web based content or interacts solely via a browser then I would say that everything is working as expected.

Bodsda

---

### Post by prodigy_ on 2013-04-28
If I were your I'd email the script author first and ask him for help. Even if he's no longer interested in developing/fixing his code, he might know what's going on.

If that fails, try contacting your VNP provider support. Maybe they have a working solution.

---

