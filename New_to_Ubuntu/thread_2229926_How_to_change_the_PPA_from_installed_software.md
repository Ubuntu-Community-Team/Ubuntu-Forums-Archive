---
title: "How to change the PPA from installed software"
date: 2014-06-16
forum: New to Ubuntu
---

### Post by czgirb on 2014-06-16
After I do some checking in USC, I found DeaDBeeF was installed via [http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu](http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu)
And I wish to used ppa:starws-box/deadbeef-player ... since it was believed to update my software
1. Is there anybody can tell me is it allowed to change the PPA directly?
2. if it cannot, would you mind to do a favor for guiding me how to change the PPA?
Thank you

---

### Post by grumblebum2 on 2014-06-16
Both ppas only contain DeaDBeeF packages with the **starws-box/deadbeef-player** ppa
having later versions so don't see any reason why you can't just add the starws-box/deadbeef-player ppa
and run **sudo apt-get update**
You could remove the alexey-smirnov/deadbeef ppa as it hasn't been updated for over two years.

PS If your going to use ppas use synaptic for a clearer picture.

---

