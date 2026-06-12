---
title: "Can't Get Rid of Epson"
date: 2016-05-14
forum: New to Ubuntu
---

### Post by Mike_Andrews on 2016-05-14
After failing to install an Epson WP 4530 inkjet printer, I resorted to some risky behavior in signing on with launchpad, which may have compromised my system.
The printer still doesn't work, so I deleted it from Printers.
But following two wipes and reinstalls of Ubuntu 16.04 in the past 48 hours, Epson's network still has a base camp in my computer and there is no way to delete it, as all I get are error messages advising that such actions are not permitted by 'backend.' Whatever that is.
Trying to use terminal with rm has failed as well, although it's very possible the code wasn't set up correctly; nonetheless the only terminal output is 'no such file or directory.'
At any rate, I want to completely rid my system of Epson's/launchpad's tentacles, since it's not doing me any good to affiliate with these entities.
The failed printer setup has been deleted from Printers, but that has no effect on Epson's connection with my computer.
. . . Even after several wipes of the HD!
What've I got here. . . a firmware implant?
Any advice would be welcome; just don't tell me I have to reinstall the system again.
That doesn't work.
Clam is useless.

---

### Post by Bucky Ball on 2016-05-14
Is the printer still plugged into/on the same network as the router/access point and turned on? If you were trying to connect to it wirelessly and if you were successful, it might even be in another room and turned on and still showing up. Just a punt.

I'd be real cautious with them 'rm' commands. :|

---

### Post by cariboo on 2016-05-14
You don't say how you are connected to the printer, I see it has both wifi and ethernet connections. I'd suggest you unplug the printer power cord, and see if it still shows up on your home network.

I have a Brother networked laser when I ran nmap against  it I get the following result:

```

Starting Nmap 7.01 ( https://nmap.org ) at 2016-05-14 20:35 PDT
Nmap scan report for 192.168.0.100
Host is up (0.017s latency).
Not shown: 993 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
23/tcp   open  telnet
80/tcp   open  http
139/tcp  open  netbios-ssn
515/tcp  open  printer
631/tcp  open  ipp
9100/tcp open  jetdirect

Nmap done: 1 IP address (1 host up) scanned in 0.40 seconds
```

You should see something similar, if the printer is powered up.

---

