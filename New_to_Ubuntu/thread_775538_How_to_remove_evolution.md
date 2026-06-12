---
title: "How to remove evolution?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by ipatec on 2008-04-30
I don't like Evolution, I rather prefer Thunderbird so I want to remove it. I tried to remove it from synaptic but there are to many files referig to it. I removed just that one called "evolution" and after reinstalling it all my configuration files were there.... :(
I want to completely remove it...how can I do this?
Thanks!

---

### Post by Sef on 2008-04-30
You really can't without it messing up the machine.  What I do is go to System > Preferences > Main Menu > Internet and uncheck it.  That way it don't appear in the menu.

---

### Post by hermes0710 on 2008-04-30
> **ipatec said:**
> I don't like Evolution, I rather prefer Thunderbird so I want to remove it. I tried to remove it from synaptic but there are to many files referig to it. I removed just that one called "evolution" and after reinstalling it all my configuration files were there.... :(
I want to completely remove it...how can I do this?
Thanks!


In order to remove the configuration files:

```
sudo dpkg --purge evolution
``` (with evolution being installed in order to be removed)

---

