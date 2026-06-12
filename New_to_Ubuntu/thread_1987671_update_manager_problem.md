---
title: "update manager problem"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-05-26
was trying to install a new update to virtual box which didnt go right  now i keep getting this error

from the spm
E: The package virtualbox-4.1 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

from the update manager
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox-4.1 needs to be reinstalled, but I can't find an archive for it.'


any ideas how to fix/tks

---

### Post by rburkartjo on 2012-05-26
note that both the spm and software center wont open when i try they both flash for a second and then  close

---

### Post by rburkartjo on 2012-05-26
here is a link to the site with the update info on virtual box
if it helps _NOTE DONT USE IT DOESNT WORK_

[http://www.ubuntugeek.com/virtualbox-4-1-16-released-and-ubuntu-installation-instructions-included.html](http://www.ubuntugeek.com/virtualbox-4-1-16-released-and-ubuntu-installation-instructions-included.html)

---

### Post by rburkartjo on 2012-05-26
okay i got it fixed. first i had to again install the ppa
then got this message

The following packages will be upgraded:
  virtualbox-4.1
1 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 70.0 MB of archives.
After this operation, 1,407 kB of additional disk space will be used.
Get:1 [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib virtualbox-4.1 amd64 4.1.16-78094~Ubuntu~precise [70.0 MB]
Fetched 70.0 MB in 49s (1,410 kB/s)                                                                           
Preconfiguring packages ...
(Reading database ... 266494 files and directories currently installed.)
Preparing to replace virtualbox-4.1 4.1.14-77440~Ubuntu~precise (using .../virtualbox-4.1_4.1.16-78094~Ubuntu~precise_amd64.deb) ...
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/virtualbox-4.1_4.1.16-78094~Ubuntu~precise_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Processing triggers for python-central ...
Errors were encountered while processing:
 /var/cache/apt/archives/virtualbox-4.1_4.1.16-78094~Ubuntu~precise_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ray@ray-GC660AA-ABA-SR5123WM:~$ 

navigated ti /var/cache/apt/archives and deleted virtual box
now spm software center work and all errors gone what a pain

---

### Post by virtualstorm on 2012-06-04
> first i had to again install the ppa then got this message
Can you please explain, *ppa* means?

---

