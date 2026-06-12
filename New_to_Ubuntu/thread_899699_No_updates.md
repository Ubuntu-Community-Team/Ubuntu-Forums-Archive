---
title: "No updates"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by omi291 on 2008-08-24
Hey everybody, I've been on ubuntu for a while (and loving it :)), but I noticed that I haven't gotten any new updates in well over a week. I'm assuming something is wrong, but could anybody point me in the right direction?

---

### Post by drs305 on 2008-08-24
> **omi291 said:**
> Hey everybody, I've been on ubuntu for a while (and loving it :)), but I noticed that I haven't gotten any new updates in well over a week. I'm assuming something is wrong, but could anybody point me in the right direction?

First, you could quickly run the following to see if you get anything, including error messages:
```
sudo apt-get update
sudo apt-get upgrade
```

You could then go to synaptic and make sure under Settings, Repositories, Updates you have at least one of the items ticked.

You could also try changing servers, Synaptic, Settings, Repositories, Download from, Other>  (maybe try Select Best Server).

---

### Post by mkvnmtr on 2008-08-24
I did not get any updates this week either. I just thought there were no updates. It checks when I turn on the power in the morning and I check before I shut it of at night.

---

