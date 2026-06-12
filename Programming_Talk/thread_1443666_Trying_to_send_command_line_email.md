---
title: "Trying to send command line email"
date: 2010-03-31
forum: Programming Talk
---

### Post by u-slayer on 2010-03-31
Hi guys.

I'm trying to send email with python via the sendmail program, by following this guide: [Link]("http://effbot.org/pyfaq/how-do-i-send-mail-from-a-python-script.htm")

I can get 10minutemail.com to receive my email, but gmail either refuses or marks it as spam and yahoo.com and verizon completely ignore me. How do I make my email get passed the spam filters?

```
message='From: user@<my isp.net>\nTo: ##########@vtext.com, <personal>@gmail.com, a2138933@owlpic.com\nSubject: Python message 6\n\nThis message was sent via sendmail.\n'

p = os.popen("%s -t -i" % SENDMAIL, "w")
p.write(message)
status = p.close()
if status:
    print "Sendmail exit status", status

```

---

### Post by gmargo on 2010-03-31
Is your MTA set up correctly?  Can you otherwise send email (without python)?

---

### Post by u-slayer on 2010-03-31
> **gmargo said:**
> Is your MTA set up correctly?  Can you otherwise send email (without python)?

I can send email, but some servers won't accept it. I don't understand these MTA settings. If you could point me to the settings I need to change, that would be great.

---

### Post by lisati on 2010-03-31
When an email gets marked as spam, it's usually because the receiving MTA has some kind of filtering in place. Sometimes the filtering system gets it wrong. 
The filtering I use on my email server is based on a number of things. This includes checking a number of [DNSBL lists]("http://en.wikipedia.org/wiki/DNSBL") as well as a number of checks of the message content. You can check if your server is listed on a DNSBL list at web sites like [blacklistalert.org]("http://www.blacklistalert.org/") and [debouncer.com]("http://www.debouncer.com/")

---

### Post by u-slayer on 2010-03-31
> **lisati said:**
> When an email gets marked as spam, it's usually because the receiving MTA has some kind of filtering in place. Sometimes the filtering system gets it wrong. 
The filtering I use on my email server is based on a number of things. This includes checking a number of [DNSBL lists]("http://en.wikipedia.org/wiki/DNSBL") as well as a number of checks of the message content. You can check if your server is listed on a DNSBL list at web sites like [blacklistalert.org]("http://www.blacklistalert.org/") and [debouncer.com]("http://www.debouncer.com/")


```
0spam.fusionzero.com OK
aspews.ext.sorbs.net OK
bl.spamcop.net OK
bl.spamcannibal.org OK
blackholes.five-ten-sg.com OK
blackholes.intersil.net OK
bogons.cymru.com OK
cbl.abuseat.org OK
combined.njabl.org OK
db.wpbl.info OK
dnsbl.ahbl.org OK
dnsbl.inps.de OK
dnsbl.sorbs.net Listed! See why
dnsbl.rangers.eu.org OK
dnsbl-0.uceprotect.net OK
dnsbl-1.uceprotect.net OK
dnsbl-2.uceprotect.net OK
dnsbl-3.uceprotect.net OK
dyna.spamrats.com OK
ips.backscatterer.org OK
ix.dnsbl.manitu.net OK
l2.apews.org Listed! See why
no-more-funn.moensted.dk OK
noptr.spamrats.com OK
psbl.surriel.com OK
rbl.efnet.org OK
spam.spamrats.com OK
spamguard.leadmon.net OK
t1.dnsbl.net.au OK
tor.dnsbl.sectoor.de OK
ubl.unsubscore.com OK
virbl.dnsbl.bit.nl OK
zen.spamhaus.org Listed! See why 
```

Okay... Now what?

---

### Post by gmargo on 2010-03-31
You have an ISP, just submit your email through the ISP's mail server.

---

### Post by u-slayer on 2010-03-31
> **gmargo said:**
> You have an ISP, just submit your email through the ISP's mail server.

How do I do that from the command line?

---

### Post by gmargo on 2010-03-31
> **u-slayer said:**
> How do I do that from the command line?
Configure your MTA to do it.  What is the MTA?  Postfix?  I haven't used it in recent years but "dpkg-reconfigure postfix" will probably get you there.

---

### Post by u-slayer on 2010-03-31
> **gmargo said:**
> You have an ISP, just submit your email through the ISP's mail server.

Thanks for the help guys. I gave up trying to do this through my machine and just found a free SMTP server to send my mail. I just needed one more line of code to login:

server.login(username, password)

---

