---
title: "HOWTO: Disable &quot;Smarter&quot; Address Bar in Firefox 3"
date: 2008-05-11
forum: Outdated Tutorials &amp; Tips
---

### Post by RATM_Owns on 2008-05-11
The "smarter" address bar might be help for some people.
But for me, I really hate it. 

The first step, in the address bar, enter in 
**about:config**

It should give you some warning. Just disregard it.

In the search bar, enter:
**browser.urlbar**

Change the **browser.urlbar.matchOnlyTyped** boolean to True. 
(Double click it)

Next, change the **browser.urlbar.maxRichResults** integer to 0.
(Double click and enter in 0 instead of current number)

Finally, restart the browser. No more "smarter" address bar!

---

### Post by binarymutant on 2008-05-12
I tried the instructions but to no avail. When I changed the variable browser.urlbar.matchOnlyTyped it was still giving me weird matches. And when I changed browser.urlbar.maxRichResults to 0 it gave no results :( . Is there a way to get it back to the way firefox 2 did the address bar? Where if I was typing say lugradio it would show all the pages I've visted that start with the letter l.

---

### Post by PinkFloyd102489 on 2008-05-12
It worked for me but doesnt show anything anymore. Doesnt bother me that much, I only visit like 2 or 3 websites outside of my bookmarks toolbar.


Thanks for fixing that damn bar! Sped my Firefox up like you wouldnt believe. :-)

---

### Post by RATM_Owns on 2008-05-12
> **binarymutant said:**
> I tried the instructions but to no avail. When I changed the variable browser.urlbar.matchOnlyTyped it was still giving me weird matches. And when I changed browser.urlbar.maxRichResults to 0 it gave no results :( . Is there a way to get it back to the way firefox 2 did the address bar? Where if I was typing say lugradio it would show all the pages I've visted that start with the letter l.

Did you restart the browser?

---

### Post by binarymutant on 2008-05-12
yeah a few times now :(
Still getting weird suggestions instead of alphabetical order

---

### Post by DirtDawg on 2008-05-13
Actually, I love the new address bar. But I navigate with it instead of bookmarks so it annoyed me that I could only see 12 at a time. But fixing the **browser.urlbar.maxRichResults** to a higher number solved my annoyance! Thanks :)

---

### Post by gywst on 2008-06-12
From: [http://webware.com](http://webware.com) 
*There are, in fact, several ways to disable this feature entirely. One way is to follow the [instructions on this page]("http://kb.mozillazine.org/Browser.urlbar.maxRichResults"), which involves a small tweak to your about:config file. Doing so will disable the drop-down of links completely, but not your auto fill. There's also [an add-on extension]("https://addons.mozilla.org/en-US/firefox/addon/6227") that mimics the behavior of the address bar found in Firefox 2 with slightly smaller favicons, link text, and sorting.*

Instructions
[http://kb.mozillazine.org/Browser.urlbar.maxRichResults](http://kb.mozillazine.org/Browser.urlbar.maxRichResults)

add-on extension
[https://addons.mozilla.org/en-US/firefox/addon/6227](https://addons.mozilla.org/en-US/firefox/addon/6227)

---

### Post by jb21206 on 2009-05-17
I stumbled onto Ubuntu through a search while trying to disable smarter address bar in firefox. I read the solution by [RATM_Owns]("http://ubuntuforums.org/member.php?u=552216") and bingo, no more issues. The instruction was exact and my computer is still running. Now I am a registered member here and I will recommend Ubuntu.com to anyone that needs help. 
 Thank you RATM :D

---

