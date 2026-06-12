---
title: "Problem installing evoltion ews"
date: 2015-06-18
forum: New to Ubuntu
---

### Post by anbu-s on 2015-06-18
I'm trying to install evolution exchange web services to access my hosted exchange email.
When I try this command, I get dependency error

```

sudo apt-get install evolution-ews
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:


The following packages have unmet dependencies:
 evolution-ews : Depends: libevolution (< 3.11) but 3.12.9-0ubuntu2~trusty1 is to be installed
                 Depends: evolution (< 3.11) but 3.12.9-0ubuntu2~trusty1 is to be installed
E: Unable to correct problems, you have held broken packages.


```
I'm using evolution 3.12.9
```

llsb_release -a; uname -a; apt-cache policy evolutionNo LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty
Linux Terminatore 3.13.0-55-generic #92-Ubuntu SMP Sun Jun 14 18:32:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
evolution:
  Installed: 3.12.9-0ubuntu2~trusty1
  Candidate: 3.12.9-0ubuntu2~trusty1
  Version table:
 *** 3.12.9-0ubuntu2~trusty1 0
        100 /var/lib/dpkg/status
     3.10.4-0ubuntu2 0
        500 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     3.10.4-0ubuntu1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages



```

---

### Post by ian-weisser on 2015-06-18
Looks like you previously added some source (like a PPA or third-party repo) that claims to make 3.12.9 available. And then, perhaps, removed that source.

Does the problem persist after an apt-get update?

---

