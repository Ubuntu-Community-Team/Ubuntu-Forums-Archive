---
title: "Syntax for using debconf-utils &amp; debconf-get-selections"
date: 2011-05-05
forum: Programming Talk
---

### Post by Elludium_Q-36 on 2011-05-05
I have tried repeatedly to get help with backing up and restoring a system where I would do a fresh install.
[http://ubuntuforums.org/search.php?do=finduser&u=814041&starteronly=1](http://ubuntuforums.org/search.php?do=finduser&u=814041&starteronly=1)

The reason is I unfortunately added 10.04 packages from a CD to an 8.04 system.  I was unable to downgrade via force version.

I know now that I need to run the cdromupgrade script from an alternative install CD :o/

The desktop box is offline, on "sneakernet" so I hoped to preserve settings, configurations, data & package .deb files.  I have backed up /home/ and those files that would copy in /etc/ as root. (some refused to copy, even for root).

I brought debconf-utils to the box and tried to use debconf-get-selections but;
```

debconf-get-selections --help

```
only yielded some configuration data to the Konsole terminal screen.

Any help would be appreciated =;

---

### Post by Elludium_Q-36 on 2011-05-07
Nobody?

I'm surprised someone didn't comment just to increase their thread/post count.

I can't be the only one who has had to reinstall a system...

---

### Post by Elludium_Q-36 on 2011-05-19
Nobody?

---

### Post by mringer on 2011-09-04
Please try:

dpkg --get-selections > ~/my-packages

I hope this helps.

---

