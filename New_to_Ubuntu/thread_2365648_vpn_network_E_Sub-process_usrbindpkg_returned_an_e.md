---
title: "vpn network E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2017-07-08
forum: New to Ubuntu
---

### Post by snowkiller69 on 2017-07-08
```
 sudo apt-get install network-manager-openvpn [sudo] password for demonic1337: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager-openvpn is already the newest version (1.1.93-1ubuntu1.1).
The following packages were automatically installed and are no longer required:
  linux-headers-4.8.0-36 linux-headers-4.8.0-36-generic linux-headers-4.8.0-46
  linux-headers-4.8.0-46-generic linux-headers-4.8.0-49
  linux-headers-4.8.0-49-generic linux-headers-4.8.0-51
  linux-headers-4.8.0-51-generic linux-headers-4.8.0-52
  linux-headers-4.8.0-52-generic linux-headers-4.8.0-53
  linux-headers-4.8.0-53-generic linux-headers-4.8.0-54
  linux-headers-4.8.0-54-generic linux-image-4.8.0-36-generic
  linux-image-4.8.0-46-generic linux-image-4.8.0-49-generic
  linux-image-4.8.0-51-generic linux-image-4.8.0-52-generic
  linux-image-4.8.0-53-generic linux-image-4.8.0-54-generic
  linux-image-extra-4.8.0-36-generic linux-image-extra-4.8.0-46-generic
  linux-image-extra-4.8.0-49-generic linux-image-extra-4.8.0-51-generic
  linux-image-extra-4.8.0-52-generic linux-image-extra-4.8.0-53-generic
  linux-image-extra-4.8.0-54-generic linux-signed-image-4.8.0-46-generic
  linux-signed-image-4.8.0-49-generic linux-signed-image-4.8.0-51-generic
  linux-signed-image-4.8.0-52-generic linux-signed-image-4.8.0-53-generic
  linux-signed-image-4.8.0-54-generic snap-confine
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up util-linux (2.27.1-6ubuntu3.3) ...
syntax error at /usr/sbin/update-rc.d line 147, at EOF
Missing right curly or square bracket at /usr/sbin/update-rc.d line 147, at end of line
Execution of /usr/sbin/update-rc.d aborted due to compilation errors.
dpkg: error processing package util-linux (--configure):
 subprocess installed post-installation script returned error exit status 5
Setting up openvpn (2.3.10-1ubuntu2.1) ...
 * Restarting virtual private network daemon(s)...                               *   No VPN is running.
syntax error at /usr/sbin/update-rc.d line 147, at EOF
Missing right curly or square bracket at /usr/sbin/update-rc.d line 147, at end of line
Execution of /usr/sbin/update-rc.d aborted due to compilation errors.
dpkg: error processing package openvpn (--configure):
 subprocess installed post-installation script returned error exit status 5
dpkg: dependency problems prevent configuration of network-manager-openvpn:
 network-manager-openvpn depends on openvpn (>= 2.1~rc9); however:
  Package openvpn is not configured yet.


dpkg: error processing package network-manager-openvpn (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for libc-bin (2.23-0ubuntu9) ...
Errors were encountered while processing:
 util-linux
 openvpn
 network-manager-openvpn
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

its been stressful trying to reseach this to fix it ive spent 4 hours on trying to fix the problem nothing has worked so please help me

---

### Post by praseodym on 2017-07-09
Lets try
```

sudo dpkg --configure openvpn
sudo dpkg --configure network-manager-openvpn
sudo dpkg --configure util-linux
```

---

### Post by snowkiller69 on 2017-07-09
```
 sudo dpkg --configure openvpn[sudo] password for demonic1337: 
Setting up openvpn (2.3.10-1ubuntu2.1) ...
 * Restarting virtual private network daemon(s)...                               *   No VPN is running.
syntax error at /usr/sbin/update-rc.d line 147, at EOF
Missing right curly or square bracket at /usr/sbin/update-rc.d line 147, at end of line
Execution of /usr/sbin/update-rc.d aborted due to compilation errors.
dpkg: error processing package openvpn (--configure):
 subprocess installed post-installation script returned error exit status 5
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Errors were encountered while processing:
 openvpn



```

---

### Post by wildmanne39 on 2017-07-09
This is an apt issue with installing applications not a networking issue.

Moved to New to Ubuntu.

---

