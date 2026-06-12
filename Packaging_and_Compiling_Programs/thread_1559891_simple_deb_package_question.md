---
title: "simple deb package question"
date: 2010-08-24
forum: Packaging and Compiling Programs
---

### Post by chaemil on 2010-08-24
hi. is any solution how to install the files in the /home/username/.appname/ ?

how can i do that if i dont know the username?
i want to user have the full access to the some app files...

---

### Post by SevenMachines on 2010-08-24
Generally programs do things like this when the user runs them. Something like,

if some config file exists in users directory then use it, if not then copy some default files across from the system directories.

---

