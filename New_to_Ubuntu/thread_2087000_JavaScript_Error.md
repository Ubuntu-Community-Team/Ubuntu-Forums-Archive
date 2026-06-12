---
title: "JavaScript Error"
date: 2012-11-22
forum: New to Ubuntu
---

### Post by llmunro on 2012-11-22
Hi y'all,

I don't know if this is a Firefox problem or a Ubuntu (12.10) problem, but after the software updater ran a partial upgrade this morning, every time I try to navigate to a new page with Firefox 17 (which was part of the upgrade, apparently), a small box pops up with the window title JavaScript Application with the message, Error: syntax error.  
This doesn't seem to happen on Chrome (to which I've fled in the meantime), but I'd really like to go back to Firefox. I have zero idea what this means or how to even start trying to fix it. Does anyone have any suggestions or things to try?

Thanks much.
Best,
Lisa

---

### Post by Pletched on 2012-11-22
```
firefox -ProfileManager
```

Could be something wrong with your profile. Type that into a terminal. Make sure firefox is not open. Make a new profile. 

If you need more help look [here]("http://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles").

---

### Post by LuisGMarine on 2012-11-22
I've had a similar problem with firefox, and I also had to run to Chrome.  However updating to the latest version of java helped me fix that problem in firefox.  I hope that it might do the same for you.

[http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html")

---

### Post by Pletched on 2012-11-22
Javascript and Java aren't the same. 

Are you sure?

---

### Post by llmunro on 2012-11-25
Hi y'all!

It appears that this was indeed a Firefox problem, caused by the Social Fixer extension.  Removed said extension and problem solved!
:)

Thanks.
Best,
Lisa

---

