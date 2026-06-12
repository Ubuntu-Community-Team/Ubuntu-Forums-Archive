---
title: "Libperl problem.."
date: 2022-10-20
forum: New to Ubuntu
---

### Post by yatski on 2022-10-20
So, I ran my usual daily updates and got this:

```
The package system is broken
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 The following packages have unmet dependencies:

libperl5.34: Depends: libcrypt1 (>= 1:4.1.0) but 1:4.4.27-1 is installed
             Depends: zlib1g (>= 1:1.2.2.3) but 1:1.2.11.dfsg-2ubuntu9.2 is installed
             Depends: perl-modules-5.34 (>= 5.34.0-3ubuntu1.1) but 5.34.0-3ubuntu1 is installed
perl: Depends: perl-base (= 5.34.0-3ubuntu1.1) but 5.34.0-3ubuntu1.1 is installed
      Depends: perl-modules-5.34 (>= 5.34.0-3ubuntu1.1) but 5.34.0-3ubuntu1 is installed
      Depends: libperl5.34 (= 5.34.0-3ubuntu1.1) but 5.34.0-3ubuntu1.1 is installed
```

Ran apt-get install -f

```
heta@heta-vaio:~$ sudo apt-get install -f
[sudo] password for heta: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  perl-modules-5.34
The following packages will be upgraded:
  perl-modules-5.34
1 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
2 not fully installed or removed.
Need to get 0 B/2&#8239;976 kB of archives.
After this operation, 3&#8239;072 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 289919 files and directories currently installed.)
Preparing to unpack .../perl-modules-5.34_5.34.0-3ubuntu1.1_all.deb ...
Unpacking perl-modules-5.34 (5.34.0-3ubuntu1.1) over (5.34.0-3ubuntu1) ...
Setting up perl-modules-5.34 (5.34.0-3ubuntu1.1) ...
Setting up libperl5.34:amd64 (5.34.0-3ubuntu1.1) ...
Setting up perl (5.34.0-3ubuntu1.1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
heta@heta-vaio:~$ 
```

....... Can you tell whats the issue?
The update seems to stop on its tracks.

---

### Post by Impavidus on 2022-10-20
The first command complained that perl-modules-5.34 was at an older version than was required by other packages, leading to a version conflict. The second command upgraded perl-modules-5.34 to the correct version. It gave no error message, so it looks like the issue is fixed.

What caused it? It looks like libperl5.34 and perl were upgraded, but the upgrade was interrupted before finishing the upgrade of perl-modules-5.34.

---

### Post by yatski on 2022-10-20
So, I have nothing to worry? (For now, at least..)

---

### Post by Impavidus on 2022-10-20
It at appears fine on first sight.

To be sure, you could run```
sudo apt update
sudo apt upgrade
```That will first check for updates, then download and install them. It may skip a few updates for [phased updating](https://wiki.ubuntu.com/PhasedUpdates), so those will be listed as not upgraded. There shouldn't be any packages listed as not fully installed or removed. If it reports no errors, everything is OK.

---

