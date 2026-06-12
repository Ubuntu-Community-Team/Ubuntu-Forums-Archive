---
title: "[Python} os.system(&quot;sudo apt-get install&quot;)"
date: 2011-04-03
forum: Programming Talk
---

### Post by ki4jgt on 2011-04-03
When I install a program to the user's computer from python, will it go through the install process:

Tell how far the installation has gone, like a normal sudo apt-get install

and then continue running my program

-or-

will it continue running my program as soon as the command is issued to the system?

---

### Post by ki4jgt on 2011-04-03
Just tried this using Putty (Have been wanting to install forever) It runs all the way through the install process before continuing to run the program. Thanks guys :-)

---

### Post by cgroza on 2011-04-03
Maybe you should take a look at the *apt-get API*.

---

### Post by kostkon on 2011-04-03
Actually apt has a python library (python-apt) and a dbus interface (use d-feet to examine it).

Thus, you don't need to use os.system to call apt-get.

---

