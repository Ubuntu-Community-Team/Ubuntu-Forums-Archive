---
title: "Other application using package manager (constantly)"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by smudge85 on 2013-03-02
Hi,

I'm running Kubuntu 12.10. I constantly get the error message (Muon Package Manager) that another application is using the packagesystem. When I run 'sudo dpkg --configure -a' the message goes away for a while, but the next day it's back.

Is there a better solution than the above command to see if there's a different problem that's causing these conflicts?

---

### Post by zrdc28 on 2013-03-02
Normally when you get that you have an apt-get open in terminal or synaptic open. If you close the other one it will work for you.
If that don't work for you!

sudo apt-get install -f      
sudo dpkg --configure -a

sudo apt-get purge muon
sudo apt-get install muon

This will clear the apt lists and will fix your problem!

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update

---

### Post by ubudog on 2013-03-02
Post the output of:
```

ps ax | grep apt

```

---

