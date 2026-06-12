---
title: "Installing from Software Centre says check internet connexion"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by Herr Regenbogen on 2012-03-11
trying to install restricted extras package but the software centre thinks i have no internet connexion. this only happens with some installations i was able to install vlc and a few others with no problem. ive included a screenshot.

---

### Post by Old_Grey_Wolf on 2012-03-11
The screenshot is missing.

That problem may be a problem with an entry in the sources.list file. Execute the following command in a terminal and post the results.

```
cat /etc/apt/sources.list
```

---

### Post by winh8r on 2012-03-11
It is possible that the mirror you are using has been offline and therefore your software centre is unable to connect to it.

To check this, open the software centre

Click on Edit > Software Sources

then click on the drop down menu where it says "Download from"

If you click on the "other" entry

you can allow the software centre to check all the available mirrors for you and recommend the best one for you.

Once it has run the check, select the one you want, click "select server" 

then you can close the software centre.

If you open a terminal and enter 

```
sudo apt-get update
```

you can see the real time progress of the update process and which mirror you are connecting to .

Hope this helps you.

---

