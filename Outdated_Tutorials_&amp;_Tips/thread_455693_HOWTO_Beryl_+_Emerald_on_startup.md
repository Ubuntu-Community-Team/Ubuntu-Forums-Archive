---
title: "HOWTO: Beryl + Emerald on startup"
date: 2007-05-26
forum: Outdated Tutorials &amp; Tips
---

### Post by tmasboa on 2007-05-26
This is for people who which Compiz/Desktop Effects works (with XGL session) but beryl gives white screen. I'm also assuming you've tried the Beryl XGL tutuorial on the Beryl site.

Afterwards, you should be able to use Beryl and Emerald.

Okay so you have beryl installed. If you haven't done so, go and do a 
sudo synaptic
and find all the beryl packages and do a CTRL-E, set them to version .9xxx...

The later versions aren't compatible.
Okay now try this: 
beryl-xgl --use-copy

That should give you beryl but no Emerald

Try this:
emerald --replace

Just "emerald" won't kill the old manager.


Okay now go System -> Preferences -> Sessions

Add one called Beryl with "beryl-xgl --use-copy" and
"emerald --replace"

Try logging out and in.

Now, if you're like me, you want to fool around with the options. For Beryl just use the Beryl Settings Manager under Applications -> System Tools.

For emerald, you can find it under System -> Preferences -> Emerald Theme Manager but when you change the theme it won't actually change. You need to add a launcher to the panel and put in "emerald --replace". (you can try reload also)

Press that button to restart emerald whenever you change a setting.

Sorry this turned out to be more of a little guide than a full tutorial. Have fun!

---

### Post by ukripper on 2007-06-09
> **tmasboa said:**
> This is for people who which Compiz/Desktop Effects works (with XGL session) but beryl gives white screen. I'm also assuming you've tried the Beryl XGL tutuorial on the Beryl site.

Afterwards, you should be able to use Beryl and Emerald.

Okay so you have beryl installed. If you haven't done so, go and do a 
sudo synaptic
and find all the beryl packages and do a CTRL-E, set them to version .9xxx...

The later versions aren't compatible.
Okay now try this: 
beryl-xgl --use-copy

That should give you beryl but no Emerald

Try this:
emerald --replace

Just "emerald" won't kill the old manager.


Okay now go System -> Preferences -> Sessions

Add one called Beryl with "beryl-xgl --use-copy" and
"emerald --replace"

Try logging out and in.

Now, if you're like me, you want to fool around with the options. For Beryl just use the Beryl Settings Manager under Applications -> System Tools.

For emerald, you can find it under System -> Preferences -> Emerald Theme Manager but when you change the theme it won't actually change. You need to add a launcher to the panel and put in "emerald --replace". (you can try reload also)

Press that button to restart emerald whenever you change a setting.

Sorry this turned out to be more of a little guide than a full tutorial. Have fun!

I prefer using shell script to start beryl at startup as it give me more flexibiilty  in time delay  as I have also setup conky with 5 sec difference between them so everything gets started within 10 sec after login screen makes my vaio look snappiest ever

---

