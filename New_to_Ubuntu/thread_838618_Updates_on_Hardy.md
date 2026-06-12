---
title: "Updates on Hardy"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by jrlii on 2008-06-23
I don't seem to have been getting upgrade notices since I upgraded to Hardy.

Most notably, I haven't be offered the upgrade to Firefox 3.0, from 3.0 beta 5 - which works, but hangs more often than I'd like.

I've run the update manager several times and have received an indication that I am up to date, even though Firefox, if nothing else is decidedly dated.

I am connected to the internet only through dialup via gnomePPP, if that makes a difference.

Thanks!

---

### Post by Rocket2DMn on 2008-06-23
Try going to System->Administration->Software Sources and making sure you have the top 4 checkboxes enabled.  You may also consider using a different mirror.  Then go to the Updates tab and check the top 2 boxes (hardy-security and hardy-updates) - I believe FF3 is in the updates repository.  Close the window, then run
```
sudo apt-get update
sudo apt-get upgrade
```
the update command shouldn't be needed if you allow the sources.list file to update when you close the Software Sources window, but I included it for good measure.

---

### Post by jrlii on 2008-06-23
Thanks! after reseting the sources, update manager wanted to download 14 hours worth of updates. . . (on dialup)

---

