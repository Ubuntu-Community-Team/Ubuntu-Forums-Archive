---
title: "Yet Another Problem"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Dragonlaw on 2008-05-08
Sigh, today is not a good day. I got this problem too - 

E: Could not open lock file /var/lib/dpkg/lock - open (2 No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: _cache->open() failed, please report.

What do I do?

---

### Post by oliviacond on 2008-05-08
```

sudo apt-get

```
type your password and press enter.

---

### Post by Dragonlaw on 2008-05-08
Done already.

justin@justin-desktop:~$ sudo apt-get
apt 0.7.9ubuntu17 for i386 compiled on Apr 22 2008 15:19:47
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove all automatic unused packages
   purge - Remove and purge packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.

What do I do now?

---

### Post by Dragonlaw on 2008-05-08
I've been looking around and mine isn't like the normal ones.

E: Could not open lock file /var/lib/dpkg/lock - open (**2 No such file or directory**)

Which is a little different from permission denied?

HELP!

---

### Post by Michael.Godawski on 2008-05-08
What are you trying to do? After which action or command this error occur?

---

### Post by joselin on 2008-05-08
The issue here is that you did an apt-get whatever without sudo before it. 

Read your output:
```
 E: Unable to lock the administration directory (/var/lib/dpkg/), **are you root?**
```

Execute it typing sudo before, and the problem will be solved.

Regards

---

### Post by Dragonlaw on 2008-05-08
How do I read the output?

---

### Post by Dragonlaw on 2008-05-08
> **joselin said:**
> The issue here is that you did an apt-get whatever without sudo before it. 

Read your output:
```
 E: Unable to lock the administration directory (/var/lib/dpkg/), **are you root?**
```

Execute it typing sudo before, and the problem will be solved.

Regards

I typed sudo apt-get update and that was what I got.

---

### Post by joselin on 2008-05-08
> **Dragonlaw said:**
> How do I read the output?

The first output of your command were posted in you first post. Just do the following to try and see if it works fine:
```
sudo apt-get update
```

---

### Post by Cappy on 2008-05-08
Try this:
```
sudo touch /var/lib/dpkg/lock
```

---

### Post by Dragonlaw on 2008-05-08
I had to restart my computer and I got not boot it up graphically. It went straight to the terminal and it said 

"Server uthorization directory (daemon/ServAuthDir) is set to /var/lib/dgm but this does not exist. Please Correct GDM configuration and restart GDM.

---

