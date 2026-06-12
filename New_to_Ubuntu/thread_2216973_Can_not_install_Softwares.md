---
title: "Can not install Softwares"
date: 2014-04-14
forum: New to Ubuntu
---

### Post by bukhari2 on 2014-04-14
my Os is update but I'm unable to install  many softwares e.g chromium,wine etc 
 for chromium I get this msg

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
The following packages have unmet dependencies:

chromium-browser: Depends: libgcc1 (>= 1:4.1.1) but 1:4.8.1-10ubuntu8 is to be installed
                  Depends: libnss3 (>= 2:3.14.3) but 2:3.15.4-0ubuntu0.13.10.2 is to be installed
                  Depends: libudev1 (>= 183) but 204-0ubuntu18 is to be installed
                  Depends: libx11-6 (>= 2:1.4.99.1) but 2:1.6.1-1ubuntu1 is to be installed
                  Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.4.4-1 is to be installed
                  Depends: libxdamage1 (>= 1:1.1) but 1:1.1.4-1ubuntu1 is to be installed
                  Depends: libxi6 (>= 2:1.2.99.4) but 2:1.7.1.901-1ubuntu1 is to be installed
                  Depends: libxss1 but it is not going to be installed
                  Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-1ubuntu1 is to be installed

---

### Post by deadflowr on 2014-04-15
If on 12.04, open the update manager program and run it's check function.
Or if on 13.10 simply open software updater and let it do it's thing
(Software updater runs the check function by default)
If any updates are listed, install them.

If your updater is set to allow an offer to install a newer version of ubuntu(it will say upgrade), you can ignore that.

Now see if you can install those packages you want.

---

### Post by monkeybrain20122 on 2014-04-15
I was about to say maybe you have added a ppa and then disabled/removed it but the errors don't make sense: the "to be installed" packages do have versions >= packages required!

Try 

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install chromium-browser
```

---

### Post by ian-weisser on 2014-04-15
> **bukhari2 said:**
> 
chromium-browser: Depends: libgcc1 (>= 1:4.1.1) but 1:4.8.1-10ubuntu8 is to be installed
                  Depends: libnss3 (>= 2:3.14.3) but 2:3.15.4-0ubuntu0.13.10.2 is to be installed
                  Depends: libudev1 (>= 183) but 204-0ubuntu18 is to be installed
                  Depends: libx11-6 (>= 2:1.4.99.1) but 2:1.6.1-1ubuntu1 is to be installed
                  Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.4.4-1 is to be installed
                  Depends: libxdamage1 (>= 1:1.1) but 1:1.1.4-1ubuntu1 is to be installed
                  Depends: libxi6 (>= 2:1.2.99.4) but 2:1.7.1.901-1ubuntu1 is to be installed
[COLOR=#ff0000]                   Depends: libxss1 but it is not going to be installed[/COLOR]
                  Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-1ubuntu1 is to be installed

The specific problem is that you have a package installed (or selected for install) that conflicts with libxss1.
Usually, this means you installed the conflicting package from a PPA or third-party repository.

It's not enough to merely disable the PPA; the conflicting package (and everything that depends upon it) must be uninstalled from your system.

You *don't* have an 'updated OS.' You cannot install updates, including security updates, until you repair this problem.

We could help you more if you post the *entire* terminal session of an apt-get upgrade or install that results in this error.

---

