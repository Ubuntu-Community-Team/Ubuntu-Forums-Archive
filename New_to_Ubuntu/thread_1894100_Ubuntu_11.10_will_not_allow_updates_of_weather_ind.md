---
title: "Ubuntu 11.10 will not allow updates of weather indicator"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by bob brazie on 2011-12-11
Ubuntu 11.10

Indicator-Weather [https://launchpad.net/weather-indicator](https://launchpad.net/weather-indicator)

I have the correct PPA entry in the software sources.

I installed it from the software center after entrying the ppa. It still shows as installed in the software center.

There is an up date listed in the update manager but when I try to install it I get a message saying <The action would require the installation of packages from not authenticated sources> and will not install or upgrade it.

What and why>

Thanks in advance. Bob.

---

### Post by ExileAmongYou on 2011-12-11
You're missing the "signing key" for that PPA, so the update system can't check that the packages you're downloading are genuine. You should be able to fix it by running:
```
sudo apt-add-repository ppa:weather-indicator-team/ppa
``` 
in the terminal, which should automatically import the key for you (you'll see a few lines come up that say things like "GPG import successful".

However, to get this to work, you may have to delete the existing ppa you have in Software Sources. This won't uninstall the package, by the way.

If you're adding ppa's in the future, sudo apt-add-repository is a good command to remember, it makes the whole process a lot easier by handling the keys for you.

---

### Post by bob brazie on 2011-12-11
Do I need to re-boot or do something because after entering what you mentioned into a terminal and then trying to install the update I get the same message and cannot install it.

Please see screen shot.

Thanks, Bob.

---

### Post by linuxman94 on 2011-12-11
Remove the line you added in software sources manually and run 
```
sudo apt-get update
```

---

### Post by bob brazie on 2011-12-11
I did remove them before using the method you mentioned above. They were there again after running the command.

I just tried to remove them, after highlighting them I click remove and nothing happens. ?

---

### Post by bob brazie on 2011-12-11
After running the command this error at the bottom was noted.

Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6A9653F936FD5529
bob@bob-HP:~$

---

### Post by bob brazie on 2011-12-11
However the up date did install this time around??

---

