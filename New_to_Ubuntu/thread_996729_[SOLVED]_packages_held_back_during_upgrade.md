---
title: "[SOLVED] packages held back during upgrade"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by panorack on 2008-11-29
When trying to install a security upgrade using 'sudo apt-get upgrade' (after updating databases) I got the following message:

"The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded."

The security upgrade icon is still showing and trying to install via 'Update Manager' caused the machine to hang, necessitating a shut down with the power off button. (Nasty!)

The packages are for Ubuntu 8.04 and show the following version number, 2.6.24.22.24. I am running kernal version 2.6.21.23

Any suggestions, please?

---

### Post by lswest on 2008-11-29
They're being held back because dependencies have not yet been upgraded (the packages in the repo are out of date and the newer version are being packaged now most likely).  Just try again in a few hours, and it should work.

Packages are uploaded at different rates, and you can force the upgrade, but it may cause a lot of issues, better to just wait til all the dependencies are satisfied.

---

### Post by panorack on 2008-11-29
Thanks for that lswest. I can stop worrying now.:)

---

### Post by lswest on 2008-11-29
> **panorack said:**
> Thanks for that lswest. I can stop worrying now.:)

Haha, yeah, glad I could save you that trouble :P

---

### Post by panorack on 2008-12-05
I have removed the 'solved' flag from this post because a week later I am still getting the same four packages held back and it doesn't seem sensible to release upgrades if the dependencies are still not resolved so long after. Plus the fact that no-one else seems to have commented on this problem.

Every time I boot up the 'software updates' flags up even when these four are the only ones there.

Are there any other reasons why they could be held back?

---

### Post by mkvnmtr on 2008-12-05
Try changing the mirror you are using. I suppose it is possible your mirror has not got them updated for some reason.

---

### Post by Elfy on 2008-12-05
Update from a terminal - see if they are there now

```
sudo apt-get update
```

Run the update manager

---

### Post by panorack on 2008-12-05
Tried again using Synaptic this time rather than 'apt-get' in a terminal. Rather than click on the upgrade icon I marked all upgrades and applied the changes. This time it went through with no problem.

I don't know what the problem was as I have tried repeatedly to upgrade using a terminal (my normal method) but thanks to all those who have taken the trouble to offer advice.

---

### Post by bodhi.zazen on 2008-12-05
If you are using the command line, and upgrades are held back with

```
sudo apt-get upgrade
```

use

```
sudo apt-get dist-upgrade
```

Or aptitiude or synaptic or .....

---

