---
title: "can't open synaptic or update manager in 11.04"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by rmallett on 2011-12-23
Hi,

I'm not too experienced with Ubuntu. Last week an intimidating message appeared when I tried to use update manager (copied below). I can't think of anything I've done to the system that might be the cause.

I have no idea how to resolve this problem so that I can update my system (I am running Ubuntu on a laptop, and I don't know if it can have a new version of Ubuntu installed either)

Any help is much appreciated.

Thanks,
Rob

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by rmallett on 2011-12-23
I've been trying to update my system (11.04). I don't know what has created this problem, but I cannot open Synaptic (nothing at all happens), I cannot open Computer Janitor, and when I open Update Manager, the following message appears: 

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, Eroblem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_bina ry-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

Otherwise, nothing else is apparently wrong. Any advice on how to resolve these issues would be appreciated. 

I am leery of reinstalling the system because I don't have the original installation disk (I'm away for Christmas). I am running Ubuntu on a laptop that I bought online, and I don't know if I can simply reinstall any 'version' of 11.04, or if the disk that came with the system is unique in some way.

Thanks

---

### Post by coffeecat on 2011-12-23
Threads merged. Please do not post duplicates for the same problem.

---

### Post by plucky on 2011-12-23
> 'E:Encountered a section with no Package: header, Eroblem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_bina ry-amd64_Packages, E:The package lists or status file could not be parsed or opened.'


From a terminal ```
sudo rm /var/lib/apt/lists/* -vf
```

Then run ```
sudo apt-get update
``` to reload the list files you deleted with the first command.

Good luck

---

