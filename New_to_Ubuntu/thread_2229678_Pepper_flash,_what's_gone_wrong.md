---
title: "Pepper flash, what's gone wrong?"
date: 2014-06-14
forum: New to Ubuntu
---

### Post by Huzudra on 2014-06-14
I should preface this with, issue only after upgrading from 13.something to 14.04 via command line. So it's entirely possible this is caused by an upgrade. I'll do a clean install over the 12.04 later to see if the issue exists there and try it on another 14.04 PC here also and see if the same error occurs. I just figured I'd ask before I potentially break things on other systems.

```
owner@owner-Inspiron-6000:~$ sudo update-pepperflashplugin-nonfree --install --verbose
options :  --install --verbose --
temporary directory: /tmp/pepperflashplugin-nonfree.uS6WRVX2EG
doing apt-get update on google repository
cleaning up temporary directory /tmp/pepperflashplugin-nonfree.uS6WRVX2EG ...
ERROR: failed to retrieve status information from google : Ignoring unknown parameter "password level"
Ignoring unknown parameter "update encrypted"
More information might be available at:
  http://wiki.debian.org/PepperFlashPlayer
owner@owner-Inspiron-6000:~$ 

```

What's not quite gone right here? Is there a problem at the Google end or my end?

---

