---
title: "how do you install google earth 4.3"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by Foxfire on 2008-08-29
how do I do this

---

### Post by hubie on 2008-08-29
[https://help.ubuntu.com/community/GoogleEarth#Installation]("https://help.ubuntu.com/community/GoogleEarth#Installation")

Don't forget to read all the way down to the Troubleshooting section.

---

### Post by drs305 on 2008-08-29
For Hardy:

If you haven't enabled it, add the Medibuntu repository from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"):

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```
[B]
Edited[/B]: I just tried and googleearth metapackage kept 4.2 on my machine. If it wants to install 4.2 (check at 'apply' for what it's about to install), change the app to *googleearth-4.3*:

Install Google Earth (this is a metapackage, no version number required. current version 4.3+):
```

sudo apt-get update && sudo apt-get install googleearth
```

---

