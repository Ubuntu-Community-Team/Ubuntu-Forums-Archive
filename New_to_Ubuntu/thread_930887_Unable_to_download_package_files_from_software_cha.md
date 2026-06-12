---
title: "Unable to download package files from software channels"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by neutron2008 on 2008-09-26
I'm unable to download package files from software channels using any of the given programs viz. "Synaptic", "Aptitude", "Add/Remove". When i start downloading a package a downloading window is viewed and then within 5-10 minutes it says that packages could not be downloaded. What should i do to rectify this problem?

---

### Post by SunnyRabbiera on 2008-09-26
you may want to check out synaptic located under system> administration listed as synaptic package manager.
Synaptic is like a more advanced version of add/ remove, there is a button in it marked refresh to help refresh your package lists.

---

### Post by hyper_ch on 2008-09-26
run it from the command line, that will give you more clues:

```

sudo apt-get install PACKAGENAME

```

---

