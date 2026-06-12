---
title: "help with the reconfiguring of apache2"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by maskiepop on 2011-09-11
Hi. I installed apache2, mysql, php5 on my ubuntu 10.04 desktop. I configured a virtualhost such that I can type [http://mydom.com/](http://mydom.com/) and see apache2 present my web pages from ~/bublic_html/folder.

I no longer want to do that on a regular basis, because I now have mydom.com as a real website. I disabled ( via a2dissite mydom.com ) the mydom.com from my desktop; I stopped apache2, (and the rest) from starting up when I login. And yet, every time I invoke [http://127.0.0.1/](http://127.0.0.1/) i get a message saying firefox is unable to connect. Nor can I connect to my real website, with [http://mydom.com](http://mydom.com).

What do I need to do to get my desktop back to the same point before I installed apache2, without necessarily un-installing it (and the rest) again. I still plan to do some work on it. Ideally I'd like to re-configure everything so that now, I can access my desktop website as [http://localhost/mydom.com](http://localhost/mydom.com).

Thanks.

---

### Post by cj13579 on 2011-09-12
You said about disabling your old site but you didn't mention anything about creating a new site and enabling it "sudo a2ensite blah".

Also take a look at [this]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html") for some more apache config stuff.

---

### Post by maskiepop on 2011-09-12
Hi. Thanks for your reply.
I suppose I am operating on the assumption that if I don't start up apache, my desktop would behave the way it did before I installed apache. But it doesn't, so obviously I am wrong.

I am now thinking of abandoning my line of thinking, and reconfigure the apache setup of mydom.com as a subdomain of localhost. That means my dev domain does not interfere with the real life mydom.com.

What I can't undersstand is how the [http://127.0.0.1](http://127.0.0.1) gets a "cannot connect" message from Apache.

---

### Post by Wim Sturkenboom on 2011-09-12
> **maskiepop said:**
> 
What I can't undersstand is how the [http://127.0.0.1](http://127.0.0.1) gets a "cannot connect" message from Apache.
That's not an apache message, that's a browser message (which makes sense).

---

### Post by cj13579 on 2011-09-12
What have you bound the new site to? Is it just you IP:80 or something like *:80?

---

