---
title: "Red exclamation mark: &quot;The update information is outdated (...)&quot;"
date: 2015-01-25
forum: New to Ubuntu
---

### Post by davismsteve on 2015-01-25
I am getting the same error and when I check for update it fails with the following error: 

W:Failed to fetch [http://ppa.launchpad.net/folke-schwinning/personal/ubuntu/dists/utopic/main/binary-amd64/Packages](http://ppa.launchpad.net/folke-schwinning/personal/ubuntu/dists/utopic/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/folke-schwinning/personal/ubuntu/dists/utopic/main/binary-i386/Packages](http://ppa.launchpad.net/folke-schwinning/personal/ubuntu/dists/utopic/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I have no network connectivity issues, and when I run (sudo apt-get update) I get the errors: 

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en
Fetched 1,088 kB in 8s (133 kB/s)                                              
W: Failed to fetch [http://ppa.launchpad.net/folke-schwinning/personal/ubuntu/dists/utopic/main/binary-amd64/Packages](http://ppa.launchpad.net/folke-schwinning/personal/ubuntu/dists/utopic/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/folke-schwinning/personal/ubuntu/dists/utopic/main/binary-i386/Packages](http://ppa.launchpad.net/folke-schwinning/personal/ubuntu/dists/utopic/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

I am not sure how to fix this issue, and am new to the Ubuntu thread. I am trying to fix the problem by walking thru the thread, but any suggestions are appreciated.  

Some information on my version and system: 

lsb_release -a output: 

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic

and

lscpu output:

Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 58
Model name:            Intel(R) Celeron(R) CPU 1007U @ 1.50GHz
Stepping:              9
CPU MHz:               898.417
CPU max MHz:           1500.0000
CPU min MHz:           800.0000
BogoMIPS:              2992.93
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              2048K
NUMA node0 CPU(s):     0,1

---

### Post by bapoumba on 2015-01-25
Post moved to its own thread (the one you posted in was solved).
I also get a 404 on this ppa, please remove it from your Software Sources. Then run the update again.

---

