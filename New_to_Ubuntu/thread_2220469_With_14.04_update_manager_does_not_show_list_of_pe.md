---
title: "With 14.04 update manager does not show list of pending packages, only settings"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by jtl2 on 2014-04-28
After having installed Ubuntu 14.04 (64 bit) I noticed that the update manager does not show any list of pending packages, only the settings of the manager (package sources, settings for updating etc.).

So I do not know what packages are to be updated, if any.

My installation was almost clean. I did a new install but in 12.04 I used Synaptic to produce a list of software and applied it to speed installation of those programs. So that might be a source of trouble.

But perhaps I should change some settings or install some piece of software?

Thank you!

---

### Post by jdeca57 on 2014-04-28
Ubuntu software center has the 'history' button showing all updated packages. So when in doubt, look there.

---

### Post by jtl2 on 2014-04-28
What I should ask perhaps is whether the default behaviour of the update manager has been changed between U 12.04 and 14.04. I do not mind if the idea nowadays is not to show the list of packages that are going to be updated. I may have missed the announcement about that.

---

### Post by ibjsb4 on 2014-04-28
I do not have update manager installed, just synaptic, so I'm not sure about the display.  You have synaptic installed, is it showing updates?

---

### Post by jtl2 on 2014-04-28
Yes, I have synaptic, and at the moment it does not show updates. I have been doing 

**sudo apt-get update && sudo apt-get upgrade**

every day.

---

### Post by ibjsb4 on 2014-04-28
If synaptic shows no updates, then doing a terminal update (and update manager) should also show nothing.  Synaptic is just a GUI for apt-get.

---

### Post by jtl2 on 2014-04-28
I think I now realize what happened. I was using "Software-properties-gtk" while thinking it was "Gnome apt update manager".
It was the latter that I should have been using.

Thank you for your attention & support. ;)

---

### Post by ibjsb4 on 2014-04-28
Welcome :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

