---
title: "Uninstall using synaptic history"
date: 2005-03-20
forum: Repositories &amp; Backports
---

### Post by gio on 2005-03-20
I noticed that synaptic can show the installation history: there is a way to use this list to uninstall packages?
For example if you install kubuntu-desktop it show all the additional pkg installed to resolve dependencies, it would be nice to be able to use that list to restore the previuos status.

---

### Post by precinto on 2006-12-13
So, aren't there plans to implement this at all? I haven't found anything on Launchpad. 

But I think it could be useful, don't you?

---

### Post by learningcurb on 2009-06-04
I think this is an interesting good idea too.  Actually what would be useful is to have a column that lists the date when a package was installed.  Then you could sort by the 'date installed' column and roll back installs as needed.

---

### Post by durand on 2009-06-04
If you use aptitude instead of apt-get, it has this functionality. It would be nice if synaptic had this though..

---

### Post by learningcurb on 2009-06-05
Hmm, how do you uninstall using aptitude's history?  So far, I've found the log file at /var/log/aptitude after reading [http://ubuntuforums.org/showthread.php?t=348803](http://ubuntuforums.org/showthread.php?t=348803)

Also, check out this bug report on Launchpad:[Feature: Synaptic Dpkg History]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/368314")

---

### Post by durand on 2009-06-06
It might only work if you install the program via aptitude with
```
sudo aptitude install program
```
Then ```
sudo aptitude remove program
``` will remove its dependencies as well.

---

### Post by learningcurb on 2009-06-06
Hmm, too bad it only works with aptitude.  I jump between apt-get and Synaptic depending on what information I want about a package.

Isn't apt-get autoremove about the same as aptitude's remove, aside from the extra step?  Also, I've heard that aptitude can sometimes be too aggressive and break dependencies occasionally, but that may be an old problem that has been fixed by now.

---

### Post by durand on 2009-06-07
> **learningcurb said:**
> Hmm, too bad it only works with aptitude.  I jump between apt-get and Synaptic depending on what information I want about a package.

Isn't apt-get autoremove about the same as aptitude's remove, aside from the extra step?  Also, I've heard that aptitude can sometimes be too aggressive and break dependencies occasionally, but that may be an old problem that has been fixed by now.

Yeah, aptitide does sometimes still have that problem but I pretty much always use it instead of apt-get because it's much better at keeping a clean system.

---

