---
title: "static ip or dynamic ip"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by hktrout on 2012-05-24
Hi,

Could you please tell me how to find out if I have static ip or dynamic ip from ubuntu os?

Thanks

---

### Post by Tony Flury on 2012-05-24
If it is a network assigned static IP address you may not be able to tell - as it still will be delivered by DHCP. You may need to ask your service provider, and if you need a static address then you may have to pay for it.

If it is a static address set up by you - then check  in /etc/network/interfaces

---

### Post by Enigmapond on 2012-05-24
This has nothing to do with Ubuntu or the OS. It is the method by which an ISP assigns IP addresses to their customers. If you have the same IP every time it's static and if it changes slightly, it's dynamic. Normally on a cable broadband it would be static however on some DSL's it's dynamic. This info you need to get from your ISP (internet Service Provider).

---

### Post by Paqman on 2012-05-24
It's pretty unlikely you have a static IP. Most home connections provided by an ISP will be dynamic.

You can confirm this by checking your IP over several days. Or just phone your ISP and ask.

---

### Post by agillator on 2012-05-24
The easiest way is to check your ip with ifconfig, then sometime after you have rebooted and the machine has been off for some time (15-30 minutes at least, to be safe) check it again. If it is different, you have a dynamic ip address. If it is the same after several times, you have a static ip.

That is if you know nothing about your system. If you are on a LAN, check your network configuration to see how you get an ip address. It may show a static address or it may show it gets its address via dhcp. If dhcp, see if your LAN has a dhcp server and check it to see if your machine is listed for a static address. If you are NOT on a LAN but connect directly through an ISP, check your account with them. If you have (are paying for) a static address then you have one. If not, you don't. 

You can also check the /etc/hosts file. If there is an entry in there showing an address other than 127.x.x.x for your machine name, you probably have a static address. If no entry, you still may have either.

Note that your machine may think it has a static address, but if the address provider thinks otherwise, guess who wins! The only sure way to find out that I know of is the first paragraph or check your bill/account.

---

### Post by Tony Flury on 2012-06-06
> **agillator said:**
> The easiest way is to check your ip with ifconfig, then sometime after you have rebooted and the machine has been off for some time (15-30 minutes at least, to be safe) check it again. If it is different, you have a dynamic ip address. If it is the same after several times, you have a static ip. 
Not neccessarily true - I work for an ISP and we try, where possible to make dynamic addresses sticky if we can - certainly over a short period like 30 minutes or so - i.e. if you log back it is entirely possible you will get the same address as you had, even though it is a dynamic address.

Static = should never change between log-ins
Dynamic = may not be the same between log-ins.

---

### Post by lisati on 2012-06-06
Have a look at the [http://whatismyipaddress.com](http://whatismyipaddress.com) website: they can offer interesting information about your public IP address, and can sometimes help with determining static or dynamic.

---

