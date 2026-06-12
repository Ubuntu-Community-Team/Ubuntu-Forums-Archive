---
title: "Silverlight equivalent for Chromium?"
date: 2012-04-23
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-23
I understand that Moonlight Ubuntu is an alternative for Silverlight for Firefox Windows.

Will it work on Chromium Ubuntu?

If not, is there an alternative for Chromium?

Note*  If you have installed Google Chrome or Chromium, you will also need to install this file to use Moonlight on that browser.

When you click, nothing there.

see: [https://help.ubuntu.com/11.04/ubuntu-help/net-install-moonlight.html](https://help.ubuntu.com/11.04/ubuntu-help/net-install-moonlight.html)


stU

---

### Post by pqwoerituytrueiwoq on 2012-04-23
[FONT="Courier New"]sudo apt-get install [moonlight-plugin-chromium](apt:moonlight-plugin-chromium)[/FONT]
if the link does not work the apt protocol is not enabled in your browser

---

### Post by Boyntonstu on 2012-04-23
> **pqwoerituytrueiwoq said:**
> [FONT="Courier New"]sudo apt-get install [moonlight-plugin-chromium](apt:moonlight-plugin-chromium)[/FONT]
if the link does not work the apt protocol is not enabled in your browser

boyntonstu@boyntonstu-s5704y:~$ sudo apt-get install moonlight-plugin-chromium
[sudo] password for boyntonstu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package moonlight-plugin-chromium
boyntonstu@boyntonstu-s5704y:~$

---

### Post by sanderj on 2012-04-23
I installed via [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

HTH

---

### Post by Frogs Hair on 2012-04-23
I found this link if installing from the website fails. [http://dennygoot.blogspot.com/2012/01/moonlight-installed-in-firefox-on.html](http://dennygoot.blogspot.com/2012/01/moonlight-installed-in-firefox-on.html)

---

### Post by Boyntonstu on 2012-04-23
> **sanderj said:**
> I installed via [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

HTH

+1

Worked perfect!

Thanks

stU

---

### Post by Curtis6767 on 2012-04-23
How many of these work with the Silverlight plugin?

[http://rockstartemplate.com/tutorial/websites/10-silverlight-sites/](http://rockstartemplate.com/tutorial/websites/10-silverlight-sites/)

Thanks

---

### Post by directhex on 2012-04-24
Moonlight's dead.

---

### Post by rgrig on 2012-05-09
> **directhex said:**
> Moonlight's dead.
Can you elaborate?

---

### Post by kellemes on 2012-05-09
> **Curtis6767 said:**
> How many of these work with the Silverlight plugin?

[http://rockstartemplate.com/tutorial/websites/10-silverlight-sites/](http://rockstartemplate.com/tutorial/websites/10-silverlight-sites/)

Thanks

For me they all seem to work, using Chromium with Moonlight.

---

### Post by alphacrucis2 on 2012-05-09
> **directhex said:**
> Moonlight's dead.

I heard Silverlight is dead too.

---

### Post by directhex on 2012-05-11
> **rgrig said:**
> Can you elaborate?

It has 0 developers.

The team who were working on it at Novell got laid off, and the project never attracted any community developers, thanks to phenomenal community hubris

---

