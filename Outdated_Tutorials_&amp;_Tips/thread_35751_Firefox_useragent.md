---
title: "Firefox useragent"
date: 2005-05-20
forum: Outdated Tutorials &amp; Tips
---

### Post by hazza96 on 2005-05-20
I recently installed Firefox 1.04 from backports. I then tried to install some themes from [www.mozilla.org](https://addons.mozilla.org/themes/moreinfo.php?application=firefox&numpg=10&id=9)  and it kept saying that I did not have the latest 1.04 and I should download and upgrade.

I found that the useragnet reported by the BP Firefox 1.04 was "Firefox/1.0"

I searched and found that the file "/usr/lib/mozilla-firefox/defaults/pref/firefox.js" contains the reported useragent. Edit that file so that that line 130 says 1.0.4 and you are away.

---

### Post by Poul on 2005-05-20
wow
thanks

---

### Post by Kyral on 2005-05-20
Mine says 1.0.4 and it still won't let me update. How do you find out what your browser is reporting as?

This is whatmy code says

```
pref("app.version", 
"1.0.4"
```

---

### Post by Jussi Kukkonen on 2005-05-20
just put 
```
about:config
```
in Firefox address bar, find the preference *general.useragent.vendorSub* and change its value to *1.0.4* 

(Kyral: I think you're changing the wrong preference)

---

### Post by Kyral on 2005-05-20
Hehe, that got it, thanks.

Man do I feel stupid.... :-P

---

