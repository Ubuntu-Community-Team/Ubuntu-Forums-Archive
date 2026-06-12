---
title: "Ubuntu 12.04 LTS DHCP only working from router not modem"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by gakubex on 2013-03-12
Alright, because I didn't even know where to begin in the Googlin' department I decided to create a post about it.

I am not new to Linux and I think I have a fair understanding on the UNIX system.

I have created 2 new servers today all running 12.04 LTS, all with the very same hardware.  All using the same DVD to install the software.

The first servers worked "like a boss", i pugged the network cable into the ethernet port and the other in into a DUMB switch.  The switch is pugged into the router and I was able to pull DHCP stuff from the modem, then I proceeded to make them static.  Which all worked fine.  All up and running.

But now here comes the purpose of this question... On server number 2 I did the very same stuff as I did on the other server, however, I was unable to pull the DHCP settings from the Modem and here is the my troubleshooting:
[LIST=1]
[*]So i unplugged one of my other servers that I was working and pugged it in to that port on the switch (checking if the port was bad)... didn't work
[*]Used the other server's network cable (checking if the cable was bad)... didn't work
[*]Went back to my original cable and pugged it into a router and I successfully pulled the DHCP settings
[/LIST]

So, why cannot I not pulled the DHCP settings from the Modem but I was to pull them from a router.  Could my disk have gotten damaged from one disk try to the other one?

---

### Post by sully101 on 2013-03-16
Are the hostnames different?

---

