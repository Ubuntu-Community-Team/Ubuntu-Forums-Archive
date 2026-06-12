---
title: "Howto: Fix RSSOwl Internal Browser"
date: 2006-02-13
forum: Outdated Tutorials &amp; Tips
---

### Post by PhogHawk on 2006-02-13
Hey everyone! I just decided to switch RSS Readers from Blam! (which is very simple and good, but lacks folder support) to RSSOwl (which has.... everything). I looked through some of my feeds and was incredibly dissappointed with the lack of HTML support. So I did some research and fixed it. Here's how:

1: Install mozilla-browser
```
sudo apt-get install mozilla-browser
```

2: Change run.sh in your rssowl directory to:
```
#!/bin/sh
export MOZILLA_FIVE_HOME=/usr/lib/mozilla/
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:${MOZILLA_FIVE_HOME}:${LD_LIBRARY_PATH}
java -Xmx134217728 -Djava.library.path=. -jar rssowl.jar
```

3: In RSSOwl, go to Tools-->Preferences-->View

4: In the "Misc" section, check "View newstext in browser"

5: Go to Tools-->Preferences-->Browser

6: In the "Please enter path to executable" box, enter the path to your exectuable (lol). This is the app that you want to use to open in an external browser, so I wanted to use firefox. My path was "/usr/bin/firefox" but that's not default. With a new system, it could be "/usr/bin/mozilla-firefox"

7: At the bottom, check "use external browser"

8: You're Done!

---

### Post by hamid.nyc on 2007-02-26
Thanks PhogHawk, your howto worked like a charm. I love RSSOwl, and the Ubuntu community!!!:)

---

### Post by JesterGr on 2007-06-10
Thnx sooooo much! been trying that a couple of hours!

Million thanx again !!!

---

