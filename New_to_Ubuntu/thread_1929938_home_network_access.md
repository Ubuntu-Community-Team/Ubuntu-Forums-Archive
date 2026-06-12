---
title: "home network access"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by tompoe on 2012-02-22
I'm sitting with a mess and hoping for experts to help.

I have ubuntu 11.10 on one older computer  (192.168.1.66).  
I have ubuntu 11.04 live DVD on one older, older computer (192.168.1.64).

I can ping the .64 computer from my .66 computer, but cannot access with ssh, until I fill in the network info on my .66 computer.

I tried to find the network info on my .64 computer to guide me as to what to fill out on .66, but don't find it anywhere as yet.

My network is a DSL -> switch -> 192.168.1.64 (straight pass-through from ISP.  Not sure what the device addresses are at this point for DSL and for switch.

Can anyone point me to how to step through settings for:
DSL modem
switch
.64 computer
and then set up .66 computer
Thanks,
Tom

---

### Post by deonis on 2012-02-22
Do you have ssh server installed on your destination computer? If you can ping the server I see no problem for ssh connection. First check if server is installed, second check if firewall has the port 22 opened.

cheers

---

