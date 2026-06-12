---
title: "Difference in Software Update File Sizes (Software Center vs Terminal)"
date: 2014-06-28
forum: New to Ubuntu
---

### Post by Digitalscribbler on 2014-06-28
Hello-
I've noticed that when I run software updates through the Terminal the total file size is different than if I update through the GUI-based Software Center tool. For example, the update in the Software Center showed a file size total of 61.2MB, but when using the Terminal to run an update it showed the file size total as 29.8MB - nearly 50% smaller. Assuming that the Terminal represents just a different way to update the software, why is the file size when doing updates through the Terminal so much smaller in size? Thanks.

---

### Post by Vladlenin5000 on 2014-06-28
It depends on whether you're using "apt-get upgrade" or "apt-get dist-upgrade".

[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool#Update.2C_upgrade_and_dist-upgrade](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool#Update.2C_upgrade_and_dist-upgrade)

---

### Post by bapoumba on 2014-06-28
> **Vladlenin5000 said:**
> It depends on whether you're using "apt-get upgrade" or "apt-get dist-upgrade".

[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool#Update.2C_upgrade_and_dist-upgrade](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool#Update.2C_upgrade_and_dist-upgrade)

Hmm ? I believe software-updater upgrades, so apt-get upgrade should be either equal or bigger, due to phased updates.

To the OP, could you please give specific examples ?

---

### Post by grahammechanical on 2014-06-28
It is my opinion that Update Manager includes in the total packages that will be installed but are not yet available for downloads. These are packages that apt-get would show as being held back. I also think it includes in the total packages that have already been downloaded but not installed because they depend upon other packages that are yet to be downloaded.

I run the development branch and I update every day and with Update Manager it sometimes seems as if the same packages are being downloaded twice.

Another thing, Ubuntu now receives Phased Updates. In the past updated packages were pushed out to all users. If one of these packages had a serious bug then all users got the buggy package and all suffered as a result. Now updates are pushed to 10% of users and if those 10% do not complain, then the update gets pushed out to another 10% and so on until all 100% of users get the updated package. This is works with Update Manager and it may be counting the full total of all packages. But apt-get does work with phased updates. It just downloads everything that is ready.

[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

Regards.

Regards.

---

### Post by deadflowr on 2014-06-28
> **bapoumba said:**
> Hmm ? I believe software-updater upgrades, so apt-get upgrade should be either equal or bigger, due to phased updates.

To the OP, could you please give specific examples ?

Terminal output would be helpful, in it's entirety.
apt-get upgrade would most likely tell you if any package upgrades are being held back.
It should at least output the line with Installed removed Upgraded Not upgraded
Like so
```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
If packages are being held, they'd be listed under the not upgraded listing.
This is usually shown right above the part which states how much is being updated, which is usually above the "do you want to update yes or no"

---

### Post by Digitalscribbler on 2014-07-03
Sincere apologies for not responding sooner (an unexpected work commitment kept me away). Anyway, thanks very much for your feedback. Definitely helps. Special thanks to grahammechanical (gave me a better understanding of the bigger picture of how these updates are pushed out) and deadflowr (yes, the terminal does show which have been held back, etc.). Thanks again!

---

