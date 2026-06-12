---
title: "Pre Hardy upgrade / clean install questions"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by CheeseEatingBulldog on 2008-04-25
Hello all, 
A few questions before I b0rk my install this weekend, I have been using Ubuntu for some time now and out of the 6 upgrades I have attempted on the various releases in the past, I would say 2 worked and 4 completely bricked my system, so the first question is what are people's perception of the upgrade this time around?

My second question is more based on the fact that the upgrade will not work. I have some stuff in my queue in Azureus, and if I reinstall I will lose that, is there anyway of saving the current Azureus queue in its current state?

I am leaning towards a clean install as lessons learned from past (like waiting brazillion hours for it to upgrade and then reboot into a shower of errors), but would like some opinions. If I upgrade it will go via the alt-cd as downloading off the repos just after a release is out is pretty much like watching paint dry, so what say ye?

---

### Post by overdrank on 2008-04-25
> **CheeseEatingBulldog said:**
> Hello all, 
A few questions before I b0rk my install this weekend, I have been using Ubuntu for some time now and out of the 6 upgrades I have attempted on the various releases in the past, I would say 2 worked and 4 completely bricked my system, so the first question is what are people's perception of the upgrade this time around?

My second question is more based on the fact that the upgrade will not work. I have some stuff in my queue in Azureus, and if I reinstall I will lose that, is there anyway of saving the current Azureus queue in its current state?

I am leaning towards a clean install as lessons learned from past (like waiting brazillion hours for it to upgrade and then reboot into a shower of errors), but would like some opinions. If I upgrade it will go via the alt-cd as downloading off the repos just after a release is out is pretty much like watching paint dry, so what say ye?

Hi and in my experience the upgrading has not worked for me. I have not tried to upgrade to Hardy so I cannot comment on that. I have always ended doing a clean install. But there are users that have had success. Good luck!

---

### Post by mivo on 2008-04-25
The distro upgrades seem to be a bit problematic at times, so I would also recommend the clean install. If you have a separate home partition, the files on there won't be touched, unless you check "format" for that partition during installation (you need to assign a mount point (/home) to it, however). Your BitTorrent client saves its data there. If you do not have a separate home partition, you can backup everything in your /home, or at least the files you wish to keep and later put back, i.e. Azureus's configuration and data files.

It's generally a good strategy to have a ~10 partition for /, a bit for swap, and the rest for /home. If nothing else, it makes reinstalling much more convenient. :)

---

