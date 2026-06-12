---
title: "Help: I Think I have Broken Something"
date: 2006-01-27
forum: Repositories &amp; Backports
---

### Post by edwin11 on 2006-01-27
Hi,

I am using Ubuntu Breezy.

Now, i was having some problems with amarok 1.3.8, so after googling and reading around, i figure that i have to upgrade kdelib to 3.5 (previously was 3.4.3), and libtag to 1.4 (previously was 1.3).

So first, i added the source
```
deb http://kubuntu.org/packages/kde35 breezy main
```

and did an upgrade on all upgradable packages.

Next, i added the source
```
deb http://sg.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
```

and installed libtag1c2a (1.4-3).

i should have known that this second step of getting packages from dapper was not a good idea. There were many dependencies resolved (packages removed, packages added, packages upgraded) given the supposed simple nature of libtag.

but alas, i have done that, and i think my system is not stable. For one, now when i go to Preferences -> Repositories in Synaptic, it does some reloading, but never takes me to the repositories screen. i have to modify sources.list to add and remove repositories.

What can i do now to roll back the wrong things that i did?



TIA and Regards,

---

