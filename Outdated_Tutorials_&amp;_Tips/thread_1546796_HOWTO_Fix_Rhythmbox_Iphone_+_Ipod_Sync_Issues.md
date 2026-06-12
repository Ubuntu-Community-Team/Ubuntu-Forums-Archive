---
title: "HOWTO: Fix Rhythmbox Iphone + Ipod Sync Issues"
date: 2010-08-05
forum: Outdated Tutorials &amp; Tips
---

### Post by tekkidd on 2010-08-05
Hi, I am an owner of an iPhone 3G 4.0 and i use Rhythmbox to manage my music on it. Recently ive had a problem with music transfers where i would transfer the music but then the music would not show up on the iPhone, but after plugging into a mac or pc and starting itunes, only then would the iPhone see it. I finnaly found a fix and here it is. 

1. Go to your home folder (Places>Home Folder)

2. Press CTRL+H 

3. Navigate to .gconf>apps>rhythmbox>state>ipod

4. Delete %gconf.xml file (Dont worry, it will be recreated the next time you start rhythmbox

5. Restart rhythmbox (if you have it running)

And there you go, music will now be recognized!

NOTE: If you suffer from the issue again (I have) just repeat the process

The Geeky Way (Command Line):

In the terminal type in:

```
cd   /home/<username>/.gconf/apps/rhythmbox/state/ipod/
```

AND

[CODE]rm -r %gconf.xml[CODE]

---

### Post by spegru on 2011-01-02
Hi what version of ubuntu & rhythmbox and which fimware inside the iphone?
Have you found a way of syncing the phone to rhytmbox without going back to itunes?
thx

---

