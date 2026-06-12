---
title: "Update Manager Problem"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by ProntoAnthony on 2011-11-16
When Update Manager is run the following error appears:


installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 11928 package 'libmagic1':
 missing maintainer
dpkg: error: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
Error in function: 
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 11928 package 'libmagic1':
 missing maintainer


Any suggestions for fixing it?

---

### Post by mikechant on 2011-11-16
Bottom two posts on this page:
[http://offthelip.org/?p=80](http://offthelip.org/?p=80)
suggests this could be due to another package manager (e.g. synaptic, software center) running at the same time.

If you can't find running one try rebooting to clear this (in case of a leftover process).

If that doesn't work, can you check if the file
'/var/lib/dpkg/available'
actually exists?

---

### Post by ProntoAnthony on 2011-11-16
Thank you for your reply. These are the steps I took to correct the problem:


Rebooted. Same problem when I ran update manager:

installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 11928 package 'libmagic1':
 missing maintainer
dpkg: error: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 11928 package 'libmagic1':
 missing maintainer



I took your advice and found the file `/var/lib/dpkg/available' did not exist. A file named `/var/lib/dpkg/available-old' existed. I renamed "available-old" "available" and ran Update Manager again and it completed with no errors.

---

### Post by Jnifoo on 2012-04-26
> **ProntoAnthony said:**
> I took your advice and found the file `/var/lib/dpkg/available' did not exist. A file named `/var/lib/dpkg/available-old' existed. I renamed "available-old" "available" and ran Update Manager again and it completed with no errors.
In the same problem under Ubuntu 12.04 beta, instead I have an existing 'available' file.
Deleting the 'available' file and run a new 'apt-get update' generate the same broken 'available' file.

So I overwrite it with the availaible-old file and it fixed it !
Thanks.

---

