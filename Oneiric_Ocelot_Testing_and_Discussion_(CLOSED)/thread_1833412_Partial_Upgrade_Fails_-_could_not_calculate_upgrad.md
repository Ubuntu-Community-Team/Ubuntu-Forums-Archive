---
title: "Partial Upgrade Fails - could not calculate upgrade"
date: 2011-08-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by pt123 on 2011-08-26
I am trying out Oneiric alpha 3 there are many packages to updated, when it gives me the option of partial upgrade, it fails.
With the following message - could not calculate upgrade.

I have attached a screenshot. 
And in update manager many of the packages are unelectable.

---

### Post by garvinrick4 on 2011-08-26
I would say to install "aptitude and then use it to upgrade" when using Alpha's and Beta's
Just my personal opinion. Stay away from any partial upgrades see sticky:
```
sudo apt-get install aptitude
```
```
sudo aptitude update; sudo aptitude safe-upgrade
```

---

### Post by cariboo on 2011-08-26
Either do as garvinrick4 said and update via the command line, or install synaptic, and use that to do your updates, instead of using, as ranch hand calls it update-mangler. :)

---

### Post by pt123 on 2011-08-26
Thanks I went and installed synaptic to install video codecs as it went into a bug loop after failing to install the video codecs, after doing it's video codec search.

---

### Post by garvinrick4 on 2011-08-26
Try to install ubuntu-restricted-extras
let it install all codecs, java, flash, gstreamers and such. Will install microsoft fonts if do not
want just tell it no, if do want toggle with tab to say yes.
Simple way to install audio, video.
##Use whatever works to install you are in Alpha sometimes lucky to get to X, oneiric is still unstable.

---

