---
title: "[SOLVED] Can i delete the contents of /var/cache/apt"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-04
i have a download of 800 MiB of contetns in /var/cache/apt

I have no room for my data in my ubuntu partition.

Could i delete the contents of my /var/cache/apt

---

### Post by kpkeerthi on 2008-06-04
Yes you can. The safest way to do is with this command
```
sudo aptitude clean
```

---

### Post by sayakb on 2008-06-04
For more clean-ups :)
```
sudo apt-get install localepurge
sudo localepurge
sudo apt-get autoremove
sudo apt-get autoclean
```

---

### Post by rraj.be on 2008-06-04
```
sudo apt-get install localepurge
sudo localepurge
sudo apt-get autoremove
sudo apt-get autoclean
```

what does each of these commands do.

Could you explain a bit more.

---

### Post by sayakb on 2008-06-04
**autoclean**: removes all stored archives in your cache for packages that can not be downloaded anymore (thus packages that are no longer in the repo or that have a newer version in the repo).
[B]
clean[/B]: removes all stored archives in your cache.

**autoremove**: a whole different thing, this option makes apt look for packages that are installed as dependency of an already uninstalled package and removes them. This is used to clean up unused dependencies that remain on your system.

**localepurge**: [http://www.debianadmin.com/remove-unnecessary-files-in-debian-and-ubuntu-using-localepurge.html](http://www.debianadmin.com/remove-unnecessary-files-in-debian-and-ubuntu-using-localepurge.html)

---

### Post by kpkeerthi on 2008-06-04
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

