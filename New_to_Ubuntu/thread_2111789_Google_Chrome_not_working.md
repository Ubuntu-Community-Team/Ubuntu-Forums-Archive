---
title: "Google Chrome not working"
date: 2013-02-02
forum: New to Ubuntu
---

### Post by regice9 on 2013-02-02
Hello. Last night at somewhere around midnight the java plugin on Google Chrome seemed to have screwed up. If I go to the java site and test it, it pulls up the "outdated" box, with the "update" or "run this time" options. However, for some reason, when I go on YouTube, there is no sort of notification, the place where the video goes just has a grey box in the centre that says "Couldn't load plug-in"

I have tried multiple times to update java with various methods, none of which helped, and have reinstalled Chrome twice. There does not seem to be any solution to this daft thing.

---

### Post by monkeybrain2012 on 2013-02-03
Are you using openjdk? For some reason it has been flagged as outdated by chrome for quite sometimes. If it is still a problem you can install up to an date version of Oracle's java7 with the webupd8 ppa

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by MadmanRB on 2013-02-03
Just be careful with standard java right now, there have been some major security bugaboos.

---

### Post by regice9 on 2013-02-03
> **monkeybrain2012 said:**
> Are you using openjdk? For some reason it has been flagged as outdated by chrome for quite sometimes. If it is still a problem you can install up to an date version of Oracle's java7 with the webupd8 ppa

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)
Tried PPA
Result:Same
For some reason, the java version is always at 1.6, no matter what I do.

---

### Post by regice9 on 2013-02-03
I believe that it is the plugin that is screwed up. Even though I have tested it on many sites, it is always the plugin, not the JRE that doesn't work. IcedTea java plugin didn't work.

---

### Post by rburkartjo on 2013-02-03
i am having the same problem with chrome. however chromium is working fine.

---

### Post by joco1500 on 2013-02-03
Just download Chromium. its the same thing just its blue.

it has a app store and you can sign into gmail.

---

### Post by rburkartjo on 2013-02-03
joco yes but on my end java isnt crashing in chromium as it is in chrome thus preventing lots of links from loading.

---

### Post by regice9 on 2013-02-03
> **joco1500 said:**
> Just download Chromium. its the same thing just its blue.

it has a app store and you can sign into gmail.
Thank you for this advice. Tried Chromium and it works like a charm.

---

