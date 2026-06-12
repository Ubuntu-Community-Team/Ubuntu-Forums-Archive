---
title: "am i under attack?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-04
while cheking my logs i came across this:
```
Sun May  4 03:17:30 2008; TCP; eth0; 44 bytes; from 192.168.1.2:58421 to a212-251-32-167.deploy.akamaitechnologies.co:www; first packet (SYN)
Sun May  4 03:17:30 2008; TCP; eth0; 44 bytes; from 192.168.1.2:58422 to a212-251-32-167.deploy.akamaitechnologies.co:www; first packet (SYN)
Sun May  4 03:17:30 2008; TCP; eth0; 44 bytes; from 192.168.1.2:58423 to a212-251-32-167.deploy.akamaitechnologies.co:www; first packet (SYN)
Sun May  4 03:17:30 2008; TCP; eth0; 44 bytes; from 192.168.1.2:58424 to a212-251-32-167.deploy.akamaitechnologies.co:www; first packet (SYN)
Sun May  4 03:17:30 2008; TCP; eth0; 44 bytes; from 192.168.1.2:58425 to a212-251-32-167.deploy.akamaitechnologies.co:www; first packet (SYN)
Sun May  4 03:17:30 2008; TCP; eth0; 44 bytes; from 192.168.1.2:58426 to a212-251-32-167.deploy.akamaitechnologies.co:www; first packet (SYN)
Sun May  4 03:17:30 2008; TCP; eth0; 44 bytes; from 192.168.1.2:58427 to a212-251-32-167.deploy.akamaitechnologies.co:www; first packet (SYN)
Sun May  4 03:17:30 2008; TCP; eth0; 44 bytes; from 192.168.1.2:58428 to a212-251-32-167.deploy.akamaitechnologies.co:www; first packet (SYN)
Sun May  4 03:17:30 2008; TCP; eth0; 46 bytes; from a212-251-32-167.deploy.akamaitechnologies.co:www to 192.168.1.2:58419; first packet (SYN)
Sun May  4 03:17:30 2008; TCP; eth0; 46 bytes; from a212-251-32-167.deploy.akamaitechnologies.co:www to 192.168.1.2:58421; first packet (SYN)
Sun May  4 03:17:30 2008; TCP; eth0; 46 bytes; from a212-251-32-167.deploy.akamaitechnologies.co:www to 192.168.1.2:58422; first packet (SYN)
Sun May  4 03:17:30 2008; TCP; eth0; 46 bytes; from a212-251-32-167.deploy.akamaitechnologies.co:www to 192.168.1.2:58423; first packet (SYN)
Sun May  4 03:17:30 2008; TCP; eth0; 46 bytes; from a212-251-32-167.deploy.akamaitechnologies.co:www to 192.168.1.2:58424; first packet (SYN)
Sun May  4 03:17:30 2008; TCP; eth0; 46 bytes; from a212-251-32-167.deploy.akamaitechnologies.co:www to 192.168.1.2:58425; first packet (SYN)
Sun May  4 03:17:30 2008; TCP; eth0; 46 bytes; from a212-251-32-167.deploy.akamaitechnologies.co:www to 192.168.1.2:58426; first packet (SYN)
Sun May  4 03:17:30 2008; TCP; eth0; 46 bytes; from a212-251-32-167.deploy.akamaitechnologies.co:www to 192.168.1.2:58427; first packet (SYN)
Sun May  4 03:17:30 2008; TCP; eth0; 46 bytes; from a212-251-32-167.deploy.akamaitechnologies.co:www to 192.168.1.2:58428; first packet (SYN)
```

and it continues until now....
i think im a target...it literally checks all my ports
what is this?

---

### Post by kidders on 2008-05-05
> **lunaluna said:**
> am i under attack?No. Those log entries seem pretty innocuous.

---

### Post by lunaluna on 2008-05-05
> **kidders said:**
> No. Those log entries seem pretty innocuous.

ofcoarse i might not be an expert but it seems to me that it was going from one port to the other...so could you explain me what is it?

---

### Post by cwgatling on 2008-05-05
I may be wrong, but this looks like simple interaction between your computer and a website.

```
TCP; eth0; 44 bytes; from 192.168.1.2:58421 to a212-251-32-167.deploy.akamaitechnologies.co:www; first packet (SYN)
```

That entry appears to be your computer (local IP 192.168.1.2) accessing a server on port 80 (deploy.akamaitechnologies.co:_www_) with the TCP source (client) port of 58421. This is completely normal.
In a few lines, you see the reply from the webserver to your computer on that same port.
I remember hearing talk of randomization of TCP source ports, but I think it's pretty normal that they increase by 1 each time.

---

### Post by Xiong Chiamiov on 2008-05-05
Isn't akamai an adserver?
[googles]
Yep.

They're not necessarily the nicest people, but I doubt that they're trying to attack you.

---

### Post by tamoneya on 2008-05-05
Xiong Chiamiov is right.  Akamai is an adservice and while we may not like having ads it is not someone who would be hacking.  This would cause a lot of problems for the company if something like that happened.  I also checked to make sure akamaitechnologies is owned by akamai and it is:
[http://whois.domaintools.com/akamaitechnologies.com](http://whois.domaintools.com/akamaitechnologies.com)

---

### Post by lunaluna on 2008-05-08
but the log is too long of their "scanning" just to ingnore 
it's my first time seeing something like this...

---

### Post by skymera on 2008-05-08
If you look at the timings, it's all within 1 second.

Doesn't seem anything to worry about if you ask me.

---

### Post by kidders on 2008-05-08
> **lunaluna said:**
> but the log is too long of their "scanning" just to ingnore 
it's my first time seeing something like this...

Nobody's "scanning" you. The log entries you posted suggest a rapid series of _outgoing_ HTTP requests that the remote server then responds to ... probably the result of visiting a site in your web browser, or perhaps one of your applications phoning home to check for updates. These two lines, for instance, go together...```
...
...

Sun May  4 03:17:30 2008; TCP; eth0; 44 bytes; from 192.168.1.2:**58422** to a212-251-32-167.deploy.akamaitechnologies.co:www; first packet (SYN)

...
...

Sun May  4 03:17:30 2008; TCP; eth0; 46 bytes; from a212-251-32-167.deploy.akamaitechnologies.co:www to 192.168.1.2:**58422**; first packet (SYN)

...
...
```

Technically, the use of sequential TCP port numbers on your side of the connection does present a theoretical security issue ... but that's a topic for another day, and isn't something you need be particularly concerned about. If it would make you feel better, you could identify & remove the application responsible for the traffic, or block access to akamai with a firewall, but I wouldn't do either, personally. Imo, you should do whatever makes you feel happier about who your computer is talking to.

I hope that helps.

---

### Post by nowshining on 2008-05-08
akamai tech. also hosts images for some sites, ex. pizzahut.com

also microsoft uses them for updates,

the yahoo slurp bot uses akamai for spidering the web.

As other said tho that those are innocent, try if u can disabling those kind of entries to keep the log clean.

---

### Post by lunaluna on 2008-05-09
> **nowshining said:**
> akamai tech. also hosts images for some sites, ex. pizzahut.com

also microsoft uses them for updates,

the yahoo slurp bot uses akamai for spidering the web.

As other said tho that those are innocent, try if u can disabling those kind of entries to keep the log clean.

well i'm a bit paranoid after all
:KS

---

