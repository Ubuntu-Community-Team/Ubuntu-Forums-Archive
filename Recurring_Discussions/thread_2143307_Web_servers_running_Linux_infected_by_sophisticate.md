---
title: "Web servers running Linux infected by sophisticated malware"
date: 2013-05-08
forum: Recurring Discussions
---

### Post by Dry Lips on 2013-05-08
Hi, I just stumbled upon this disturbing article, and I wanted to know what you guys make of this... :-k




> **Attack hitting Apache sites goes mainstream, hacks nginx, Lighttpd, too**
Linux/Cdorked backdoor exposes 100,000 Web visitors to potent Blackhole exploits.
[COLOR=#263034][FONT=Arial]
[...]

"A couple years ago malware against the Linux operating system was really in the age of its proof of concept," he said. "Whenever we would discover something everybody would say: 'It's not really in wild. It's just somebody trying to prove a point.' Now the fact that we see so many instances of infected Web servers out there really shows we're past the era of the proof of concept. Now serious operators are making serious money by victimizing these web servers."[/FONT][/COLOR][URL="http://arstechnica.com/security/2013/05/attack-hitting-apache-sites-goes-mainstream-hacks-nginx-lighttpd-too/"]

[/URL]
read more:

[http://arstechnica.com/security/2013/05/attack-hitting-apache-sites-goes-mainstream-hacks-nginx-lighttpd-too/](http://arstechnica.com/security/2013/05/attack-hitting-apache-sites-goes-mainstream-hacks-nginx-lighttpd-too/)

---

### Post by MadmanRB on 2013-05-08
a patch will come out soon, thus the advantage of open source.

---

### Post by Dry Lips on 2013-05-08
> **MadmanRB said:**
> a patch will come out soon, thus the advantage of open source.

Apparently the problem is that researchers don't know how the servers are being infected in the first place.

> [COLOR=#263034][FONT=Arial]Researchers still don't know how servers are being infected with Cdorked. Because compromised machines are running a variety of administration controls, cPanel and competing software aren't obvious suspects. Cdorked doesn't have the ability to spread by itself and doesn't exploit a vulnerability in any other specific piece of software, either. **- ibid.** [/FONT][/COLOR]

---

### Post by mastablasta on 2013-05-09
is the system that is infected or the servers? at one point the article talks about how the servers get infected with different code. and then suddenly how the OS got infected.

so Java can (potentially) be exploited in Linux as well. does that mean linux itself is always vulnerable?

furthermore no system is 100% bulletproof. it's just how hard it is to crack it.

---

### Post by alphacrucis2 on 2013-05-09
> **mastablasta said:**
> is the system that is infected or the servers? at one point the article talks about how the servers get infected with different code. and then suddenly how the OS got infected.

so Java can (potentially) be exploited in Linux as well. does that mean linux itself is always vulnerable?

furthermore no system is 100% bulletproof. it's just how hard it is to crack it.

They say that the apache2 binary has been replaced by a bogus version. That would require root access. It is possible that the servers have been compromised by an ssh brute force password attack or even phishing, or more worrying a possible zero day exploit that hasn't been figured out by the good guys yet. I know of a forum admin, who was fooled into giving away his admin usercode and password through a directed phishing attack. I suppose it is possible that the admins of these servers have been tricked by some sort of phishing scheme. From what I have read, the security analysts haven't yet actually determined how the initial compromise has occurred.

---

### Post by mastablasta on 2013-05-09
phishing was the first thing that popped into my mind. but then it would be kind of strange they would get it from admin of server. i doubt these sites with so many hits are some privately run servers. then again sometimes you want to be helpfull... and i saw some extremely strange practice by a host. they needed me to give account password to help me. luckily their help was to melp me move away from them (so i gave them the password). and i know plenty pages on that host have very high ratings.

hope it's not a zero day and if it is that it get's patched.

---

### Post by SeijiSensei on 2013-05-09
Like earlier articles about this exploit, the article mentions it being found on some 400 web servers.  That is out of a universe of over 300 million domains served by Apache.

The fact that the exploit requires replacing the Apache binary with a corrupt version means the attacker needed to have root privileges on the machine already.  

I'm not very worried.

---

### Post by Gone fishing on 2013-05-09
If this exploit requires root access through something like a phishing or ssh brute force attack then this implies the security is pretty good, if these systems were compromised in some type of trivial remote attack then I'd be concerned.

---

### Post by Dry Lips on 2013-05-10
A more technical description of *Linux/Cdorked.A* can be found here:

[http://www.welivesecurity.com/2013/05/07/linuxcdorked-malware-lighttpd-and-nginx-web-servers-also-affected/](http://www.welivesecurity.com/2013/05/07/linuxcdorked-malware-lighttpd-and-nginx-web-servers-also-affected/)


see also:
[http://www.welivesecurity.com/2013/05/02/the-stealthiness-of-linuxcdorked-a-clarification/](http://www.welivesecurity.com/2013/05/02/the-stealthiness-of-linuxcdorked-a-clarification/)

---

### Post by CharlesA on 2013-05-11
Nice links, thanks. I saw an article about this on slashdot, but those were more in-depth.

As far as I can tell the only way this can happen if either thru gaining root access via weak passwords or using another exploit to preform privilege escalation.

---

### Post by prodigy_ on 2013-05-11
```
Researchers still don't know how servers are being infected with Cdorked.
```
Oh yeah? :) Well, maybe research isn't their field of expertise then. I'd say something else might suit them better... like street cleaning or field painting.

All in all it's just another FUD article. And the original one by ESET isn't much better. In fact ESET should focus on making **quality** anti-malware products instead of trying to gain free publicity. They still can't compete with Symantec/Norton, Kaspersky Lab or Trend Micro.

---

### Post by Primefalcon on 2013-05-11
I wouldn't call norton/symantic a good anti-virus product

---

### Post by Sef on 2013-05-11
Moved to recurring discussions. Nothing new about this.

---

