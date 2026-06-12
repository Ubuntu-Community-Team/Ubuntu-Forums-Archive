---
title: "dpkg: unrecoverable fatal error, aborting:"
date: 2017-02-24
forum: New to Ubuntu
---

### Post by deerty on 2017-02-24
i need some help. .
I have been having an error trying to upgrade my system. Currently I can't install/remove or upgrade anything with apt-get...

Here is the error I get when running sudo apt-get upgrade :

Reading changelogs... Done
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'exploitdb': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by ajgreeny on 2017-02-24
Are you using Kali Linux as it is the only distro that I can find with any search for exploitdb?
 
Perhaps you have added Kali Linux Tools PPA 2 to your Ubuntu system.

Tell us more as there is no exploitdb package available in the standard repos for Ubuntu.

---

