---
title: "A smart way to identify a pc opened a site"
date: 2012-12-10
forum: Programming Talk
---

### Post by cherva on 2012-12-10
This is the problem I made my own DNS server with messed zones ( for example facebook.com goes to my server and a few more sites ) and there I display a message like "You can not browse this site while you are on work." The problem is that the DNS server is in a data center and I need a way to identify the user who requested the page... I found a way with java to get the local ip address and then to send it with jquery, but some pcs may not have java installed. Is there another way to get somekind of info about the pc so I can generate a statistic of "who opened what" javascript can't access the pc name :confused::confused: give me ideas :)

---

### Post by Tony Flury on 2012-12-10
All incoming packets to your server will have the source IP address in them - it is part of the IP protocol.

Your serve logs should contain the source address, and I vaguely remember that the source address may be available as a CGI variable which you could extract.

also bear in mind that any worker can easily work-around your poisoned DNS just by using IP addresses rather than the DNS name in their browsers.

BTW - all the research carried out suggests that allowing access to email and social media from work by employees will improve their efficiency and work rates - it allows them time to take short breaks from the daily routine, and also shows that you trust them. That sense of trust is repaid in terms of a better work ethic for you as an employer.

---

### Post by cherva on 2012-12-10
It is not my call to prohibit some sites :)
I know that I can see the ip address of the client, but in this case I will see only the public ip of the office the person is in, not his private ip (192.168.xxx.xxx) :) I need a way to somehow id the machine.

Maybe like this:

```
<FORM method=post action="/register/user-login" name="login">
<script language="javascript" src="c:\machine\machine-name.js"></script>

The file c:\machine\machine-name.js on the client PC just contains the following line:
document.writeln('<input type="hidden" name="machine_name" value="BRIAN" />');
```

---

### Post by epicoder on 2012-12-10
The code snippet you posted won't work in any properly functioning browser because of domain restrictions on scripts... That is, a page can't execute javascript outside of its own domain name. example.com/index.htm can't run different.org/jquery.js. The browser treats the user's hard drive as its own domain, thus preventing a page from executing local javascript.

Unfortunately, I can't think of any ways to actually accomplish this in a foolproof way... 
The only thing that comes to mind is have your access denied page leave a DOM storage object or a flash cookie containing a unique id corresponding to an entry in a log. However, your clients would be able to clear those.

The easiest solution would probably be to get your IT department to install java on all the workstations.

---

### Post by haqking on 2012-12-10
If it is at work, and sites are officially controlled then why arent the employess going through a proxy which a) controls what they can go to  b) logs everything

Also are you supposed to be doing it as you say it is not your call ?

---

### Post by SeijiSensei on 2012-12-10
The most effective approach for this problem is to put a [Squid]("http://www.squid-cache.org/") proxy either on or just behind the egress router and run it in transparent mode.  You won't be able to control HTTPS requests; for those you'll need iptables rules.  If your network is centrally managed with something like Active Directory, you could use [SslBump]("wiki.squid-cache.org/Features/SslBump") to manage HTTPS after deploying certificates to everyones' browsers and using policies to force everyone to use the proxy.

---

