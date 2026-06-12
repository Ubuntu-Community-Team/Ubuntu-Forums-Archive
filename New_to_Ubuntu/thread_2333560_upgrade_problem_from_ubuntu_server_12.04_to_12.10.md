---
title: "upgrade problem from ubuntu server 12.04 to 12.10"
date: 2016-08-11
forum: New to Ubuntu
---

### Post by los91 on 2016-08-11
I have installed ubuntu server 12.04 from a LiveCD adn it works fine with me. Now I need to upgrade to ubuntu 13.10. It is mentioned that I cant upgrade directly so I have to upgrade to 12.10, then 13.02, then 13.10 ([https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)). In the process of upgrading to 12.10, I am able to "apt-get update, but "do-release-upgrade" yields an error:


Checking for a new Ubuntu release Err Upgrade tool signature
404 Not Found [IP: 91.189.88.161 80]
Err Upgrade tool
404 Not Found [IP: 91.189.88.161 80]
Fetched 0 B in 0s (0 B/s)
WARNING:root:file 'quantal.tar.gz.gpg' missing Failed to fetch Fetching the upgrade failed. There may be a network problem.


I changed the sources.list and was able again to do the update but yet the same error is appearing. 
How could I solve this problem?

---

### Post by CatKiller on 2016-08-11
All of the versions you are hoping to pass through, and the version you plan on stopping on, are no longer supported. It would be much better to do a fresh install of at least 14.04 LTS, which will be supported until 2019, or 16.04 LTS, which will be supported until 2021.

Note that you could have upgraded directly from 12.04 to 14.04, since they are both Long Term Support releases.

---

### Post by grahammechanical on 2016-08-11
Have you installed update-manager-core?

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

This is where you are

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards

---

