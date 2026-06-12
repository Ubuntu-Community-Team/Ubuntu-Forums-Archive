---
title: "What now? Dependency question"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by raker t on 2008-07-01
I went to install a Deb package, Python-uniconverter, and got the message about dependency not satisfied, Python-central. I went and got it, a small file, and installed it (Fiesty). It said that the package install was completed.

But now, when I go to install the uniconverter, I still get the same message about Python-central. Twice I've installed the dependency, still the same.

Any ideas? Thanks for any help.

---

### Post by InfinityCircuit on 2008-07-01
If these are deb packages which you are installing, then you should be able to run "apt-get install -f" and it should bring in the necessary dependencies.

---

### Post by nowshining on 2008-07-01
also apt-get install -f removes files if they are broken. to make sure it installs what is needed use 

```
sudo apt-get -f install
```

:)

ur pw won't show as you type

to install the deb anyway

in terminal

```
sudo dpkg -i --force- nameofpackage/pathtopackage
```

make sure ther is a space between "force-" and the package name or else it won't work.

---

