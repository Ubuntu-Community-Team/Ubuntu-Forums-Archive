---
title: "[SOLVED] Hardy installed - internet working real slow"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by niceguy123 on 2008-06-04
I've "upgraded" from feisty 7.04 to Hardy 8.04 with a new cd and now Firefox and package manager are working real slow or not at all.

---

### Post by cmnorton on 2008-06-04
Are you on a wireless network? If so, have you restarted that? 
(This suggestion is to remove any doubt that your high speed internet connection did something strange right around the same time. I have a shaky DSL connection that gets flaky in wet weather, and I have had this same thing happen to me at the time of an upgrade.)

Can you browse to any site and not have the browsing experience feel sluggish, or is all browsing sluggish. If you have a wireless router, can you connect to that reasonably quickly?

The problem with network speed problems is you probably have one, but most of us do not expect to have to create prior release benchmarks to compare with a current release. 

The only other things I can think of to do is check /etc/resolv.conf. How is that configured? I have seen some network speed-releated posts in these forums, and setting up resolv.conf correctly seemed to fix the problems. I do not remember the posts' urls, unfortunately.

Look for any interesting messages in /var/log/messages, /var/log/kern.log, or /var/log/syslog. You probably won't find anything unusual, but it does not hurt to check.

---

### Post by niceguy123 on 2008-06-05
Thanks for the reply. No, I'm on a wired office network using a joint router dsl conenction. 

The windows xp box that I am writing from now is on the same network. At the same time my two Ubuntu boxes are physicly conected to the same network but the browsers are not browsing the web. Network conection between them works. The internet on this system worked fine before I installed Hardy 8.04. I turned off and on the dsl modem a few times and restarted the computers. ??? :confused:

---

### Post by superprash2003 on 2008-06-05
sometimes slow browsing speeds is because of overloaded DNS servers.. try changing DNS servers to opendns.. [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by niceguy123 on 2008-06-05
> **superprash2003 said:**
> sometimes slow browsing speeds is because of overloaded DNS servers.. try changing DNS servers to opendns.. [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

The problem was in the Network configuration. I fix that and wow internet is working in Hardy too.

---

