---
title: "Unable to install automake and autoconf"
date: 2006-01-12
forum: Programming Talk
---

### Post by rrova on 2006-01-12
I've just received the latest Ubuntu install CD and am trying to set up a development environment. However, the command "sudo apt-get install automake autoconf" returns the following:

Reading package lists... Done
Building dependency tree... Done
Package autoconf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package autoconf has no installation candidate

What's up with that?

---

### Post by toojays on 2006-01-12
Have you tried doing "apt-get update" to refresh your package list?

---

### Post by rrova on 2006-01-12
I have done the update several times, but no packages are showing up for automake and autoconf.

---

### Post by rrova on 2006-01-12
The problem seems to be almost resolved. I had to hack the /etc/apt/sources.list which had incorrect entries for the package info (it first points to the install CD). I uncommented the internet sources and fixed each one individually by checking the proper paths to the repositories. There must be a newer sources.list somewhere that I can download?

---

### Post by rrova on 2006-01-12
OK, happy camper. The instructions at [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php) fixed this problem for me. The trick they suggest is:

"Apparently, some people have been experiencing errors even after following this tutorial. There's some weird glitch where residual info hangs out and gives you a GPG signature error. If that's the case, do this:

Back up the sources.list you got from this tutorial with this command: sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

Then edit the sources.list by typing sudo gedit /etc/apt/sources.list and delete everything.

sudo apt-get update with your empty repositories list.

Finally, sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list sudo apt-get update"

---

