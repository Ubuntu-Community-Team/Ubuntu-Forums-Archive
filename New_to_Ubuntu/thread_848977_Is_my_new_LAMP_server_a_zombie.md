---
title: "Is my new LAMP server a zombie?"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by thepiston on 2008-07-04
I installed 7.10 a while back and it's been running 24/7 ever since.  How do I make sure it hasn't been hacked and is sending out tons of spam emails?  The website it serves up is fine, but I don't check email on it or anything.

---

### Post by bab1 on 2008-07-04
Zombies are dead system processes.  
See:  [http://www.linuxsa.org.au/tips/zombies.html](http://www.linuxsa.org.au/tips/zombies.html)

If you have no mailserver on your system then you have no worries about sending spam.  I assume you have some sort of firewall protection.  You might want to use an IP sniffer to see what traffic is going in or out.

---

### Post by thepiston on 2008-07-04
> **bab1 said:**
> Zombies are dead system processes.  
See:  [http://www.linuxsa.org.au/tips/zombies.html](http://www.linuxsa.org.au/tips/zombies.html)

If you have no mailserver on your system then you have no worries about sending spam.  I assume you have some sort of firewall protection.  You might want to use an IP sniffer to see what traffic is going in or out.ok, if I just installed a LAMP, then I guess I don't even have mail, do I.

---

### Post by hyper_ch on 2008-07-04
zombies are also computers that were hacked and belong to a botnet now ;)

---

### Post by thepiston on 2008-07-04
yeah, so on my LAMP server that runs 24/7 without a monitor even on it, how can I make sure that's it's not infected?  I have a router firewall, but no software firewall on that box.

---

### Post by txcrackers on 2008-07-04
There is no magic "am I infected?" command - you have to do the due diligence yourself...

Install/setup a software firewall. Check for unwanted processes running on the box. Check for rootkit installations (there are utility programs for that). Check the timestamps/contents of all the files being served by the Apache server. Run an anti-virus check program. Do all of these continually - some of them can be set up to run on a periodic basis with cron.

There are lots of resources for maintaing LAMP servers on the net - you'll have to do some studying and, to quote Allister "Mad Eye" Moody, **"Constant vigilance!"**

---

