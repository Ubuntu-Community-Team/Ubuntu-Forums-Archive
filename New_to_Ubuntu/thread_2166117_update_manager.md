---
title: "update manager"
date: 2013-08-07
forum: New to Ubuntu
---

### Post by expatcm2 on 2013-08-07
My update manager installs everything except the following.  
gimp-help-zh-cn: Depends: gimp-help-common (= 1:2.8-0precise8~ppa) but 1:2.8-0precise16~ppa is installed

How do I clear this off?

If I use sudo apt-get -f install it runs but then terminates with 

Errors were encountered while processing:
 gimp-help-zh-cn
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by bluefrog on 2013-08-08
try downgrading to 1:2.8-0precise8~ppa

---

### Post by expatcm2 on 2013-08-08
How should I do that?

---

### Post by SlugSlug on 2013-08-08
not sure why you'd have mismatched versions.

I'd

```
sudo apt-get remove ---purge gimp && sudo apt-get autoremove && sudo apt-get install gimp
```

---

### Post by Jonathan Precise on 2013-08-08
[SIZE=2][FONT=verdana]Try:
 
```
sudo apt-get install synaptic && synaptic-pkexec
```

This will install and launch a package manager called synaptic.Then it will ask for your password. Put it in, then press enter. Then search for gimp-help-common in the quick filter. Select gimp-help-common. Then in the menu bar click Package --> Force Version.  [COLOR=#000000][FONT=verdana]1:2.8-0precise8~ppa[/FONT][/COLOR][COLOR=#000000]. Click apply if necessary. This should fix your problem.[/COLOR][/FONT][/SIZE]

---

### Post by Dennis N on 2013-08-08
Investigate packages here:

[https://launchpad.net/~otto-kesselgulasch/+archive/gimp/+packages](https://launchpad.net/~otto-kesselgulasch/+archive/gimp/+packages)

In particular,

**gimp-help - 1:2.8-0precise16~ppa **

appears to offer the desired language, and was published aug 6 2013.

**gimp-help-zh-cn_2.8-0precise16~ppa_all.deb (27.8 MiB)**

remove gimp-help-* packages that are currently installed first.

---

