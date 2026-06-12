---
title: "Thunderbird 8.0 crashes after update of parts"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by il pepe on 2011-11-28
My thunderbird 8.0 doesn't start anymore, i directly get a bug screen.

I did the safe mode startup, same problem....

Any ideas where i can find the logs? or where i can get more info about the problem?

---

### Post by khelben1979 on 2011-11-28
You say it crashes after update. Can you describe a bit more in detail how that happened?

In **/home/[your user]/mozilla-thunderbird/** you got the configuration files which is stored for your mail client. If a configuration file have become corrupted or if there's an addon in the extension directory which causes this problem, it's good to know how it looked like when it was working OK.

---

### Post by il pepe on 2011-11-28
i ran sudo apt-get update/upgrade this morning and now TB isn't working anymore.

i did a reinstall and nothing changed, as expected.

So indeed it porbably is in the config files. But where do i start to look? how do i know what files are corrupted?

---

### Post by khelben1979 on 2011-11-28
What version of Ubuntu are you using and does it have any addons installed? 

I would downgrade to a previous version of Thunderbird to not over-complicate things for you. 
Thunderbird 3.x can be found over [here]("http://www.mozilla.org/en-US/thunderbird/all-older.html") at the Mozilla.org website.

[SIZE="1"]B.t.w. the prefence file for Thunderbird is named prefs.js and can be moved to another catalog, 
just to see if it starts up, but you will loose all your settings if it ain't put back there. Not recommended.[/SIZE]

---

### Post by il pepe on 2011-11-28
hey,
i solved it. Rather than stepping a couple of versions down(8->3) although relative), i upgrade thunderbird with ppa:mozillateam/thunderbird-next
to thunderbird-next. and that also solved the problem.

Kind regards

---

### Post by Frogs Hair on 2011-11-28
I encountered an add-on problem , but it was only a theme and TBird restarted with the default theme .

---

