---
title: "pptp connection doesn't appear in network manager"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by joey_breizh on 2008-08-28
Hi!

I'm desperately trying to connect to my school's VPN from Ubuntu and running into some issues... There is probably something ridiculous that I'm missing seeing as I've read setting up a PPTP VPN connection through network manager is super simple. 

I've installed the VPN connection manager that supports pptp via add/remove. When I click on the Network Manager applet I have VPN Connections/configure VPN. I go there and say I'd like to connect via PPTP tunnel, then fill out the basic fields - Connection Name, Type, Gateway, then Apply and Exit. But if I go back to the applet, the connection I just set up doesn't appear so it's impossible for me to get connected to it.

I should add that earlier by mistake I installed a VPNC (Cisco compatible) connection and it appeared fine in the menu. So how come the pptp ones don't?

(I am, in case it's not painfully obvious, a complete newbie to Ubuntu and Linux in general.)

---

### Post by joey_breizh on 2008-08-29
Now I've installed OpenVPN via add/remove, my pptp connection appears in the list, but when I click on it to connect and then enter username and password, nothing seems to happen... (and I'm definitely not logged in if I check the website for my university's library) What am I missing here?

---

### Post by daemonk on 2008-08-29
Hi,

I am having the same problem. If you do find a solution please post it here. I will do the same ;)

Thanks

---

### Post by whitethorn on 2008-08-29
I recently set up a pptp connection in hardy,  in my situation it showed up in the configure menu, it also didn't show up right above the configure option.  I needed to restart my computer and it showed up.  You could also try

```
sudo NetworkManager restart
```

in the terminal, didn't work for me though.

---

### Post by joey_breizh on 2008-08-29
I think my connection issue yesterday might have come from my wireless being wonky (am having trouble with that right now). Right now I am connected to a wired network, my VPN connection appears in the list (after I installed OpenVPN support and restarted the computer) and it works perfectly.

---

