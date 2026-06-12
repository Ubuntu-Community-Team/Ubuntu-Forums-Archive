---
title: "Update problem 12.04"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by sarum on 2012-06-04
Hi. A month ago I upgraded to the new LTS and thought it time to update things. There are loads of updates and when I clicked on 'update' a warning message came up saying that some updates are from unauthenticated places. The message has no alternative options other than 'details' and 'close'.
Details seems to be a list of whats not OK, but I've always kept up to date and am quite happy to go ahead - after all Ubuntu would hardly offer updates that are harmful. So how can update please? There seems to be no way to either accept or reject. Thanks for any help with this..........sarum

---

### Post by drs305 on 2012-06-04
To take the conservative approach, first open Software Sources. You can do this from the Ubuntu Software Center's menu: Edit, Software Sources.

You can check the "Ubuntu Software" and "Updates" threads just to see what you have selected, but the one you probably want to check is the "Other Software". You can note the ones that are enabled and then untick them all. Close Software Center/Software Sources and reload the repository list and run the upgrade as you normally do.

All of the enabled sources should be acceptable and update normally.

The second way of doing this is to verify the "Other Software" tab entries to make sure all the ones enabled are ones you trust. If that is the case, close Software Sources/Ubuntu Software Center, and run:
```

sudo apt-get update
sudo apt-get upgrade
```
If you still aren't allowed to upgrade, untick the repositories in "Other Software" one by one, trying to update after each.

---

### Post by sarum on 2012-06-05
Thanks drs305 for your help. I'm an LTS guy, and the change has been dramatic, but I'll stick with it for the next 5 years.
I'll do what you suggest in the morning - thanks again.....sarum

---

### Post by sarum on 2012-06-06
Once again my thanks; I'm all uptodate.
Sarum

---

