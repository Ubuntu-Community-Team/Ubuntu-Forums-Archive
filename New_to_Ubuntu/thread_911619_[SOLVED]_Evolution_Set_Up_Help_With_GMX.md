---
title: "[SOLVED] Evolution Set Up Help With GMX"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by Absolute4Zero on 2008-09-05
Hello there

I am having difficulty of setting up evolution with my gmx email (global mail exchange, i was wondering if there is anyone who uses the same service or similar one that explain or give more details on how to do it. any information is appreciated

---

### Post by knix on 2008-09-05
I'm using gmx, hven't tried it with evolution yet, but I'll give it a try.

---

### Post by knix on 2008-09-05
imap server: imap.gmx.com
smtp server: mail.gmx.com

for your user name, use [email]username@gmx.com[/email]

leave everything else as default.

just tried it, set it up in ~2 minutes.

---

### Post by Absolute4Zero on 2008-09-05
thank you so much, it really works, i tried so many ways and could not figure it out, thanks a lot mate nice one

---

### Post by knix on 2008-09-05
Evolution loads a lot faster than gmx's webmail. I'm glad you mentioned the idea.

---

### Post by osowiecki on 2009-09-06
I have followed the above instructions and do receive mail.
But when it comes to sending an email, it hangs.
the mail remains in the outbox unsent.
I have hit the send/receive button "sending message 1 of 1"....
please help.

---

### Post by Rytron on 2010-02-11
Could someone post a step by step guide?

---

### Post by lisati on 2010-02-11
> **knix said:**
> Evolution loads a lot faster than gmx's webmail. I'm glad you mentioned the idea.
+1. I noticed too....
> **Rytron said:**
> Could someone post a step by step guide?
Setting up email accounts with evolution is similar to other email clients. You can find the relevant part of Evolution by clicking on its "edit"->"preferences" menu item.

---

### Post by Rytron on 2010-02-12
All I get is this [pictures attached]. It just hangs. I tried different settings. I was able to receive mail but I cannot send.

---

### Post by kitchenguy on 2011-01-22
I got GMX working with Evolution by adding the following and you may need to check your firewall as well.

Receiving is easy and they detail that on their page, you use basically the same setting as they outline for Thunderbird.

Sending was harder, and only worked from trial and error.


[LIST=1]
[*]Server - mail.gmx.com
[*]Tick the "Server requires authentication" checkbox
[*]Select SSL encryption from the dropdown under Security
[*]In the Authentication area I chose
[/LIST]

[LIST]
[*]Type - POP before SMTP
[*]Username - enter your full GMX address
[*]Tick the "Remember Password" box
[/LIST]
I use Firestarter as my firewall and I found that it was blocking the connection.  If you watch the Events tab when you are trying to do something it will display blocked connections.  I enabled port 465 as an allowed outbound connection and it worked fine.  I don't know that much about networks and sockets etc so you need to be careful here because you are opening a port that might be then used by a naughty person . . . so take my advice on opening this port as amateur opinion only and maybe even ask someone who does know about networks and security (just my disclaimer)

Hope it works for you

---

### Post by Rytron on 2011-01-25
Thank you kitchenguy. ;)

---

### Post by abdusamed on 2011-02-11
i'm getting 

```
Error while Sending message.

Welcome response error: Input/output error 
```

---

### Post by abdusamed on 2011-02-15
doesn't work!

---

### Post by lisati on 2011-02-15
> **abdusamed said:**
> doesn't work!

What doesn't work? I have successfully used Evolution to read emails @ GMX for quite some time......

---

### Post by abdusamed on 2011-02-16
Evolution isn't able to send email using GMX. Gmail works fine. 

I'm trying POP because IMAP is just a bit annoying on a slow connection.

---

### Post by Rytron on 2011-02-16
Thunderbird works perfectly with GMX. ;)

---

### Post by abdusamed on 2011-02-19
it doesn't work on my thunder bird either... it just keeps on loading

ends wth 'timeout' error

fixed by changing the security option to SSL

---

