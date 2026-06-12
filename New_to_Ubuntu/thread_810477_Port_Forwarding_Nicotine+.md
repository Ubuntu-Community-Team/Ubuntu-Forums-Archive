---
title: "Port Forwarding Nicotine+"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by nilsolaris on 2008-05-28
Im having quite a hard time figuring out how to forward the ports for nicotine... followed steps at [www.portforwarding.com](www.portforwarding.com) yet still have not gotten anywhere. Suggestions?

---

### Post by Weidbrewer on 2008-05-28
Although not familiar with Nicotine, I get the general gist of what it is.  Can you give us some more information, such as what kind of router you're using?

---

### Post by nilsolaris on 2008-05-28
Bell Speedstream 6520.

---

### Post by Weidbrewer on 2008-05-28
And, of course, they don't seem to have any instructions for that particular client...Drat.  Well, we'll just roll with it.

First off, since I'm not familiar with Nicotine (I hate typing that...haven't had a smoke since January 15th, and just that *word* is getting me) is there a reason that you are using that instead of, say, something like Azureus?

In regards your specific case:  Are you getting an error of some sort, or is it just not working?  (If error, what is it?  If not working, in what way is it not working?)  Also, which port are you forwarding?   Have you tried using a different one.

Another cause for problem might be your provider.  Some ISPs block port forwarding, and we're SOL in that case.  My ISP just throttles the hell out of it, but still allows it.

---

### Post by nilsolaris on 2008-05-28
Ive used soulseek (windows nicotine) for a long while, and love it to death for huge music archives. Nicotine is amazing, i can use all the features, searching, chat etc. etc. but as soon as i go to download it will not connect. The ports are 2232 and 2239.

---

### Post by Monicker on 2008-05-28
This says which ports need to be forwarded:

[http://nicotine-plus.sourceforge.net/NicotinePlusGuide/AdditionalDocs/SoulseekPorts.htm]("http://nicotine-plus.sourceforge.net/NicotinePlusGuide/AdditionalDocs/SoulseekPorts.htm")

---

### Post by Weidbrewer on 2008-05-28
So, since you used it on Windows without problem, then obviously your ISP doesn't block it.

Now, when I set mine up, the problem wasn't just the router.  Forwarding ports there was only part of the issue.  I also needed to forward the ports withing Ubuntu as well.  The following link isn't exactly where I found the solution, but until technology lets us hyperlink to a passage in a book, it will have to do.  ;)

[http://ubuntuforums.org/showthread.php?t=331161](http://ubuntuforums.org/showthread.php?t=331161)

Check that out, and see if that's something that you've done yet.  If not, it might be the solution.

---

### Post by Monicker on 2008-05-28
> **Weidbrewer said:**
> So, since you used it on Windows without problem, then obviously your ISP doesn't block it.

Now, when I set mine up, the problem wasn't just the router.  Forwarding ports there was only part of the issue.  I also needed to forward the ports withing Ubuntu as well.  The following link isn't exactly where I found the solution, but until technology lets us hyperlink to a passage in a book, it will have to do.  ;)

[http://ubuntuforums.org/showthread.php?t=331161](http://ubuntuforums.org/showthread.php?t=331161)

Check that out, and see if that's something that you've done yet.  If not, it might be the solution.

Hrmm. Ubuntu does not block any ports by default.  Unless he installed something like Firestarter or manually changed the iptables rules, then he should not have to do anything else besides the port forwarding.

---

### Post by Weidbrewer on 2008-05-28
> **Monicker said:**
> Hrmm. Ubuntu does not block any ports by default.  Unless he installed something like Firestarter or manually changed the iptables rules, then he should not have to do anything else besides the port forwarding.

Not trying to say that you are wrong, by any means - I'm just speaking from person experience with my install:  I had zero luck until I forwarded the ports within Ubuntu.   Couldn't hurt to try.

---

### Post by fwre01 on 2008-05-28
Do you still use nicotine in windows (maybe in a dualboot senario)?

...because that wud verify the port forwarding

---

### Post by nilsolaris on 2008-05-28
Still doesnt seem to be working:S

---

### Post by nilsolaris on 2008-05-28
> **fwre01 said:**
> Do you still use nicotine in windows (maybe in a dualboot senario)?

...because that wud verify the port forwarding

No i am not.. this is a completely new computer and has been installed with xubuntu 8.4 from day one.

---

### Post by fwre01 on 2008-05-28
Are you forwarding other ports successfully?

...I found [this]("http://portforward.com/english/routers/port_forwarding/Bell/Speedstream6520/Echolink.htm")

---

### Post by nilsolaris on 2008-05-28
> **fwre01 said:**
> Are you forwarding other ports successfully?

...I found [this]("http://portforward.com/english/routers/port_forwarding/Bell/Speedstream6520/Echolink.htm")


Thank you!! Worked perfectly!:)

---

