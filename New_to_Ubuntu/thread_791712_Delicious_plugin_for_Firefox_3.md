---
title: "Delicious plugin for Firefox 3"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Inxsible on 2008-05-12
I am really hooked onto del.icio.us for my bookmarks. I used the Delicious Bookmarks plugin for Firefox 2. But it doesn't work in FF3. I know I can login to the delicious website and get things done, but I find the FF plugin to be handy since I keep bookmarking random sites all the time.

I would really like to use FF3 since it has better support for Indic languages. Can anyone suggest any delicious plugins for FF3?

A simple search for it on Firefox's website doesn't yield any plugins working for FF3 b5

---

### Post by Cypher on 2008-05-12
You can grab the Beta version of the plugin from the [Yahoo Tech group]("http://tech.groups.yahoo.com/group/delicious-firefox-extension/message/2376") and it'll work on FF3..you'll have to Join the group to access the file..

---

### Post by philphil on 2008-05-12
I read (can't remember where) that with each major FF upgrade there's always a long time in which you have to wait for your plugins to be upgraded before they'll work, so I'd stick with FF2 if you need your plugins to work.

---

### Post by Cypher on 2008-05-12
On the contrary..most authors of popular plugins support FireFox in it's beta forms..but some choose to wait for an RC or full release before providing support quickly just so that they don't have to deal with fluctuating APIs..

---

### Post by philinux on 2008-05-12
1. In the Firefox address bar type “about:config”
2. Right click in the list of settings, choose New > Boolean
3. Type the phrase “extensions.checkCompatibility” and press enter
4. Choose “false” as the value
5. Restart Firefox

---

### Post by dfour on 2008-05-12
[http://blog.delicious.com/blog/2008/04/firefox-3-delicious-and-you.html](http://blog.delicious.com/blog/2008/04/firefox-3-delicious-and-you.html)

---

### Post by Inxsible on 2008-05-12
> **philinux said:**
> 1. In the Firefox address bar type &#8220;about:config&#8221;
2. Right click in the list of settings, choose New > Boolean
3. Type the phrase &#8220;extensions.checkCompatibility&#8221; and press enter
4. Choose &#8220;false&#8221; as the value
5. Restart Firefox
That has crashed my Firefox and now I have no way to get back into it and delete the new setting that I created. :(

I even tried re-installing FF3. No luck. Does anyone know how to delete an entry in the about:config page without going to that page in FF ?

I mean there has to be a config or ini file where it stores that information in. BTW I am currently on my XP machine. Was testing this at work.

---

### Post by philinux on 2008-05-12
Works fine here.

Use

firefox -safe-mode

from the terminal.

---

### Post by philinux on 2008-05-12
Close firefox

Go into your .mozilla folder.

Back up prefs.js

Use gedit to edit the pref.js file to delete the entry.

---

### Post by Inxsible on 2008-05-12
I am currently at work on an XP machine. It is on the XP machine that I tried to add the additional property. Do you know how to delete that property in XP?

---

### Post by Cypher on 2008-05-12
I'm curious to see why faking the FF version is better to do than using the beta of the plugin??

---

### Post by philinux on 2008-05-12
I thought you were on ubuntu. :(

[http://support.mozilla.com/en-US/kb/Profiles#How_to_find_your_profile](http://support.mozilla.com/en-US/kb/Profiles#How_to_find_your_profile)

---

### Post by Inxsible on 2008-05-12
Alright deleted the property from the prefs.js file -- In XP its under C:\Documents and Settings\username\Mozilla\Firefox\Profiles\xxxxxxx.default

Then re-installed FF3 and now I am back in FF. On to trying Cypher's solution :)

---

### Post by philinux on 2008-05-12
> **Inxsible said:**
> Alright deleted the property from the prefs.js file -- In XP its under C:\Documents and Settings\username\Mozilla\Firefox\Profiles\xxxxxxx.default

Then re-installed FF3 and now I am back in FF. On to trying Cypher's solution :)

Phew, glad about that.

---

