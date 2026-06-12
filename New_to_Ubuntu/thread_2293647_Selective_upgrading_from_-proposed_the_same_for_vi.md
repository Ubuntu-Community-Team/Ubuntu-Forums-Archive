---
title: "Selective upgrading from -proposed the same for vivid?"
date: 2015-09-06
forum: New to Ubuntu
---

### Post by lambdafox on 2015-09-06
I want to try to install wine 1.6 from -proposed, and only update from -proposed any dependencies for wine.

I am looking at: [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

After using synaptic to enable -proposed, the wiki says to create a text file in /etc/apt/preferences.d called proposed-updates and set its contents to:

```
Package: *
Pin: release a=trusty-proposed
Pin-Priority: 400

```

I assume that I replace the word trusty with vivid? Is this the correct procedure for Xubuntu vivid?  

Also, after doing that, the wiki is unclear, but I am assuming I will use Synaptic force version to install the -proposed package.  Is that correct?

---

### Post by monkeybrain20122 on 2015-09-06
why don't you install from the wine ppa? [https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa)

Don't update from proposed. You will screw up your system somehow.

---

### Post by lambdafox on 2015-09-06
> **monkeybrain20122 said:**
> why don't you install from the wine ppa? [https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa)

Don't update from proposed. You will screw up your system somehow.

[This is what led me to my question.]("http://ubuntuforums.org/showthread.php?t=2292761")

---

### Post by ian-weisser on 2015-09-06
Using packages in -proposed is discouraged, unless you are an active tester. -proposed is for testing.
When testing is complete, the package will migrate to -updates

An experienced tester seems unlikely to ask your question, so I strongly discourage you from going the route you propose. Down that road you may encounter great frustration and, eventually, a reinstall.

---

### Post by lambdafox on 2015-09-07
> **ian-weisser said:**
> Using packages in -proposed is discouraged, unless you are an active tester. -proposed is for testing.
When testing is complete, the package will migrate to -updates

An experienced tester seems unlikely to ask your question, so I strongly discourage you from going the route you propose. Down that road you may encounter great frustration and, eventually, a reinstall.

Thank you for your advice.  I am a noobie to linux and ubuntu; so, perhaps I shall just wait until the proposed hits the regular repo

---

