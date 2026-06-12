---
title: "Adobe Flash Player Stuck!"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by jesseinthabane on 2012-06-17
Whenever the menu to enable something for adobe flash player pops up, I can't click anything at all. Sites such as chatroulette, omegle, etc... What's the problem? I even removed, then installed it, still nothing. Please Help!

---

### Post by gnusci on 2012-06-17
This post my be useful to you

[http://askubuntu.com/questions/89932/flash-not-working-in-firefox](http://askubuntu.com/questions/89932/flash-not-working-in-firefox)

---

### Post by daslinkard on 2012-06-17
I had a similar issue....I was able to resolve it by the following:

```
sudo apt-get purge adobe-flashplugin
```Then reinstalling with:

```
sudo apt-get install flashplugin-nonfree
```Good Luck!

---

