---
title: "Compiling programs from debian sources"
date: 2007-04-19
forum: Programming Talk
---

### Post by ashrack on 2007-04-19
I just put the Debians SID DEB-SRC repo in sources.list. 
Afterwards I did:
```
apt-get source kaffeine
```
which downloaded kaffeine 0.8.4 source. Which has more extended subtitle support compared to the version in Feisty.
Then I changed the changelog and checked if debian/rules and debian/control are ok.
afterwards I did:
```
dpkg-source -b kaffeine-0.8.4
pbuilder build kaffeine*ashrack*.dsc
```
the package compiled fine and after I installed it it also works great.
But the problem is that if I type
```
apt-get autoremove
```
it will remove Kaffeine.
What must I do so this does not happen?

ps. Just tried downloading the UBUNTU SOURCE's KAFFEINE and then compile it and the same thing happens.

---

