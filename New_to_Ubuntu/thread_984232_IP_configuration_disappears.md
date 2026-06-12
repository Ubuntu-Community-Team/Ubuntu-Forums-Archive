---
title: "IP configuration disappears"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Bisuletz on 2008-11-16
Hello,

I'm using my ubuntu 8.10 desktop pc to share a PPPOE internet connection with a laptop in my house. I have an one ethernet card for PPPOE (eth0) and one ethernet card for my lan (eth1). 

I setup firestarter to do the internet connection sharing(routing).

When  I setup eth1 with ip 192.168.0.1 but every time I reboot the pc it resets itself to atomatic ip (dns). I set it up by right clicking the network connection in the upper right corner of the screen next to the clock. How come it doesn't remember the settings? Is it meant to do that? :)


Thanks

---

### Post by cmnorton on 2008-11-16
This sounds like you are changing this address, but the change is not taking. You may be setting to this address, but does that address become your current address? Only ifconfig will know for sure, before you reboot.

Are you properly saving this new configuration, and how are you changing your ip address?

Why do you want a static address, if you're a client? Asking you this does not answer your question, but dynamic address are a useful thing, unless you're Linux box is serving clients.

---

### Post by Bisuletz on 2008-11-18
I wanted a static ip address because my machine acts as a server.

I used the default network manager to assign the ip but at the time it didn't save the config. 

It seems the problem solved itself. I don't know how but it's ok now.

Thanks for taking the time to reply.

---

### Post by cmnorton on 2008-11-18
Using NetworkManager back in 6.10, it would tend to drop out when static addresses were used. I don't know how it works now with static, because I'm on DHCP.

---

### Post by drakeman007 on 2008-11-18
> **Bisuletz said:**
> I wanted a static ip address because my machine acts as a server.

I used the default network manager to assign the ip but at the time it didn't save the config. 

It seems the problem solved itself. I don't know how but it's ok now.

Thanks for taking the time to reply.

You know how to configure your interfaces file? there  you can set your static ip address!...

---

### Post by superprash2003 on 2008-11-18
true.. i guess its a bug.. i too face that issue with static ip..

---

### Post by drakeman007 on 2008-11-18
> **superprash2003 said:**
> true.. i guess its a bug.. i too face that issue with static ip..

Well i solved my problem removing the network manager, and editing the interfaces file with the ip configuration!

---

### Post by jamb on 2008-11-18
Maybe you do not need to remove NetworkManager if you use static IP, I had a similar problem which can be work around by adding the name server address in /etc/resolv.conf

[http://ubuntuforums.org/showthread.php?p=6189706#post6189706](http://ubuntuforums.org/showthread.php?p=6189706#post6189706)

---

