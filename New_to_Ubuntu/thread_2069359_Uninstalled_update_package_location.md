---
title: "Uninstalled update package location"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by fractalman on 2012-10-10
i recently upgrade skype to ver 4 but i can't get on with it, it's really glitchy and the layout is horrible, microsoft have left there mark yet again by ruining everything they create or touch......

i rolled back to ver 2.2 beta as i found that version to be the least glitchy, i found a deb and installed it, works fine...

when i run update manager it is offering me an upgrade for skype, to update to ver 4,   i have unchecked the box so i don't update but it says it has still downloaded the package ready for a later time,   

Where can i find this uninstalled update package so i can remove it from my pc?

---

### Post by DuckHook on 2012-10-10
```
sudo apt-get clean
```

There really is no harm in leaving it on your computer. I know, leaving it there offends my sense of tidiness too.

---

### Post by Gone fishing on 2012-10-10
sudo apt-get clean will remove all the files in /var/cache/apt/archives including the offending package.

---

