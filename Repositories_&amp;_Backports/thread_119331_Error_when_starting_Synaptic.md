---
title: "Error when starting Synaptic"
date: 2006-01-19
forum: Repositories &amp; Backports
---

### Post by dwerf on 2006-01-19
Hi all,

When I start Synaptic, I'm getting the error stated below. I get it every time I want to upgrade or install anything. It seems that applications are installed and upgraded just fine anyways.

W: Couldn't stat source package list file: apt-build/main Packages (/var/lib/apt/lists/_var_cache_apt-build_repository_dists_apt-build_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list file: apt-build/main Packages (/var/lib/apt/lists/_var_cache_apt-build_repository_dists_apt-build_main_binary-i386_Packages) - stat (2 No such file or directory)

I'd really like to know what the error means, what I've done wrong (must have been me) and how to fix this. Thanx!

---

### Post by Luke771 on 2006-01-19
I don't really know if it's actually the same error I got some time ago, anyways I fixed it by reinstalling the repositories. To do that, open synaptic and choose repositories from the settings menu, click the "add" button, check ALL the checkboxes and then click OK, and yes, and so on untill it's done and synaptic restarts; then do the same thing all over again but selecting "ubuntu security updates" from the drop-down menu in the box where you check the checkboxes, click all the OK's and yesses of the case an then repeat the operation one last time selecting the last line (ubuntu updates) from the drop down menu, and again, OK, yes, etc.
Let me know it that worked.

---

### Post by Syco54645 on 2006-01-20
I had this error.  I think it is because the repositories that were there are dead.  Just check the sticky on this forum about the repository list and use that.  If you notice at the bottom, it was recently edited.

-Syco54645

---

