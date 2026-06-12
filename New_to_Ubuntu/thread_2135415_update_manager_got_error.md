---
title: "update manager got error"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by chitragurung on 2013-04-14
I have error of update manager. In the menu bar I have red stop button when I click on it to run the update manager I got the following. so cant run update

could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

---

### Post by ikt on 2013-04-14
Heya, 

This is a problem with one of the configuration files that apt uses to update.

It seems like someone had a similar problem and they solved it here:

[http://ubuntuforums.org/showthread.php?t=1983220&p=11958892&viewfull=1#post11958892](http://ubuntuforums.org/showthread.php?t=1983220&p=11958892&viewfull=1#post11958892)

---

### Post by chitragurung on 2013-04-15
it does not help me

---

### Post by grahammechanical on 2013-04-15
Here is something that you can try

```
sudo rm /var/lib/apt/lists/* -rf
``` followed by
```
sudo apt-get update
```

The first command removes/deletes (rm) all the files (scripts) in the lists folder. The second command replaces those files. I have had this problem before. About a year ago. It was the same file as I remember. That was how I solved it. That script has a blank line at the top of the page. When Update Manager reads that script it looks for a header at the top of the page and all it sees is a blank line and Update Manager falls over. It is by comparing scripts of what is installed on our computer with those in the repositories that Update Manager identifies what packages can be updated.

Regards.

---

### Post by raja.genupula on 2013-04-15
open your terminal and type this 

```
sudo rm -rf /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_multiverse  _i18n_Translation-en
sudo apt-get update
```

---

### Post by joneez on 2013-05-13
Thank you grahammechanical! This worked for me.

My error was - "E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened."

---

