---
title: "nmap scan help please"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by mentisafer on 2008-08-29
Hi everyone.
I've been using nmap aplication with satisfaction since it always showed filtered ports. Well on wireless networks.
I just moved into the dorms at my campus and I had to plug a DSL high-speed (no wireless available). 
After I scan my ports, I got a wierd output:

sudo nmap -sS -sV -O -p- -PI -PT 127.0.0.1
Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-08-28 20:10 CDT
All 65535 scanned ports on localhost (127.0.0.1) are filtered
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running: Microsoft Windows 2003
OS details: Microsoft Windows Server 2003 SP1
Network Distance: 0 hops

Is this safe? If not, what should I do about it? I'm new to Ubuntu, please advise.
Thank you.

---

### Post by RequinB4 on 2008-08-29
It's fine

> Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port

That means nmap isn't able to tell what your operating system is and for some reason it thinks it's windows.

---

### Post by mentisafer on 2008-08-29
oh thanks!

---

### Post by nicedude on 2008-08-29
Weird when I run it with your same arguments it does not guess I am using Windows which is weird if we are both using hardy 8.04 but anyway it still is just an incorrect guess it is making so I wouldn't worry about it.

Here is my output

nicedude@dellbox:~$ sudo nmap -sS -sV -O -p- -PI -PT 127.0.0.1
[sudo] password for nicedude: 

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-08-29 01:10 EDT
All 65535 scanned ports on localhost (127.0.0.1) are closed
Too many fingerprints match this host to give specific OS details
Network Distance: 0 hops

OS and Service detection performed. Please report any incorrect results at [http://insecure.org/nmap/submit/](http://insecure.org/nmap/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 4.997 seconds
nicedude@dellbox:~$

---

