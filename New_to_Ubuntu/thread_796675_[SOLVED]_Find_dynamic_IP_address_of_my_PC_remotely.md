---
title: "[SOLVED] Find dynamic IP address of my PC remotely"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by newbuntuxx on 2008-05-16
hey..

i just installed open-ssh on my ubuntu. I then installed putty and xming on my windows machine, and I was able to connect to my ubuntu and even forward X server to my windows machine. It all worked magically.

I have cable internet, which means my Ip address will change regularly. So, If I traveled to a different city and wanted to connect to my ubuntu at home, I will need to know the IP address of my home pc.

How can I achieve that? Is there a shell script that I can use to have my pc send my ip address to my email? I am using: [www.dyndns.com](www.dyndns.com), which simply assigns a host name to your ip address, but does not keep track of your IP when it changes.

any help is appreciated!

---

### Post by newbuntuxx on 2008-05-16
bump

---

### Post by bubba_169 on 2008-05-16
If you contact your ISP it might be possible to get a static IP address which would make things much easier? Just a thought...

---

### Post by HotShotDJ on 2008-05-16
> **bubba_169 said:**
> If you contact your ISP it might be possible to get a static IP address which would make things much easier? Just a thought...Or you can use a DDNS service such as [DynDNS]("http://www.dyndns.com"), which is a free service.  Static IP's from your ISP tend to be expensive.

EDIT:   OOPS.  I guess I didn't read the OP as completely as I thought.  Obviously, my comment here is irrelevant.  My apologies.  I'll get back to my beer now. :)

---

### Post by Golem XIV on 2008-05-16
I think you need to run an update client that will tell the server if your IP changes.

[http://www.dyndns.com/support/clients/](http://www.dyndns.com/support/clients/) has a list of clients that you can use with the DynDNS service.

---

### Post by Monicker on 2008-05-16
> **newbuntuxx said:**
> 
How can I achieve that? Is there a she
ll script that I can use to have my pc send my ip address to my email? I am using: [www.dyndns.com](www.dyndns.com), which simply assigns a host name to your ip address, but does not keep track of your IP when it changes.

any help is appreciated!

???

Did you try any the dyndns clients?

[http://www.dyndns.com/support/clients/unix.html]("http://www.dyndns.com/support/clients/unix.html")

ddclient has worked well for me in the past.

---

### Post by HotShotDJ on 2008-05-16
> **Golem XIV said:**
> I think you need to run an update client that will tell the server if your IP changes.Well, yes.  And some routers (my US$50 wireless router, for example) supports DynDNS also (meaning no configuring software... it works automagically!).

---

### Post by lazyart on 2008-05-16
Yeah, just install a client to update dydns regularly.  Getting a static IP from your ISP is too expensive.

---

### Post by PinkFloyd102489 on 2008-05-16
If you have a Linksys (and some other types) router, DynDNS is support in the router's firmware and will update for you.

---

### Post by dublued on 2008-05-16
i use [www.no-ip.com](www.no-ip.com)
they have a linux client, though i haven't tried that yet

---

### Post by nhandler on 2008-05-16
> **dublued said:**
> i use [www.no-ip.com](www.no-ip.com)
they have a linux client, though i haven't tried that yet

I also use no-ip. The linux client, 'noip2', is in the ubuntu repos. After a simple initial configuration, it will run silently in the background. It will update your host to point to your current ip address after a set interval of time.

---

### Post by newbuntuxx on 2008-05-16
thank you very much guys...I have a link sys router, so, i'll just use the default DDNS. I didn't even know it had that! 

I will still try to install one of the update clients, probably the one available in the respos. Just to get the feel of it.

Thanks again.

---

