---
title: "Getting my package accepted into multiverse"
date: 2010-02-25
forum: Packaging and Compiling Programs
---

### Post by yanom on 2010-02-25
I packaged a free-as-in-beer program, seen [here]("http://ubuntuforums.org/showthread.php?t=1415482&highlight=fusion"). I read about the sections of the repos (universe, multiverse, etc.) and it only fits in multiverse. How can I get it included in the main Ubuntu repository/repositories?

---

### Post by SevenMachines on 2010-02-26
see [Requesting New Packages]("https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages#Requesting%20a%20new%20package%20for%20Ubuntu"), if you have or are going to package it yourself you should look at the [REVU Process]("https://wiki.ubuntu.com/MOTU/Packages/REVU") to get a sponsor to check it out and then bring it into the repository

---

### Post by yanom on 2010-02-26
ahh, thx

---

### Post by yanom on 2010-02-28
Now... I can't figure out how to upload my package to REVU. I already went through the "add your PGP key to Launchpad" proccess.

---

### Post by SevenMachines on 2010-03-01
Have you [logged into revu]("http://revu.ubuntuwire.com/launchpad_login.py") at least once?
If so then you should be able to upload with dput
$dput revu <my_new_package>_source.changes

---

