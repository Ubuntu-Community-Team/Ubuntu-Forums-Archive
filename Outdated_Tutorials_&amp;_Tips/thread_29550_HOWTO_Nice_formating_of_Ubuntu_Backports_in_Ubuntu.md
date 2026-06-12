---
title: "HOWTO: Nice formating of Ubuntu Backports in Ubuntu Update Manager"
date: 2005-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Nis on 2005-04-24
Attached is a new aptsources.py that nicely formats the listing for the Ubuntu Backports project in the repostories listing in Ubuntu Update Manager.  Do the following below to get it working.

1) Download the attached file to ~ (your home directory)

2) Perform the following commands in a terminal
```

tar -xfvj ~/aptsources.py.tar.bz2
sudo cp /usr/share/update-manager/python/aptsources.py /usr/share/update-manager/python/aptsources.py.old
sudo cp ~/aptsources.py /usr/share/update-manager/python/aptsources.py

```
3) Start Ubuntu Update Manager and click Preferences to see if the Backports listing is nicely formated.  If you haven't added the Backports project to your repository list then you won't see anything but you now can through the add button.

---

### Post by XplOzIOn on 2005-04-24
[QUOTE=Nis]Attached is a new aptsources.py that nicely formats the listing for the Ubuntu Backports project in the repostories listing in Ubuntu Update Manager.  Do the following below to get it working.

1) Download the attached file to ~ (your home directory)

2) Perform the following commands in a terminal
```

tar -xfvj ~/aptsources.py.tar.bz2
sudo cp /usr/share/update-manager/python/aptsources.py /usr/share/update-manager/python/aptsources.py.old
sudo cp ~/aptsources.py /usr/share/update-manager/python/aptsources.py

```
3) Start Ubuntu Update Manager and click Preferences to see if the Backports listing is nicely formated.  If you haven't added the Backports project to your repository list then you won't see anything but you now can through the add button.[/QUOTE]
 Thanks! it worked nicely done!

---

