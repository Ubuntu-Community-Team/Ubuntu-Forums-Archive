---
title: "server: does apt-get now have an install log like software center?"
date: 2011-07-04
forum: Repositories &amp; Backports
---

### Post by WOTHed on 2011-07-04
Hi the software centre has a nice log of what you installed that isn't in a mess of other automaticly installed packages.

If I am using apt-get in ubuntu server is there a log of just the files I installed in the same nice type of list?

It't nice to see just the packages you installed last week for example.
Would be a little nicer still if the list hid or mark deps rather than being in massive list with all the stuff you typed on the apt-get command line.

---

### Post by Enigmapond on 2011-07-04
I don't know if it does, however I would assume it did. There is an easy way to get a list which can also be used to do a mirror-install on a second machine.

```
dpkg --get-selections > ~/my-packages
```

This puts a file in your home folder, "my-packages"

Also just for fun and OP unrelated...update all the repos on a new install and run:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

This will install all your programmes to another machine...

Cheers!

---

