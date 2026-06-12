---
title: "Web site problem"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by JureM on 2012-07-09
Hello. I'm new Ubuntu user from Slovenia. I have a problem with the Web site [www.avto.net](www.avto.net) (web site to buy or sell cars and car parts :) ) and its results. I use Ubuntu 12.04 operating system and Web browser Chromium/FF/Chrome. The problem is on all 3 browsers. When I select the desired brand and model of car, click Iskanje oglasov (english: Search ads) and displays only the top menu (Uvodna, Avto, Moto, ...), the browser shows the status that page is loading but eventually returns an error (error 7: err_timed_out). In Windows operating systems, such problems are not. Click search ads, for a short time it displays the top menu, then automatically refresh the page again and displays the results of search. The problem in my Ubuntu OS only appears on the website [www.avto.net](www.avto.net) (other web sites that I visit work ok).
PS.My english is not very good. I hope you understand what's my Ubuntu problem. :)

---

### Post by Rex Bouwense on 2012-07-09
Sounds like the web site is having a problem since other web sites load properly.  I would wait a few hours and try to visit it again.
Welcome to the forums.

---

### Post by JureM on 2012-07-09
I think that the problem is in my computer because I tried on computer with windows os, it works normally. I tried through proxy but without success.

---

### Post by SeijiSensei on 2012-07-09
Some websites stupidly look at the "User-Agent" data you send to make sure you're using an "approved" browser/OS combination.  One trick is to install the Firefox add-on called [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/") which can be configured to tell the remote site that you're using IE on Windows when you're really running Firefox on Linux.

Are you using any forms of ad blocking or cookie management tools like [Ghostery]("https://addons.mozilla.org/en-US/firefox/addon/ghostery/")?  It could be that you're blocking something, and the remote site refuses to load unless it can send that object to you.  When it finds it cannot do so, it times out.  If you are using something like [AdBlock Plus]("https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/"), click the down arrow next to its stop-sign logo and disable it on the page you're having problems with.  Then try reloading the page.

---

### Post by JureM on 2012-07-09
Ok, i will try that useragent.
No, i don't use any add blocks.

---

### Post by JureM on 2012-07-09
I tried UserAgent but website still doesn't work :(

---

### Post by SeijiSensei on 2012-07-09
Site works for me from here in the US with Firefox on Linux. I did a search for "Cadillac" and got half-a-dozen replies within seconds.

---

### Post by JureM on 2012-07-09
Still without success. I don't know what to do.
Anyway, thanks to everybody who tried to help me.:)

---

### Post by JureM on 2012-07-12
Any ideas?

---

### Post by JureM on 2012-08-06
up

---

### Post by audiomick on 2012-08-06
The site works for me, using Firefox on 10.04 from Germany. I am using AdBlock Plus and Ghostery, and have things blocke, all though I am not sure exactly what on this install. Anyway, I don't think any of those are the problem. 

The behaviour of the site looks sloppy to me. I suspect it is not all that elegantly programmed. Maybe the problem you have is related to Flash. Have you done anything related to flash like trying to install a different version of the flash player or similar?

---

### Post by Frogs Hair on 2012-08-06
The site is functional in Opera and Chrome . Are you running any script or ad blocking extensions ?

---

### Post by JureM on 2012-08-06
no scripts, no add blocker, or anything else. just chrome, installed from programmes center. flash player is built-in chrome.

---

### Post by flyfishingphil on 2012-08-06
> **SeijiSensei said:**
> Some websites stupidly look at the "User-Agent" data you send to make sure you're using an "approved" browser/OS combination.  One trick is to install the Firefox add-on called [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/") which can be configured to tell the remote site that you're using IE on Windows when you're really running Firefox on Linux.

Are you using any forms of ad blocking or cookie management tools like [Ghostery]("https://addons.mozilla.org/en-US/firefox/addon/ghostery/")?  It could be that you're blocking something, and the remote site refuses to load unless it can send that object to you.  When it finds it cannot do so, it times out.  If you are using something like [AdBlock Plus]("https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/"), click the down arrow next to its stop-sign logo and disable it on the page you're having problems with.  Then try reloading the page.
Dom arrigato Seijisensei. Was not aware of that add-on's ability. Just added in and several sites work much better now.

---

