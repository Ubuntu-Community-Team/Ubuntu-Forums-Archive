---
title: "Update manager broken"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by fractalman on 2013-01-04
I am using 12.04 with gnome classic,  when i open update manager i get a list of updates to install but when i click install it does nothing, no download or anything.  i have tried through unity as well but nothing happens,  any ideas? i have had a good google but nothing showed up

---

### Post by Pjotr123 on 2013-01-04
Use the terminal for it to see what goes wrong:
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

### Post by fractalman on 2013-01-04
well i tried sudo apt-get update, but that made no difference, i don't want to upgrade my distro but thanks for the reply, 

 I tried using sudo update-manager from the terminal and that worked so i have now installed the updates.

i have a similar issue with synaptic, when launched from a menu it doesn't open but when launched from a terminal as root it is fine.  guess it must be the 12.04 way of doing things, i was on 11.04 before and only switched a couple of days ago so i'm still getting used to how things work on 12.04.

---

### Post by Pjotr123 on 2013-01-04
> **fractalman said:**
> i don't want to upgrade my distro

With the command I gave you, you won't upgrade it to 12.10.... For that, there's another command needed: "do-release-upgrade".

"apt-get upgrade" will apply ordinary updates, and "apt-get dist-upgrade" will apply fundamental system updates like a new kernel (or to be more precise: a minor newer kernel version with only bugfixes, not a major newer kernel version). :)

---

