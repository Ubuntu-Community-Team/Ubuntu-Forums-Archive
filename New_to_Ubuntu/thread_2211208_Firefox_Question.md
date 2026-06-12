---
title: "Firefox Question"
date: 2014-03-14
forum: New to Ubuntu
---

### Post by SiflOlly on 2014-03-14
This might be a weird issue/preference.  When I click the address bar in Firefox, or any other browser, on any other OS, it selects the whole text.  With Ubuntu, it just puts the cursor where you click.  Highly annoying... Is there any way to fix this?  I know it's a minor issue, and I can live with it, but it drives me nuts.

---

### Post by entropy1 on 2014-03-14
Try double clicking instead.

---

### Post by vasa1 on 2014-03-14
> **SiflOlly said:**
> This might be a weird issue/preference.  When I click the address bar in Firefox, or any other browser, on any other OS, it selects the whole text.  With Ubuntu, it just puts the cursor where you click.  Highly annoying... Is there any way to fix this?  I know it's a minor issue, and I can live with it, but it drives me nuts.

Go into about:config and set *browser.urlbar.clickSelectsAll* to *true*.

Also, at least in Linux, I doubt very much that "When I click the address bar in Firefox, or any other browser, on any other OS, it selects the whole text" is true by default. I know that for Chrome/Chromium the default is to click three times in the address bar to select everything.

---

### Post by andrew.46 on 2014-03-15
Stop all the clicking and press ctrl + l :)

---

### Post by vasa1 on 2014-03-15
> **andrew.46 said:**
> Stop all the clicking and press ctrl + l :)
Or alt + d if OP wants another keyboard route :)

---

### Post by claracc on 2014-03-15
In my ubuntu 12.04 firefox, the default behaviour is to "double click" in url bar address in order to select all.

What I have in about:config page is:

browser.urlbar.clickSelectAll set to false
browser.urlbar.doubleClickSelectAll set to true

So, I understand that if you want to select the text with only one click you will have to have:

browser.urlbar.clickSelectAll set to true
browser.urlbar.doubleClickSelectAll set to false

---

### Post by vasa1 on 2014-03-15
> **claracc said:**
> In my ubuntu 12.04 firefox, the default behaviour is to "double click" in url bar address in order to select all.

What I have in about:config page is:

browser.urlbar.clickSelectAll set to false
browser.urlbar.doubleClickSelectAll set to true

So, I understand that if you want to select the text with only one click you will have to have:

browser.urlbar.clickSelectAll set to true
browser.urlbar.doubleClickSelectAll set to false

Interesting point!

Just checked and I have both set to "true". The "double" one is marked "default" and the other one is "user set". I guess if both are true, the first one works without having to set the second to "false". 

Could you try that?

---

### Post by claracc on 2014-03-15
Yes vasa1, you are right.

I have tried in about:config page to set:

browser.urlbar.clickSelectAll to true

and browser.urlbar.doubleClickSelectAll remains as true

and efectively, when I click (only once) in the text in url bar, all the text is highlighted.

Regards.

---

