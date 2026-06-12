---
title: "how hard would it be to make a proxy server..."
date: 2009-01-10
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-01-10
people use them at work and school to play games...seems like a decent thing to get views since they are constantly being blocked...how hard would it be to make one and what would i need to know

---

### Post by pmasiar on 2009-01-10
If your school/work does not want you to use some website, it is foolish to try to work around it.

I know one quite smart Linux hacker student, who was banned in his High School to use any computer at all, after setting his home server to work around HS IT. Those folks were completely sure that he knows more about network security than them, and if they let him use any school PCs, he will find another way.

His home PC is quite interesting, running Slackware with 3 monitors, each one different.

But banning him from using PCs did not prevented him from being accepted to CMU :-) - he was way too cool to go to MIT like other geeks want to.

---

### Post by myrtle1908 on 2009-01-10
Proxies (at their most basic level) are very trivial.  There are countless examples of basic HTTP proxies floating around the net in many languages.  A *very* simple Perl example can be found here [http://www.adp-gmbh.ch/perl/proxy.html](http://www.adp-gmbh.ch/perl/proxy.html)

---

### Post by hundredwatt on 2009-01-10
> **jimi_hendrix said:**
> people use them at work and school to play games...seems like a decent thing to get views since they are constantly being blocked...how hard would it be to make one and what would i need to know

If you just want to get around a firewall,  install openSSH on a computer at your house and then you can use it as a secure proxy. See [http://souptonuts.sourceforge.net/sshtips.htm](http://souptonuts.sourceforge.net/sshtips.htm)

---

### Post by jimi_hendrix on 2009-01-10
hehe i dont want to get around it...im fine not playing games until i get home...i just want to capitalize on others' BOREDOM!

an example in php would be nice

---

### Post by kavon89 on 2009-01-10
Its actually really easy, I set up my home server with a proxy. Too bad my upload bandwidth is crap, but I'm moving up to FiOS soon.

Install squid and edit the detailed config file to prompt a password for any outside requests, but allow all for 192.168.1.0/24 (local network).

---

