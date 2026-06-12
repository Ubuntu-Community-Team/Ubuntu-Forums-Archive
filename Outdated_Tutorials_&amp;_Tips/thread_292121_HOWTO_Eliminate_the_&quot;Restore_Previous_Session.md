---
title: "HOWTO: Eliminate the &quot;Restore Previous Session&quot; dialog when Firefox 2.0 starts"
date: 2006-11-03
forum: Outdated Tutorials &amp; Tips
---

### Post by paul6 on 2006-11-03
If you want to get rid of the "Restore Previous Session" dialog and simply start a new session everytime, you need to add one value in your Firefox config file.

1) Go to your about:config file by typing about "about:config" (without the quotes) in the address bar and press enter.

2) Right click any part of the page, select "New," than "Boolean". A popup should appear asking for the preference name. Enter "browser.sessionstore.resume_from_crash" (without the quotes) . Select "false" as the value.

Restart Firefox, and your done!

Info in this howto taken from [here.]("http://kb.mozillazine.org/Browser.sessionstore.resume_from_crash") ;)

---

### Post by kooldino on 2008-01-01
I love you.

---

### Post by Rob Loach on 2008-12-23
Christ this thing is annoying and it still happens in FireFox 3.x..... Thanks!

---

### Post by tturrisi on 2008-12-23
Annoying?
My God, then you must have a lot of FF crashes then!

I dig the feature.  The usuall cause of FF crashes is due to Flash Player not being handled correctly by the browser, and in some cases, closing a tab or FF window w/ embedded Flash will not close that particular FF process... memory leaks and then FF crashes.

But what if you really want to get back to the other sites you were viewing in tabs or other windows?  The restore session after crash is a great feature to have, it saves a lot of clicking and typing.

Oh, & to prevent these Flash caused crashes, and depending upon your version of FF and version of Flash, it is always best use the stop button when viewing flv files like youtube videos prior to navigating elsewhere.

---

### Post by nigeldodd on 2009-02-16
It is a security issue. A restored Gmail tab, for instance, remembers that it is logged in! Same with Google docs and spreadsheets. Even with the suggested config file entry, a suspecting hacker could change it back before starting up Firefox.

---

### Post by mr.natural on 2010-05-23
Thank you!

---

