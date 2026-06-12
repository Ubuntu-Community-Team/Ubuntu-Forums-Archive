---
title: "I need help with steam"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by shamusl on 2008-08-24
I want to make a purchase through steam using paypal, however when I click paypal and click next, it brings me to a paypal payment page, then it tells me when I finished entering my details that "Your transaction is almost complete! Please click here to review your payment in Steam. When I click it, firefox gives me an error telling me that "Firefox doesn't know how to open this address, because the protocol (steam) isn't associated with any program", how do I associate steam with firefox so that I can complete this purchase? (I'm using wine 1.0 and firefox 3 on ubuntu 8.04 32 bit)

---

### Post by Vadi on 2008-08-24
Oh, I remember having this issue before also.

I googled for this, and it looks like you need to tell firefox to open steam:// links with "wine <path to>/steam.exe"

This [post]("http://basecamphq.com/forum-archive/viewtopic.php?pid=9135#p9135") describes how to do that.

And to get the <path to> steam, what you can do is open a terminal, and drag steam.exe into it. It'll give you a path.

---

### Post by Catalyst2Death on 2008-08-24
I'm assuming that this applies:
[http://mozex.mozdev.org/index.html](http://mozex.mozdev.org/index.html)
[http://www.linuxquestions.org/questions/linux-software-2/associate-mailto-in-firefox-to-a-program-174792/](http://www.linuxquestions.org/questions/linux-software-2/associate-mailto-in-firefox-to-a-program-174792/)

you should (hopefully) be able to customize a command that would look like:
```
wine /path/to/steam/exe/steam.exe

```

Hopefully you know if you use a custom wine command to run steam, in which case you should know it...

Are you doing this through Firefox from linux, or a page loaded via the steam GUI?  If its through the steam gui, I don't know you may have to hack something to get it to work.  I would suggest making the purchase on a windows machine and then logging in if at all possible...

One solution may be installing the windows version of firefox via wine to finish the purchase....

[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

---

