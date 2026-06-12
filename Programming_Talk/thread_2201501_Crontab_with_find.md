---
title: "Crontab with find"
date: 2014-01-24
forum: Programming Talk
---

### Post by Langstracht on 2014-01-24
I have been trying and failing to concoct a crontab command which would:

1 open  a browser (google chrome or whatever) and perform a specified find on an identified site (something like "find mannerheim site:dw.de").

OR

2 open a browser on a site (dw.de) and then perform a specified find on that site.

I'd rather not have to be limited to a single word search, but I can live with that limitation if I have to.

So, I've gotten nowhere.   Anyone know how to do it ... or if it can in fact be done?

TIA.

---

### Post by Lars Noodén on 2014-01-24
I can't remember how to get a browser to open (or re-use) a specific window or tab.  

But to lauch a graphical program into your existing display you have to set the DISPLAY environment variable for that particular instance of the program.

```

DISPLAY=:0.0 /usr/bin/firefox http://www.ixquick.com/

```

---

### Post by Langstracht on 2014-01-24
Actually I gave up/in too soon.

I've gone back and given it another try and now we're good. 

At least for me

```
export DISPLAY=:0 && chromium-browser http://google.com/search?h1=en+q=1stSearchTerm+2ndSearchTerm+site:dw.de
```

works.

---

