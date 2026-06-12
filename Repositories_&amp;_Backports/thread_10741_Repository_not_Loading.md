---
title: "Repository not Loading"
date: 2005-01-10
forum: Repositories &amp; Backports
---

### Post by jahn on 2005-01-10
Whenever I load Synaptic I get this message:

"Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com)
warty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_main_binary-i386_Packages) -stat (2 no such file or directory)"

Any ideas? Thanks so much!

---

### Post by rubycon on 2005-01-11
Have you updated the repository pressing the Reload button?

---

### Post by byourg on 2005-01-11
I had the same problem. What I found out was if your on a home network with a windose computer, shut down the windose computer, restart the router and modem, open your web browser and type in the url for the repository and see if it comes up. If it does start the spm program, hit reload and it works. Hope this helps.

---

### Post by jahn on 2005-01-11
Thanks to both!

I had to hit Reload, then Mark All Upgrades, before Applying the changes.

I could've sworn I tried to press Reload, but I guess not.  My bad!

Thanks for the help, this message board is among the best I've seen.

---

