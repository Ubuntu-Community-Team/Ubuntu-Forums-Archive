---
title: "Have just reinstalled to get 12.10 but am having problems with the panel"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by hamstermoon on 2012-12-02
Before on Precise I had a top panel looking like this:

[Link]("https://picasaweb.google.com/lh/photo/RW0B3kKaGReN5PHHffZZkdMTjNZETYmyPJy0liipFm0?feat=directlink")

Now on Quantal it looks like this:

[URL="https://picasaweb.google.com/lh/photo/sFchIvhb99E_GHNPCFuewtMTjNZETYmyPJy0liipFm0?feat=directlink"]Link
[/URL]
The 'window buttons' plug-in doesn't seem to want to space everything over to the right like whatever the equivalent in Precise did before.

Suggestions?

---

### Post by Dennis N on 2012-12-02
This post might offer a solution, although from 2009:

[http://ubuntuforums.org/showpost.php?p=8077662&postcount=2](http://ubuntuforums.org/showpost.php?p=8077662&postcount=2)

---

### Post by Toz on 2012-12-02
You're missing an expanding separator between the Window Buttons plugin and the Indicator Plugin. If a separator exists there, set it to expanding. Otherwise add a new one and set it expanding.

If you happen to have an expanding separator at the end after the Action Plugins, remove it.

To get to the configuration dialog, right-click the panel. select  Panel->Panel Preferences and look on the Items tab.

---

