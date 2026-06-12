---
title: "error message"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by DGZDGZ on 2008-11-02
Every time i download a package from the package manager i receive the following error message:

E: openjdk-6-jre-headless: subprocess post-installation script returned error exit status 1
E: openjdk-6-jre: dependency problems - leaving unconfigured
E: icedtea-gcjwebplugin: dependency problems - leaving unconfigured

I've tried : sudo apt-get install -f, but that didn't work.

Can somebody please let me know what it means and how to fix it.

---

### Post by Sand Lee on 2008-11-03
I'm guessing xubuntu has synaptic by default? Try opening it and going to Edit -> Fix Broken Packages

---

### Post by sayems on 2008-11-03
Go to Synaptic and click on "custom filters then click on "broken" and that should tell you what's causing it

---

### Post by DGZDGZ on 2008-11-03
hi there, and thanks for responding.

When i filter for boken packages nothing shows up? however, i still can't open the pages which i've downloaded since this eror message started to appear.

---

