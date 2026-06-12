---
title: "updated to geany 1.23 question"
date: 2014-04-08
forum: Programming Talk
---

### Post by jgw on 2014-04-08
I am running w/ubuntu 12.04  I just updated geany to 1.23  the debug tab has now gone away.  I checked synaptic and it tells me that the GeanyGDB plugin is not installed and was for geany .21  I suspect I have missed something here.  Should I then be simply invoking gbd from a terminal?  I also checked the plugins and it told me that the debugger (plain) was installed.  I am, obviously, confused.  (when I updated my thought was to overcome some small problems with v .21 of Geany as a jump from .21 to 1.23 was kinda big.  Now I wonder if I made a mistake by updating)

Thoughts? (thanks)

---

### Post by vasa1 on 2014-04-08
What do you see when you run **apt-cache policy geany-plugin-debugger**?

On my system, Geany 1.23 on 13.10, I see:```
[07:36 AM] ~ $ apt-cache policy geany-plugin-debugger
geany-plugin-debugger:
  Installed: (none)
  Candidate: 1.23+dfsg-3
  Version table:
     1.23+dfsg-3 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
[07:38 AM] ~ $ 

```

---

### Post by jgw on 2014-04-09
Thank you for the reply.  Here are the results:

geany-plugin-debugger:
  Installed: 1.23+dfsg-2~hyper1+precise
  Candidate: 1.23+dfsg-2~hyper1+precise
  Version table:
 *** 1.23+dfsg-2~hyper1+precise 0
        500 [http://ppa.launchpad.net/geany-dev/ppa/ubuntu/](http://ppa.launchpad.net/geany-dev/ppa/ubuntu/) precise/main i386 Packages
        100 /var/lib/dpkg/status
     0.21.1.dfsg-2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages

---

