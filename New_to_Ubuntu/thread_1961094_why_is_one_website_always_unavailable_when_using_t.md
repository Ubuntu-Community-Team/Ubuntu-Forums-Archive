---
title: "why is one website always unavailable when using this computer?"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by hanzj on 2012-04-18
Hello
Whenever I go to a particular website, Google Chrome always says, "Oops! Google Chrome could not find www.website.net". I am Sure that the website is up. I put the URL in google translate and it appears. Can someone help me diagnose this?


UPDATE: I went to [http://www.hcidata.info/host2ip.cgi](http://www.hcidata.info/host2ip.cgi) to convert the website address to IP address.  I get: 
> This domain is registered and protected
by MarkMonitor

More than half the Fortune 100 trust MarkMonitor
to protect their brands online.


---

### Post by Daveth on 2012-04-18
comes up in Opera!

---

### Post by Dragonbite on 2012-04-18
If you open up a terminal and try ```
ping website.net
```do you get connected?  That should also provide the IP address for the site as well.

Also, does it work in other browsers? Do you have any blocking software on your system?  How are you connecting to the internet?

---

### Post by hanzj on 2012-04-18
daveth, the website address is not  website.net. It's some other website URL that ends in .net.

---

### Post by hanzj on 2012-04-18
Dragonbite,
thanks for your post.

ping notworkingwebsite.net> 
PING notworkingwebsite.net (64.124.14.63) 56(84) bytes of data.
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=1 ttl=107 time=210 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=2 ttl=107 time=188 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=3 ttl=107 time=128 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=4 ttl=107 time=136 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=5 ttl=107 time=135 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=6 ttl=107 time=143 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=7 ttl=107 time=132 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=8 ttl=107 time=151 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=9 ttl=107 time=150 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=10 ttl=107 time=129 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=11 ttl=107 time=137 ms
^C
--- notworkingwebsite.net ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 10012ms
rtt min/avg/max/mdev = 128.253/149.364/210.489/25.215 ms

It doesn't work on Firefox.
On opera, foo.net goes to publisher.typepad.com/foo. When I click one of the blog entries, it goes back to foo.net/2012/04/some-title.html. Opera then says "Network problem".

Connected to internet without any firewalls. We use OpenDNS.

---

### Post by Dragonbite on 2012-04-18
> **hanzj said:**
> Dragonbite,
thanks for your post.

ping notworkingwebsite.net
PING notworkingwebsite.net (64.124.14.63) 56(84) bytes of data.
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=1 ttl=107 time=210 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=2 ttl=107 time=188 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=3 ttl=107 time=128 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=4 ttl=107 time=136 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=5 ttl=107 time=135 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=6 ttl=107 time=143 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=7 ttl=107 time=132 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=8 ttl=107 time=151 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=9 ttl=107 time=150 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=10 ttl=107 time=129 ms
64 bytes from forward.markmonitor.com (64.124.14.63): icmp_req=11 ttl=107 time=137 ms
^C
--- notworkingwebsite.net ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 10012ms
rtt min/avg/max/mdev = 128.253/149.364/210.489/25.215 ms

Ok, so Ping can reach it, but not your browser cannot.  What if you put that IP address ([http://64.124.14.63](http://64.124.14.63)) into the browser's URL?

My Fedora 16 and openSUSE 12.1 installations use IPv6 automatically and I could ping it, but not use the browser because my router (or something) could not handle IPv6 in its current configuration.  Once I turned off/ blacklisted IPv6 it worked for me.

Try ```
ping6 notworkingwebsite.net
```because "ping" is using IPv4 (the older technology) while "ping6" uses the newer IPv6, which may not work, or may not work with your browser.

Ubuntu, though, always seemed to work for me so I don't suspect this to be the case here.

---

### Post by hanzj on 2012-04-18
dragonbite,

1. isn't "forward.markmonitor.com" in the ping a sign that things are not working?
2. [http://64.124.14.63/](http://64.124.14.63/) goes to [http://64.124.14.82/](http://64.124.14.82/) which says "This domain is registered and protected
by MarkMonitor

More than half the Fortune 100 trust MarkMonitor
to protect their brands online."
 
3. ping6 samewebsite.net gives "unknown host"

---

### Post by Dragonbite on 2012-04-18
Ok, so we know it isn't an IPv4 vs IPv6 issue.

I guess one question that comes to mind is whether it is actually working properly or not.  If markmonitor isn't actually in control and forwarding the site to their generic page.

The only way to do that is to have somebody get something different.  

Is this a suitable for work type site?  I'm at work and don't know what the site is like but I would rather not take the chance if you don't mind.. ;)

---

### Post by hanzj on 2012-04-18
dragonbite, it's definitely safe for work, home, anywhere. I can pM you the address.
when i use a computer in the public library, the site loads without any problem.

---

### Post by Dragonbite on 2012-04-18
Unfortunately I am not a network guru (I barely make heads-or-tails about it as is).  What comes to mind is [LIST]
[*]your DNS is pointing to the wrong place
[*]your router is pointing to the wrong location
[*]content filtering or some blocking software is "protecting" you?
[/LIST]I just am not familiar enough with beyond the box to know where it could be or how to determine what it is.  Sorry.

Maybe PM me the address and I can check it on some of my machines at home.  Maybe something will stand out?  I just don't know.

---

### Post by ajgreeny on 2012-04-18
I can reach that website here with Firefox 11, and on this old laptop using Lubuntu11.04.

See screenshot.

Is that the page you expected to see?

---

### Post by Dragonbite on 2012-04-18
Hmm.. it comes up for me [LIST]
[*]Windows XP Chrome normal mode
[*]Windows XP Chrome incogneto mode
[*]Windows XP Firefox Privacy browsing
[*]Windows XP IE 8
[/LIST]
Although my Firefox did ask me to install a plugin, though I don't know which plug in is necessary.  I have removed Java from the system, and as far as I know Chrome is the only browser able to run Flash.

My browsers are also set to NOT accept 3rd party cookies and Flash (in Chrome at least) is told not to store data on my system either.

Anybody else out there have any ideas?

---

### Post by hanzj on 2012-04-18
ajgrenny,
no, the "markmonitor" page is not what we should expect. It's a blog.

---

### Post by Dragonbite on 2012-04-18
> **ajgreeny said:**
> I can reach that website here with Firefox 11, and on this old laptop using Lubuntu11.04.

See screenshot.

Is that the page you expected to see?

I get that when I try by IP address, but when I use the URL PM'ed to me it came up (assuming) fine.  

The site is a blog site with the first post including a picture of a book and titled "Wednesday's Giveaway...".

---

