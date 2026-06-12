---
title: "Dpkg error"
date: 2014-09-13
forum: New to Ubuntu
---

### Post by jordon2 on 2014-09-13
hello friends first of sorry for my bad english :)

i am new in ubuntu and buyed a octa core cpu from fortatrust which is working fine but after error in vnc etc install it goes stucked on an error now iam unable to do any thing on my ubuntu vps :( :cry:


even apt-get upgrade is not working :cry: 

i tried apt-get -f upgrade also but same error occurs ..

i cant rebuild my vps because vps company asking for 10 usd rebuild fee :cry:

here is the error details :) may be any expert help me ;)
```
root@vm79858:~# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  baloo
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  evolution-data-server python3-distupgrade ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk
Suggested packages:
  evolution-data-server-dbg
The following NEW packages will be installed:
  evolution-data-server
The following packages will be upgraded:
  python3-distupgrade ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
3 upgraded, 1 newly installed, 0 to remove and 135 not upgraded.
159 not fully installed or removed.
Need to get 136 kB/450 kB of archives.
After this operation, 1454 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main ubuntu-release-upgrader-gtk all 1:0.220.5 [9284 B]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main ubuntu-release-upgrader-core all 1:0.220.5 [23.1 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main python3-distupgrade all 1:0.220.5 [104 kB]
Fetched 136 kB in 0s (230 kB/s)
(Reading database ... 208798 files and directories currently installed.)
Preparing to unpack .../evolution-data-server_3.10.4-0ubuntu1.2_amd64.deb ...
Unpacking evolution-data-server (3.10.4-0ubuntu1.2) ...
dpkg: error processing archive /var/cache/apt/archives/evolution-data-server_3.10.4-0ubuntu1.2_amd64.deb (--unpack):
 unable to create `/usr/lib/evolution/camel-index-control-1.2.dpkg-new' (while processing `./usr/lib/evolution/camel-index-control-1.2'): Input/output error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../ubuntu-release-upgrader-gtk_1%3a0.220.5_all.deb ...
Unpacking ubuntu-release-upgrader-gtk (1:0.220.5) over (1:0.220.4) ...
Preparing to unpack .../ubuntu-release-upgrader-core_1%3a0.220.5_all.deb ...
Unpacking ubuntu-release-upgrader-core (1:0.220.5) over (1:0.220.2) ...
dpkg: warning: ubuntu-release-upgrader-core: unable to stat config file 'etc/update-manager/release-upgrades'
 (= '/etc/update-manager/release-upgrades'): Input/output error
dpkg: error processing archive /var/cache/apt/archives/ubuntu-release-upgrader-core_1%3a0.220.5_all.deb (--unpack):
 unable to stat `./etc/update-manager/release-upgrades' (which I was about to install): Input/output error
Preparing to unpack .../python3-distupgrade_1%3a0.220.5_all.deb ...
Unpacking python3-distupgrade (1:0.220.5) over (1:0.220.2) ...
dpkg: error processing archive /var/cache/apt/archives/python3-distupgrade_1%3a0.220.5_all.deb (--unpack):
 unable to stat `./usr/lib/python3/dist-packages/DistUpgrade/GtkProgress.py' (which I was about to install): Input/output error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/evolution-data-server_3.10.4-0ubuntu1.2_amd64.deb
 /var/cache/apt/archives/ubuntu-release-upgrader-core_1%3a0.220.5_all.deb
 /var/cache/apt/archives/python3-distupgrade_1%3a0.220.5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

iam ready to pay 3 usd via btc if any one ready to solve my problem i will pm my details to him (only trusted one) [SIZE=5]**:)**[/SIZE]

---

### Post by Bashing-om on 2014-09-13
jordon2; Hello;

Maybe nothing more here than corrupted index files.
Try:
```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

``` to partially remove the package manager's index files, and rebuild them. and 'dist-upgrade' to install held packages ( ie: new kernels).
IF there are still errors, post back the complete outputs, such that we see the errors in context.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

