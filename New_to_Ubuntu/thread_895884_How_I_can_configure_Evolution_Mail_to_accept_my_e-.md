---
title: "How I can configure Evolution Mail to accept my e-mail adress?"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Harmony_Of_Distortion on 2008-08-20
Hello! I'm just istalled ubuntu 8.04 and I want to know how I can configure the Evolution Mail to accept my e-mail adress?

I have an account on hotmail. My e-mail adress has the following type

[www.xxxxxx@hotmail.com](www.xxxxxx@hotmail.com)

Can anyone tell me how I can configure the Evolution Mail to receive my e-mails via this programm?

Thanks!

---

### Post by mike555 on 2008-08-20
Hotmail is a Microsoft product , as such it's a bit different ... you will need a plugin to get it.... Well, I'm not sure about Evolution, but Thunderbird needs the webmail addon and the Hotmail addon ....
and of course you will need your user name and password .....

---

### Post by LowSky on 2008-08-20
[http://www.forwardhotmail.com/](http://www.forwardhotmail.com/)

but it looks grim for hotmail to link with Evo or T-bird

---

### Post by erginemr on 2008-08-20
I don't think you can use Evolution with your hotmail account. There is a howto on this topic:
[http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)
but it involves installing internet server daemons and therefore is quite complex. 

If you are insistent on using it however, you can install thunderbird with:
```
sudo apt-get install thunderbird
```
and also install the following add-ons to reach your hotmail account:
[http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html)
[http://www.math.colostate.edu/~reinholz/freebsd/thunderbird_tips.html](http://www.math.colostate.edu/~reinholz/freebsd/thunderbird_tips.html)

---

### Post by Liberator on 2008-08-29
> **erginemr said:**
> If you are insistent on using it however, you can install thunderbird...

Be aware that Thunderbird has had a huge bug with Hotmail for years.  It's still there and I don't think anybody is working on it.

The problem is that you can't properly forward HTML emails from Thunderbird using your Hotmail account.  The text will get forwarded but the pictures won't.

I don't see a good solution at the moment.  Here's what's out there that I am aware of:

1 - Thunderbird with WebMail and HotMail plugins (won't forward pictures in HTML emails, plus Hotmail may soon drop WEBDAV support upon which it depends).

2 - Evolution with Hotway and HotSMTP (complex, plus Hotmail may soon drop WEBDAV support upon which it depends)

3 - Various web-based 3rd party forwarders (your Hotmail login credentials plus all of your email are now in the hands of a 3rd party, plus a risk that it will break in the near future when Hotmail drops WEBDAV support upon which it presumably depends).

I wish that the short term news was better.  Long term there will be a workaround developed.  It's an arms race.

---

### Post by whitethorn on 2008-08-29
Well I read this somewhere and thought it's a pretty good idea.  Get yourself a different email account either at gmail, or gmx.  Somewhere where they support IMAP or POP3 access and then you hotmail account to forward you mail to that account.  Not exactly what you want, but I think it's better than giving your login account data to a third provider...

Wait I just tried to see if it works, forwarding only work for microsoft accounts...

---

### Post by Oldsoldier2003 on 2008-08-29
> **whitethorn said:**
> Well I read this somewhere and thought it's a pretty good idea.  Get yourself a different email account either at gmail, or gmx.  Somewhere where they support IMAP or POP3 access and then you hotmail account to forward you mail to that account.  Not exactly what you want, but I think it's better than giving your login account data to a third provider...

+1 gmail works well with evolution. Pop access to hotmail is iffy unless you have a paid account.

---

