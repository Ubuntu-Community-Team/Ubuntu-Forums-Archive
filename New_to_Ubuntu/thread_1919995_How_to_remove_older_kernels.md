---
title: "How to remove older kernels"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by Virajs on 2012-02-03
Hey guys, :o
I'm using ubuntu 10.10 still. Since I have installed 10.10 I have done several updates for 10.10 and now the problem is there are three kernels showing up as I see during booting. I don't know how to remove the older kernels. Need some help from you.. :o

---

### Post by mikewhatever on 2012-02-04
Check out this thread -> [http://ubuntuforums.org/showthread.php?t=1916641](http://ubuntuforums.org/showthread.php?t=1916641).

---

### Post by Lars Noodén on 2012-02-04
You can see which kernels you have by using [dpkg](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dpkg.1.html)

```

dpkg --get-selections linux-image*

```

Then manually uninstall the one(s) you want to get rid of.  

```


sudo apt-get remove linux-image-3.2.0-2-generic

sudo apt-get autoremove

```

---

### Post by Virajs on 2012-02-04
Thanks. I came across with that. And now There's no list of older kernels while booting. But I have little doubt because when I executed for linux images it was like this. 
dpkg --get-selections linux-image*

linux-image-2.6.35-22-generic			deinstall
linux-image-2.6.35-28-generic			deinstall
linux-image-2.6.35-30-generic			install
linux-image-generic				install

So, I feel the older ones aren't removed completely yet.

---

### Post by Lars Noodén on 2012-02-04
The ones that say 'install' are there installed.  The ones that say 'deinstall' have been removed already but used to be there once.  This is useful in tracking the things you've removed from a stock distro in case you are going to automate the changes.

If you want to show only what you have currently installed, you can assist **dpkg** with [awk](http://manpages.ubuntu.com/manpages/oneiric/en/man1/awk.1posix.html)

```

dpkg --get-selections linux-image* | awk '$2="install" { print $1 }'

```

---

### Post by philinux on 2012-02-04
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

See step 5. Make sure you do the dry run first.

---

