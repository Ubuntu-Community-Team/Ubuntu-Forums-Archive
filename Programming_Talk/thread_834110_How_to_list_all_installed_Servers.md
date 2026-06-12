---
title: "How to list all installed Servers?"
date: 2008-06-19
forum: Programming Talk
---

### Post by shoaibi on 2008-06-19
I am developing this application which will check if any server like |Web server, FTP server, SSH server, IMAP, POP3, etc are installed or not and then show a list of the installed servers. These servers may or may not be running at the time of check. Check should be performed using command line. I know about dpkg -l, and rpm -qa and then using grep, but i want the software to be generic, no matter what backend distro is, it should list all the publicly accessible servers.

What i will do is that show that list to user with check box, user will mark which servers he is interested in and then i will parse that info, and add the information into nagios files for monitoring of those servers.

---

### Post by dtmilano on 2008-06-19
Detect the distro first and then use customized search for each distro (dpkg, rpm, etc.).
How can you find something you don't know how to search for ?
No silver bullets.

---

### Post by Martin Witte on 2008-06-19
> **dtmilano said:**
> Detect the distro first and then use customized search for each distro (dpkg, rpm, etc.).
How can you find something you don't know how to search for ?
No silver bullets.
In case you wonder how to find distro details run command ```
martin@toshibap200:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04
Release:	8.04
Codename:	hardy
martin@toshibap200:~$ 
```

---

### Post by dtmilano on 2008-06-19
And think that could also be non LSB compliant.

---

### Post by shoaibi on 2008-06-21
Okay, i have this problem and i would like someone from you people to help me out.

I am developing a software which would list "publicly available services which are monitorable by nagios" (listed at: [http://nagios.sourceforge.net/docs/3_0/monitoring-publicservices.html](http://nagios.sourceforge.net/docs/3_0/monitoring-publicservices.html)). Problem is:
1. These services may or may not be running on the system at the time of check.
2. How to check?
a. On irc i was suggested using dpkg-l or rpm -a and then grep, but that is distro dependent, is there a generalized way to do this? Or should i do this manually?
i. if you say that i do it via lsb_relase -a, but that will given different output for even Linux, isn it? Does it mean that first i will have to cretae an array of Debian based distros and red hat based ones, then do lsb_release -a, check from which group the distro belongs to, and then use dpkg -l or rpm -qa and search for what??? (what should i be searching for in the installed service list? coz in my experience for apache, dpkg -l shows apache, while rpm -qa will shows httpd, am i right? if yes then what string should i check?)
3. Isnt there a easy and nice way to know using nagios that which services are installed on a system, running or not...??
4. What if i monitor a service thats even not installed?
5. Is it okay to have multiple definitions of the same host with exact same text in nagios? If no, what about if just the IP remains same?

---

### Post by Can+~ on 2008-06-21
SOLVE the problem, THEN you port it. BUT! it doesn't mean that you should hard code everything, make it easy to be ported later (like, using a config file where the commands are allocated like "distro=ubuntu, etc..."). Start it as a home-grown project, later you'll rewrite it with the new knowledge.

---

