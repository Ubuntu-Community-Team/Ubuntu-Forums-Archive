---
title: "Server Domain Help"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Mentch on 2008-05-25
Ok so I have a server setup running apache2 and everthing works fine. It can be accessed here: [http://66.166.89.106/](http://66.166.89.106/)

My question is what do I need to do to get a domain name pointed to it. I tried going into my godaddy account and just changing the name servers to that IP but godaddy doesn't like the IP I put in.

Do I need to run bind and set that up for a DNS or what? Im confused.

---

### Post by scxtt on 2008-05-25
dyndns.org will let you pick from a predetermined list of DNS names that you can point to that IP ... rolling your own DNS/bind setup won't help anyone who doesn't use you as a DNS server ...

---

### Post by superprash2003 on 2008-05-25
you could choose a free domain like myname.dyndns.org or you could purchase a domain like myname.com it depends on what you want

---

### Post by Mentch on 2008-05-26
Ok I got it all working, I installed webmin and configured bind9 and then went into my godaddy account and set everything in their to point to the Nameservers of my server and IP.

Now to see about getting the mail server to work with multiple domain names.

---

