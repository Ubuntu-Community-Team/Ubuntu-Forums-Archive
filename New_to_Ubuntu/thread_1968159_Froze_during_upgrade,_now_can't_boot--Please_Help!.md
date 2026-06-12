---
title: "Froze during upgrade, now can't boot--Please Help!!!! Urgent"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by rby151 on 2012-04-28
Sorry for the dramatic title, but I have to take two finals online this week and I need to get this fixed as soon as possible! I was in the middle of upgrading from Oneiric to Precise, and the program that was doing the upgrade froze. So I closed it. Then, my computer wouldn't run any programs, so I shut off the power manually and turned it back on. And now it won't boot. I tried to do dpkg in recovery mode, and it failed. This is what my screen says:
 
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg) rename failed, Read-only file system (/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_release.gpg).
 
W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release.gpg](http://deb.opera.com/opera/dists/stable/Release.gpg)  rename failed, Read-only file system (/var/lib/apt/lists/parital/deb.opera.com_opera_dists_stable_Release.gpg.reverify -> /var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release.gpg).
 
W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
 
I tried to run dpkg at the root command line (I don't even know if that's the right command line! Yes I AM a complete beginner), and it says:
 
dpkg: error: unable to access dpkg status area: Read-only file system
 
Also, the recovery mode menu seems to be not working quite right. I've rebooted and entered recovery mode several times now, and the letters and enter keys allow me to make selections only sometimes. Out of about 6 boots, I've only been able to attempt dpkg twice (and it failed both times). Now, I don't even know for sure that dpkg is what I should be trying to do. Please please please, does anyone have any advice as to how I can get my computer working again, with all my files intact? You will be my hero/ine!

---

