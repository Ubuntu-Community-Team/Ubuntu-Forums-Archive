---
title: "problem with update manager"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by sevenape on 2008-04-26
So apparently I have a serious problem with my update manager, it told me to open synaptic manager and when I did it gave me this message:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_hardy_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


If I try to add/remove applications I get this: 

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


Please could someone talk me through what to do?

Thanks


OK I did the sudo stuff in the terminal and it all works now :)

---

### Post by meindian523 on 2008-06-06
Please mark it as solved.See the link in my sig to see how.

---

