---
title: "Upgrade ubuntu server 11.04 to 12.04"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by hkl@hkl.no on 2013-02-12
Ladys and gents

I want to upgrade a 11.04 server to 12.04, trying the do-release-upgrade command, but the respnse is: "no upgrades available"

Any ideas?

br

hkl

---

### Post by fdrake on 2013-02-12
> **hkl@hkl.no said:**
> Ladys and gents

I want to upgrade a 11.04 server to 12.04, trying the do-release-upgrade command, but the respnse is: "no upgrades available"

Any ideas?

br

hkl
what about ```


do-release-upgrade -d
```
at the final question press enter

---

### Post by hkl@hkl.no on 2013-02-12
Tried that, same result:

No new release found.

---

### Post by fdrake on 2013-02-12
```

sudo apt-get install update-manager-core
sudo do-release-upgrade -d

```
any luck?

---

### Post by hkl@hkl.no on 2013-02-12
> **fdrake said:**
> ```

sudo apt-get install update-manager-core
sudo do-release-upgrade -d

```
any luck?

Tried
Update manager is already the newest version
same result.

hkl

---

### Post by arpanaut on 2013-02-12
11.04 is End of Life...
Please see: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

For best support get to a LTS and try to stay there especially for Server.

---

### Post by hkl@hkl.no on 2013-02-12
> **arpanaut said:**
> 11.04 is End of Life...
Please see: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

For best support get to a LTS and try to stay there especially for Server.

Thanks for Your responce

I tried the suggestions in EOLupgrades, but get the same results!
I did beleive that 11.04 was an LTS though, realise that it is EOL, but instead of having to reinstall everything, an Upgrade would be Nice, anyone got any ideas here?

hkl

---

### Post by d4m1r on 2013-02-12
Try the method outlined in this thread:

[http://ubuntuforums.org/showthread.php?t=2115240](http://ubuntuforums.org/showthread.php?t=2115240)

---

