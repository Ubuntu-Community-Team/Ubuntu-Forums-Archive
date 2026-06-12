---
title: "scann host for web services."
date: 2010-06-13
forum: Programming Talk
---

### Post by ja660k on 2010-06-13
Hey all,

The only thing i hate about web services, is that they are IMPOSSIBLE to find (to me anyway)

so im wondering is there a way to scan a host and find its web services(if any)?

---

### Post by hakermania on 2010-06-13
what do you mean "web services"?

---

### Post by soltanis on 2010-06-13
Yeah seriously I don't understand what you mean. If you want to scan a host to see what TCP ports they have open you should look at nmap.

I should warn you, though, that while port scanning per se isn't illegal (in the United States anyway) it's pretty suspicious looking to most admins, so you should not do it to random computers.

---

### Post by ja660k on 2010-06-14
by web services, i mean ...
[http://en.wikipedia.org/wiki/Web_service](http://en.wikipedia.org/wiki/Web_service)

from what i've found it is nearly impossible to scan a host if they have a web service.

---

### Post by lisati on 2010-06-14
Wouldn't it be better to get an idea through "official" sources (e.g. their web site) before trying to access someone's services, rather than trying to be sneaky?

(By the way, a properly set up server is likely to log accesses & whatever attempts to access it come its way)

---

### Post by ja660k on 2010-06-14
Yeah but most places dont really specify, 
im not scanning actual hosts, but if i can find a way...
so far when i put my own service up on my server i cant distinguish it from 
any other open port i have.

---

### Post by Dayofswords on 2010-06-14
> **ja660k said:**
> Yeah but most places dont really specify, 
im not scanning actual hosts, but if i can find a way...
so far when i put my own service up on my server i cant distinguish it from 
any other open port i have.

[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)

---

### Post by ja660k on 2010-06-14
> **Dayofswords said:**
> [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)

... webservices can be on any port. well one not in use and >1024
so its hard to tell what is what.

---

