---
title: "Remote Desktop Viewer only works with wireless, not with wired connection"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by swarup on 2008-06-24
I am running Ubuntu Hardy, and have been using a wireless dongle for my online connection. With that, the Remote Desktop Viewer is able to properly check (using "Find") for who else is online in my office so I can click on the name of another person's desktop and access their machine as needed. 

But when I switch over to a wired connection to the router instead of my wireless dongle, then when I go into Remote Desktop and click on "Connect", and then on "Find", then it doesn't find anyone else online. When there *are* people online. And if I remove the wired connection and put in the wireless dongle, then it immediately finds the other online computers in the office.

Why is this, and what do I have to do to make the wired connection work with Remote Desktop as the wireless dongle does?

---

### Post by superprash2003 on 2008-06-24
is the wired connection able to ping those pcs with remote desktop enabled?

---

### Post by swarup on 2008-06-24
Good question, one that will probably give very helpful information. I'm not certain how to ping another pc, although I know basically what it means to do so. Could you tell me the procedure? 

I've pinged my router before, but never another pc. It's probably quite similar, right? I'd have to go back and refresh myself on how it was that someone once instructed me to do that.

---

### Post by superprash2003 on 2008-06-24
find out the ip address of  a machine with remote desktop ON .. in windows you can do that by typing ipconfig in the command prompt.. in linux type ifconfig in the terminal.. once you come to know the ip.. go to your pc and type ping x.x.x.x in your terminal... where x.x.x.x is the ip you found out in the beginning

---

### Post by swarup on 2008-06-24
I see-- that worked fine.
I could ping the other computer equally well with the wireless dongle and the wired connection. Here below is the output I get with either one. It goes on infinitely if I let it:

```
desktop:~$ ping 192.168.0.101
PING 192.168.0.101 (192.168.0.101) 56(84) bytes of data.
64 bytes from 192.168.0.101: icmp_seq=1 ttl=64 time=12.3 ms
64 bytes from 192.168.0.101: icmp_seq=2 ttl=64 time=4.66 ms
64 bytes from 192.168.0.101: icmp_seq=3 ttl=64 time=4.96 ms
64 bytes from 192.168.0.101: icmp_seq=4 ttl=64 time=4.83 ms
64 bytes from 192.168.0.101: icmp_seq=5 ttl=64 time=4.89 ms
```

I presume this represents a positive ping. So both wired and wireless can ping the other computer. But only wireless sees the other computer when I do "Find" in vncviewer. The wired connection doesn't see any other computer in "Find" in vncviewer. 

So what does it all mean? And what is the next step?

---

### Post by superprash2003 on 2008-06-25
i hope you did the pinging of wired when wireless was switched off??if so. then in your remote desktop viewer try connecting manually using the ip rather that finding!!

---

### Post by swarup on 2008-06-25
Thank you for the suggestion. :) I tried it and it works perfectly! Don't know why the "Find" feature only works with the wireless. But whatever it may be, now we've got the solution. Thank you! :)

---

