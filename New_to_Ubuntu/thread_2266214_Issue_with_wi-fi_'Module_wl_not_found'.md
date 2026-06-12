---
title: "Issue with wi-fi: 'Module wl not found'"
date: 2015-02-20
forum: New to Ubuntu
---

### Post by Spencer_Monheim on 2015-02-20
Hi everyone!

I just installed ubuntu 14.04 on my lenovo twist and while trying to download the correct drivers for my wireless card, bcm43228, which uses bcmwl-kernel-source. So I did the standard sudo apt-get install bcmwl-kernel-source and got this as my return:

spencer@Science-Twist:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for spencer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,126 kB of archives.
After this operation, 5,800 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 190055 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Setting up bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Loading new bcmwl-6.30.223.141+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.16.0-30-generic
Building for architecture x86_64
Building initial module for 3.16.0-30-generic
Error! Bad return status for module build on kernel: 3.16.0-30-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/make.log for more information.



Not quite sure where to go from there, I have a decent amount of experience USING ubuntu (been using since 12.04, but that was on a different computer and was painless to setup and use), but as far as troubleshooting my google-fu is my only tool which has ended up just overwhelming me and made me even more confused :(

Any additional information I'm willing to give! Just let me know what I need to do to have you guys' help me!

---

### Post by Spencer_Monheim on 2015-02-21
evidently it's an issue with the kernel, fresh instal on 14.10 and everything worked out of the box. Not sure what exactly was wrong, but fresh instal of 14.10 fixed everything! Just in case someone else has the issue.

---

### Post by jeremy31 on 2015-02-21
You had kernel 3.16.0-30 on your 14.04 install and the version of bcmwl-kernel-source must not have been updated for trusty in the repos.  For the 3.16 kernel you need bcmwl version 6.30.223.248

Please use the 'thread tools' to mark this as solved

---

