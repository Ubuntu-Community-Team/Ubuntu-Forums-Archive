---
title: "HOWTO: Install Flock on Ubuntu Hardy"
date: 2008-08-08
forum: Outdated Tutorials &amp; Tips
---

### Post by danielesalatti on 2008-08-08
Ok, this is my first tutorial here... :)

Hoping to do a useful thing I have set up a repository for Ubuntu Hardy and I have loaded in it some packages from the [GetDeb]("http://www.getdeb.net/") project. One of this packages is the [Flock Browser]("http://flock.com/").

In this tutorial I'll explain how to set up your Hardy box to use my repository and how to install Flock.

To begin with, we need to edit the /etc/apt/sources.list file, so open a shell and issue the following command:

```
sudo nano -w /etc/apt/sources.list
```

Now append the following three lines at the end of the file:

```
# SN's Repository
2. deb http://www.salatti.net/repo/ hardy-salatti main contrib non-free
3. deb-src http://www.salatti.net/repo/ hardy-salatti main contrib non-free
```

Save (CTRL + O) and close the file (CTRL + X).

Update APT sources by issuing the command:

```
sudo apt-get update
```

And install Flock:

```
sudo apt-get install flock
```

Hope this helped...

---

### Post by shamanphenix on 2008-11-05
Flock, boswar, Google gadget & Vuze.
Thanks a lot, dude. :-)

---

### Post by justinlawrence on 2009-04-20
i dont think this repository works anymore

---

### Post by danielesalatti on 2009-04-20
No, it's not working at the moment.

---

### Post by tmsbrdrs on 2009-07-12
Since the repos don't work now, an alternate method for installing Flock is simply to download and install the .deb package for your particular version of Ubuntu from the following link.

[http://www.getdeb.net/search.php?keywords=flock](http://www.getdeb.net/search.php?keywords=flock)

If there's a getdeb repo available, that information would be greatly appreciated.

---

### Post by tmsbrdrs on 2009-07-24
[https://launchpad.net/~fta/+archive/ppa](https://launchpad.net/~fta/+archive/ppa)

I'm testing this repo currently, looks like it's working just fine and it does have Flock for Hardy as well as Intrepid.

---

