---
title: "I cannot compile Firefox!"
date: 2011-07-31
forum: Packaging and Compiling Programs
---

### Post by stamatiou on 2011-07-31
Hello!
I would like to uninstall Firefox and compile him myself so the browser runs faster but I have an error! I have already added the firefox repository. Here are the commands that I have executed:

```

sudo apt-get build-dep firefox
apt-get source firefox
dpkg-source -x firefox_5.0+build1+nobinonly-0ubuntu0.11.04.2.dsc

```
but with the following command I take:
```
gpgv: Signature made Thu 23 Jun 2011 02:10:32 AM EEST using DSA key ID AA97FD59
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./firefox_5.0+build1+nobinonly-0ubuntu0.11.04.2.dsc
dpkg-source: info: extracting firefox in firefox-5.0+build1+nobinonly
dpkg-source: info: unpacking firefox_5.0+build1+nobinonly.orig.tar.gz
dpkg-source: info: applying firefox_5.0+build1+nobinonly-0ubuntu0.11.04.2.diff.gz
dpkg-source: info: upstream files that have been modified: 
 firefox-5.0+build1+nobinonly/mozilla-release-5.0+build1-source.tar.bz2.cdbs-config_list

```
What is the problem?

---

### Post by lovinglinux on 2011-07-31
I haven't compiled Firefox in a while, because these days it already comes with optimizations and the performance gain doesn't worth the trouble. Last time I tried, I've got only 10% improvement.

Anyway, if you want to try, see my tutorial at [http://www.webgapps.org/tutorials/firefox/advanced/compiling-from-source](http://www.webgapps.org/tutorials/firefox/advanced/compiling-from-source)

On my site you will also find other tutorials to improve FF performance.

---

