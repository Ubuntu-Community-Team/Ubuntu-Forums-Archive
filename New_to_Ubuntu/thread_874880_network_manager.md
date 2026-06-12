---
title: "network manager"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-07-30
ah i kinda uninstalled network manager and now i cant get it installed again...could someone please give me step by step instructions on how to install it again...thanks in advanced.

---

### Post by JoneYee on 2008-07-30
Yoiu might find this useful:
[http://ubuntuforums.org/showthread.php?t=375546](http://ubuntuforums.org/showthread.php?t=375546)

---

### Post by luisfcup on 2008-07-30
Since you don't have a connection to the internet after uninstalling the network-manager package, the easiest thing to do is to install it again from the Ubuntu cd/dvd. So, go to System->Administration->Software sources: in the first separator you will see a check box "Cdrom with Ubuntu 8.04" make sure the box is checked and close the windows. Now wither install the package "network-manager" with the synaptic package manager or simply open up the console and type: ```
sudo apt-get update
sudo apt-get install network-manager
```
And all should be fine.

---

