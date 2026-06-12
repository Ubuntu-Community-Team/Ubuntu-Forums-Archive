---
title: "Unistalling Software not from Software Center"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by TheMTtakeover on 2012-04-17
I installed a deb package and I opened it and it installed through the software center, but I didn't actually download it through the software center. How do I uninstall these programs?

---

### Post by daslinkard on 2012-04-17
To remove the package (we will call mplayer) you would do the following sudo command from the terminal

```
sudo apt-get remove mplayer
```

If you want to remove the package and all configuration files, you would type:

```
sudo apt-get --purge remove mplayer
```

---

### Post by critin on 2012-04-17
That's the way it's supposed to work.  SC installs .deb
To uninstall, go back to SC and click on INSTALLED SOFTWARE.  Find the one you want to delete and click on REMOVE.

---

