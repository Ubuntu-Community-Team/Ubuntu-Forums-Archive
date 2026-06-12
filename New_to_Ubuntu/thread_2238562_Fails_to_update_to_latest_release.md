---
title: "Fails to update to latest release"
date: 2014-08-08
forum: New to Ubuntu
---

### Post by Craig_Pullen on 2014-08-08
What might cause a failure to update to the very latest release.  My home computer runs Ubuntu 14.04.4 or 5 (with 3.13.0-32) yet my office computer runs Ubuntu 14.04.1 LTS (with 3.13.0-27).  I run the following on BOTH computers:

sudo  apt-get update  &&  sudo apt-get  upgrade
sudo  apt-get  dist-upgrade

Any ideas ?

thanx
CRaig

---

### Post by Frogs Hair on 2014-08-08
Hello and Welcome Craig_Pullen :

One possible cause would be a difference in Software & Update settings. If proposed updates are enabled on one computer and not the other this could explain the difference in kernel versions. To find out release and kernel versions use the following commands.

Release ```
lsb_release -a 
``` Kernel Version ```
uname -r
```

14.04.4 hasn't been  released yet
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by ajgreeny on 2014-08-08
> **Craig_Pullen said:**
> What might cause a failure to update to the very latest release.  [COLOR=#ff0000]My home computer runs Ubuntu 14.04.4 or 5[/COLOR] (with 3.13.0-32) yet my office computer runs Ubuntu 14.04.1 LTS (with 3.13.0-27).  I run the following on BOTH computers:

sudo  apt-get update  &&  sudo apt-get  upgrade
sudo  apt-get  dist-upgrade

Any ideas ?

thanx
CRaigI presume that was a typo and should have read [COLOR=#ff0000]12.04.4 or 5[/COLOR].

The online upgrades from 12.04.4 or 5 have not yet appeared in update manager, but should do very soon.  Does that answer your query or is it just about the kernel version?

I have 12.04 and 14.04 and both are using the 3.13.0-32 kernel, so unless the difference is from the phased updates that are being used now, I can not see why your two systems are not updating the kernel to the same version.

---

### Post by Impavidus on 2014-08-09
Phased upgrades are used by the update manager, not by apt-get IIRC. Also, 3.13.0-32 has been out for quite a while now, and so have 3.13.0-30 and 3.13.0-29. The office computer with 3.13.0-27 seems months behind.

Open a terminal on the office computer, maximise it (else the output will be incomplete) and run```
dpkg --list linux-image*
```I wonder that maybe the metapackage to pull in the new kernels isn't installed. That would most likely be the package **linux-image-generic**.

---

### Post by Craig_Pullen on 2014-08-09
Sorry I've been distracted lately and medded up.  On verifying the releases again I found Both were at 14.04.1 LTS but that the kernels were different.  My home computer is at 3.13.0-32 generic (uname -a) and my office computer is at 3.13.0-27-generic (uname -a).

Could there be a dependency that isn't met with the latest release?  Is there a way to reset something to get the latest kernel?

thanx
Craig

---

### Post by coffeecat on 2014-08-09
@Craig_Pullen, you may have missed something that Impavidus posted:

> **Impavidus said:**
> I wonder that maybe the metapackage to pull in the new kernels isn't installed. That would most likely be the package **linux-image-generic**.

Try this on the office computer in case one or more of the metapackages have gone missing:

```
sudo apt-get install --reinstall linux-generic
```

That will install (or re-install) the metapackage linux-generic which will pull in the latest metapackages linux-image-generic and linux-headers-generic, which will in turn pull in the latest 3.13.0.32 kernel packages.

---

### Post by sandyd on 2014-08-09
Also on both computers
```

cat /etc/apt/sources.list
```
Are the sources identical?

---

### Post by Craig_Pullen on 2014-08-09
OK thanx for your help - I'll try both fixes (compare sources.list & reinstall linux-generic) on office computer on Monday.

thank you again
craig

---

### Post by Craig_Pullen on 2014-08-11
Solved:  The command ...

sudo apt-get install --reinstall  linux-generic

loaded the latest kernel. 

thanx again
craig

---

