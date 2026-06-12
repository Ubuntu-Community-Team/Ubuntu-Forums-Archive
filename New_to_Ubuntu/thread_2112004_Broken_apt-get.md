---
title: "Broken apt-get?"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by skyler544 on 2013-02-03
I've seen a few similar threads with very similar problems, and I've been able to fix the problem with this terminal command: sudo rm /var/lib/apt/lists/* -vf (I found this out looking at those similar threads, but my issue seems a bit more extensive.)

I'm getting ahead of myself though; I installed Kubuntu on a 25 gb partition, and filled it up by going haywire in the "Software Center." Then, I got an error message saying that some packages could not be installed. I figured out that there was no room left on the partition, uninstalled a bunch of stuff, and now it works again. However, every time I reboot, I have to go into the terminal and type the previously mentioned command and then type: sudo apt-get update in order to install any packages. Understandably this is frustrating, so my question is, why do I have to fix this every time I want to use the package manager? the specific error is this:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_quantal-updates_multiverse_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.

I'd appreciate being able to use Aptitude without fixing it every single time I reboot. Anyone have any idea what is causing this?

---

### Post by sudodus on 2013-02-03
This list (or if you with script) was posted by ***oldfred*** in an Ubuntu Forum thread recently. It may help you repair your system.

```

# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

```
Use ***sudo*** if you run individual command lines manually, as well as if you run it as a bash script.

---

### Post by skyler544 on 2013-02-03
I'm working on it, the wifi at my school is so slow that it keeps crashing halfway through and I have to restart to go on

---

### Post by skyler544 on 2013-02-03
That seems to have done it. Thanks a lot!

---

### Post by sudodus on 2013-02-04
> **skyler544 said:**
> That seems to have done it. Thanks a lot!
You are welcome :-)

---

