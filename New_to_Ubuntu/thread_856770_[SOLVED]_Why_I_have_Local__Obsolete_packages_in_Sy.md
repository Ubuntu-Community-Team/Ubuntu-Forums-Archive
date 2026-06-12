---
title: "[SOLVED] Why I have Local  Obsolete packages in Synaptic"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Liakath on 2008-07-11
Dear Friends,

I am curiously surprised / perplexed over some of the installed packages showing up as local / obsolete packages in Synaptic. Kindly see the attached screenshot. All these except realplayer were installed / updated through repos including Ubuntu Hardy proposed / backports.


For example for "kaffeine" only the earlier version is available in repos while the installed version is not available in any more. It is not that I have any problem with these packages; only curious to know why these show up like this.

Liakath

---

### Post by LowSky on 2008-07-11
try? 
```
 sudo apt-get autoremove
```

---

### Post by Liakath on 2008-07-11
Dear LowSky,
> **LowSky said:**
> try? 
```
 sudo apt-get autoremove
```

Thank you. I tried your suggestion with these results.

```
liakath@liakath-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
liakath@liakath-laptop:~$ 
```

Not that I want these to be removed; are these versions not available in 
any of the repos? Will I be able to get updates for them when they come up!

---

### Post by rogier.de.groot on 2008-07-11
Did you install these from the repo? Maybe "local" just means they´re outside the normal package tree?

---

### Post by Liakath on 2008-07-11
Dear rogier.de.groot,
> **rogier.de.groot said:**
> Did you install these from the repo? Maybe "local" just means they´re outside the normal package tree?

Thanks. Except "realplayer" other packages were from repos and updated through synaptic / aptitude update route only. "realplayer" was installed with a download from realplayer website some time back and probably the latest one.

---

### Post by fatality_uk on 2008-07-11
Check this thread out.
May give you the answer

[http://ubuntuforums.org/showthread.php?t=50779](http://ubuntuforums.org/showthread.php?t=50779)

---

### Post by Liakath on 2008-07-11
Dear fatality_uk,
> **fatality_uk said:**
> Check this thread out.
May give you the answer

[http://ubuntuforums.org/showthread.php?t=50779](http://ubuntuforums.org/showthread.php?t=50779)

Thank you for the link. Probably these are versions from the proposed / backports repos which were later removed and yet to appear in regular repos considering that these are newer than what are appearing in hardy / hardy updates repo.

I will wait and watch for newer updates of these packages.

---

### Post by fatality_uk on 2008-07-11
No worries!!

---

### Post by Liakath on 2008-07-11
Dear All,

As a further attempt to get this resolved I was able to downgrade "kaffeine" and "kaffeine-gstreamer" packages by forcing version available in "Hardy / Hardy updates" repos. The downgraded version was downloaded by Synaptic and installed. This downgraded these two packages and removed them from local or obsolete list.

However attempting the same with "python2.5" and "python2.5"; I am given the option to remove a number of other installed packages (more than 100) and therefore I did not go through.

Hope by this I will be able to get future updates.

---

