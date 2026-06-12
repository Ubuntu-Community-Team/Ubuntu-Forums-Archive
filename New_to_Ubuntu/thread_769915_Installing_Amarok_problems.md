---
title: "Installing Amarok problems"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by SigmaHog on 2008-04-27
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

i tried sudo apt-get install amarok and this is what i get...

whats it mean?

---

### Post by SigmaHog on 2008-04-27
wait ... forgot to close synaptic... this is what I got

 sudo apt-get install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package amarok is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package amarok has no installation candidate

---

### Post by SigmaHog on 2008-04-27
and this is what I get for sudo apt-get install wine:

sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libaudio2 but it is not installable
E: Broken packages

---

### Post by hackle577 on 2008-04-27
Try running

```
sudo apt-get install -f
```

then try again

---

