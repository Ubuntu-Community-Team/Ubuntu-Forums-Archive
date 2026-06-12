---
title: "HOWTO: Repair a broken package if an upgrade or reinstall fails"
date: 2009-06-15
forum: Outdated Tutorials &amp; Tips
---

### Post by PaulWhipp on 2009-06-15
For whatever reason, I often get broken packages after an upgrade. Errors such as "corrupt tar file" lead to my system ending up in a state where something does not work as it should.

Here is how I go about fixing these problems:

First isolate the issue using:
```

$ dpkg --configure -a

```

This will fall over with a missing file or corrupt package or some such. It varies but you should be able to spot the earliest issue in the list in terms of either a missing file or a bad package. For example (from my most recent update):

```

$ sudo dpkg --configure -a
Setting up xulrunner-1.9 (1.9.0.11+build2+nobinonly-0ubuntu0.9.04.1) ...
/var/lib/dpkg/info/xulrunner-1.9.postinst: 5: /usr/bin/xulrunner-1.9: not found
dpkg: error processing xulrunner-1.9 (--configure):
subprocess post-installation script returned error exit status 127 
...

```

Your exact issue will be different but if look at your dpkg output and you should be able to make a good guess at the package or file that is at the root of your problems. In my case above its the missing "xulrunner-1.9" file.

If you need to identify the package a file belongs to, use the very handy [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

Now you might get lucky and be able to re-install the package and have the problem go away but its more likely that the configuration problems have you stuck because the same configuration error hits you again. Its worth a try.

If that fails you can look at removing the package and then reinstalling it but be wary of any additional uninstalls - if the list is more than one or two items long or is too scary (like its going to remove your desktop) I would not go there. You will need to reinstall everything on the list and you can end up with bootstrapping issues (like not having a browser, or worse). If in doubt, don't try it.

Still stuck? That's what usually happens to me too.

So next we download the offending package file manually:
```

$ sudo aptitude download <package name>

```

This will download a file whose name generally starts with the package name and looks something like "xulrunner-1.9_1.9.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb"

Now we have our package file, we can force it to install properly using dpkg:
```

$ sudo dpkg --force-overwrite --install <file name> 

```

Next we can get the configuration issues affecting any other parts of the update sorted out:
```

$ sudo dpkg --configure -a 

```

Hopefully the command will complete fine. If it doesn't, it should at least get further on and you can rinse and repeat with the next issue until it comes up clean.

---

### Post by PaulWhipp on 2009-07-28
Something else to try if trying to remove a package and it wont go away because of script errors:

```

~ $ aptitude purge <package name>

```

Its more effective than synaptic or apt-get at dealing with problems in the pre-removal scripts.

---

### Post by crystaldart on 2009-08-02
Thank you Paul.

Now this tut saved my neck. Was stuck half way installing the Java Environment.

---

