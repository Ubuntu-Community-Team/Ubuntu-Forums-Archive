---
title: "libgtkmm-2.4-dev unmet dependencies"
date: 2010-10-28
forum: Programming Talk
---

### Post by jazzgossen on 2010-10-28
I'm using Ubuntu 10.04 and want to do some gtkmm programming. However, I can't install libgtkmm-2.4-dev because of unmet dependencies.

Here's what happens:
```
$ sudo apt-get install libglibmm-2.4-dev 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libglibmm-2.4-dev: Depends: libglibmm-2.4-1c2a (= 2.24.1-1) but 2.24.2-0ubuntu1 is to be installed
E: Broken packages

```

Does anybody know of a way around this?

And by the way, libglibmm-2.4-1c2a is already installed.

---

### Post by MadCow108 on 2010-10-28
are you using a ppa?
10.10 only ships version 2.20 but yours wants to install 2.24.

If not try:
sudo apt-get install -f
to try fix the dependencies

---

### Post by jazzgossen on 2010-10-29
Thanks for your reply. 

I disabled all PPAs, updated and ran "apt-get install -f", but the situation remained. However, running "aptitude install libgtkmm-2.4-dev" worked. 

For the record, what aptitude did was to downgrade libcairomm-1.0-1,libglibmm-2.4-1c2a and libpangomm-1.4-1.

---

### Post by worksofcraft on 2010-10-29
I'm glad you found a way round it :) I had similar problem a while back but it sort of fixed itself when I upgraded my Linux to 10.4 I had to reinstall loads of stuff anyway and suddenly it was all working and I have no idea why. Thus I couldn't offer you any practical suggestions.

---

