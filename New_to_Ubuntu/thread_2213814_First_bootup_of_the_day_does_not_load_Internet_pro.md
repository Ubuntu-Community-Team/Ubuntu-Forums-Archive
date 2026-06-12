---
title: "First bootup of the day does not load/ Internet problems"
date: 2014-03-28
forum: New to Ubuntu
---

### Post by amber4 on 2014-03-28
Hi,
I am running Ubuntu 12.04 LTS on an old Dell machine. When I first boot the computer in the morning, it stays on the Ubuntu loading screen indefinitely. However, it boots quickly after I turn it off and on again (go figure! :P) There are no errors displaying when it successfully boots.

Also, the Internet becomes slow only on this particular machine after some time using it. When this happens, neither Chrome nor Firefox will load a webpage and display DNS lookup failures for whatever website I am attempting to visit. I am using OpenDNS to filter web access, and once again, after a reboot, the Internet will load.

---

### Post by GigabyteProduction on 2014-03-28
You might want to look into changes that occur in your network configuration as you use your computer, you can try these command and look for changes:
```
ifconfig (look for ipv4 address disappear entirely or change to something starting with a 169 or something else that doesn't match your actual netowork)
route -n (look for disappearance of the 0.0.0.0 route)
sudo iptables --list-rules (this will be your firewall, parhaps you have some bad software that may start blocking stuff)
ping 192.168.1.1 (check connectivity to router, but make sure this is the router ip address)
ping 8.8.8.8 (check connection with actual outside world, this specific ip address is google's dns)
```
and the last thing i can think of currently, but not the least is check opendns status, if you're using something like dnscrypt, check the program's log, or if you're using just their regular dns service see if you can ping 8.8.8.8 but not opendns's ip address, if that happens, their actual servers might just be down for a sec

The kind of thing that could cause your network to change suddenly and lose connection would most likely be your router, or if you're on wifi, just bad signal, i used a cheap tp+link router that was absolutely horrible... it seemed fine, until my computer (being wired) would change to link-local addresses (the ones starting with 169) but would take an hour to resolve unless i restart my computer (i honestly thought it was just windows, until i figured out it was my router) and another issue i had was my mother's playstation would get disconnected suddenly and for no reason, and for some reason it was even reacting to her bluetooth headset despite being on two different ranges... so yeah, routers can cause big problems if you use a cheap one.

---

### Post by tgalati4 on 2014-03-28
The key words are "old" and "Dell".  Your machine may have bad capacitors.  They are slow to charge which is why it requires a second boot.  Check your motherboard for bulging or leaky capacitors.

---

