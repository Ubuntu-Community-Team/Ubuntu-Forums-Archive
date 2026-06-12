---
title: "Upgrade may not have completed."
date: 2008-11-19
forum: New to Ubuntu
---

### Post by fatgeek on 2008-11-19
There was some kind of glitch during my upgrade from Hardy to Intrepid.  I think that the upgrade did not complete.  If I go to System > About Ubuntu where the version information is now has the following:

```
Thank you for your interest in Ubuntu 
                - the  - released in .
				
```

My system seems to be working fine, but my question is: is there a way to check if the whole system has been upgraded?  Some kind of version integrity check or something?

---

### Post by taurus on 2008-11-19
You can try running these two commands from a terminal.

```
sudo apt-get update
sudo apt-get upgrade
```

---

