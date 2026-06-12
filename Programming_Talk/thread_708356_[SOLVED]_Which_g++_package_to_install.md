---
title: "[SOLVED] Which g++ package to install?"
date: 2008-02-26
forum: Programming Talk
---

### Post by Ryozanpaku Tiger on 2008-02-26
Dear all,

I would like to have g++ compiler on my Ubuntu 7.10. I see that I already have gcc preinstalled. Which g++ package should I choose in the Synaptic Package Manager? I guess I don't need to install *build-essential* package, as I have gcc already. So which g++ package is needed?

Thank you!

---

### Post by aks44 on 2008-02-26
You should be installing build-essential, this will save you from numerous headaches.

See also the sticky FAQ, there is useful information there.

---

### Post by Ryozanpaku Tiger on 2008-02-26
Thank you!

One more question please. I have the following version of gcc installed now: gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

Will build-essential overwrite it with a newer version or not?

---

### Post by aks44 on 2008-02-26
TBH I don't really know, as I'm using Feisty not Gutsy.

Afterthought: [this page]("http://packages.ubuntu.com/gutsy/devel/build-essential") indicates that Gutsy's build-essential requires gcc >= 4:4.1.1. So I guess your version will be kept (better triple-check it yourself anyway).

---

### Post by Ryozanpaku Tiger on 2008-02-26
Thank you once again! I will check it.

---

### Post by Ryozanpaku Tiger on 2008-03-10
Update: I installed *build-essential* package, the pre-installed version of g++ compiler was kept.

---

