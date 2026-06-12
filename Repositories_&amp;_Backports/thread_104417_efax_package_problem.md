---
title: "efax package problem"
date: 2005-12-16
forum: Repositories &amp; Backports
---

### Post by sitara on 2005-12-16
I'm not sure if this is the right place to post this, but I had a problem installing efax and I thought it might save someone else some time.

I am running Kubuntu Breezy Badger with KDE 3.5.

When I installed efax, I got an error message saying that 'paperconf' could not be found.

It seems that the default /etc/efax.rc has 'page=paperconf' set. There are two solutions: 1) Install libpaper-utils from Synaptic or 2) Change 'page=paperconf' to 'page = A4' or 'page=letter'...

I guess that libpaper-utils should be a dependency for efax?

---

