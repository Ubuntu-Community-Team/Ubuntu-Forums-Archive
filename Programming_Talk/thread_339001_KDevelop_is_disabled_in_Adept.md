---
title: "KDevelop is disabled in Adept"
date: 2007-01-15
forum: Programming Talk
---

### Post by glue on 2007-01-15
KDevelop is disabled and Eclipse isn't even available. I look at getting Eclipse from packages.ubuntu.com but it has lots of dependencies and the dependencies have lots of dependencies, etc. There doesn't seem to be any end to it. I try getting Emacs21 but it says there's a conflict. 

How do I get a C++ IDE?

---

### Post by jblebrun on 2007-01-15
> **glue said:**
> KDevelop is disabled and Eclipse isn't even available. I look at getting Eclipse from packages.ubuntu.com but it has lots of dependencies and the dependencies have lots of dependencies, etc. There doesn't seem to be any end to it. I try getting Emacs21 but it says there's a conflict. 

How do I get a C++ IDE?

What do you mean that it's disabled? Did you try closing adept, and opening a terminal window, and typing:

```

aptitude install kdevelop

```

---

### Post by glue on 2007-01-16
I mean in the Add/Remove programs app KDevelop is gray and cannot be selected. Unless this means something else, I would describe it as disabled. The command you suggested didn't do anything either.

---

### Post by tpg on 2007-01-16
If the previous command didn't work, then this probably won't either, but try running

```

sudo apt-get update
sudo apt-get install kdevelop

```
and see what happens. If it doesn't work, read the error message, and see if it gives any hints.

---

### Post by glue on 2007-01-16
sudo apt-get update returned a list of a whole bunch of files then said:

"Fetched 3B in 5s (1B/s)
Reading package lists... Done"

Nothing looked like any errors.


sudo apt-get install kdevelop returns

"Reading package lists... Done
Building dependency tree
Reading state information... Done
Package kdevelop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  kdesdk-scripts
E: Package kdevelop has no installation candidate"

---

### Post by mat087 on 2007-01-16
Hum... it seems like the exact same problem that I've got three days ago.

I tried apt-get check, clean and autoclean. None of these worked.

Then I tried : rm /var/cache/apt/archives/* (If you deleted the "partial" directory, just recreate it)
Then I did apt-get update, and everything goes back normally.


Did it help you ?


Mathieu

---

### Post by glue on 2007-01-17
Actually, it was a problem with some of my repositories being disabled in the repository manager. I enabled them then tried the commands that were suggested and they work.

---

