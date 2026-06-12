---
title: "Problem updating"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by Akhil_Katkar on 2013-09-10
I have a problem updating. Whenever I use sudo apt-get update the following msg comes... I am very new to ubuntu... please help

```
root@akhil-Inspiron-1545:~# sudo apt-get update
Err http://extras.ubuntu.com raring Release.gpg                                
  Could not connect to 10.0.0.51:3142 (10.0.0.51), connection timed out
Err http://ppa.launchpad.net raring Release.gpg                                
  Could not connect to 10.0.0.51:3142 (10.0.0.51), connection timed out
Err http://archive.ubuntu.com raring Release.gpg                               
  Could not connect to 10.0.0.51:3142 (10.0.0.51), connection timed out
Err http://archive.ubuntu.com raring-updates Release.gpg
  Unable to connect to 10.0.0.51:3142:
Err http://archive.ubuntu.com raring-security Release.gpg
  Unable to connect to 10.0.0.51:3142:
Err http://archive.ubuntu.com raring-proposed Release.gpg
  Unable to connect to 10.0.0.51:3142:
Err http://archive.ubuntu.com raring-backports Release.gpg
  Unable to connect to 10.0.0.51:3142:
Reading package lists... Done           
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/Release.gpg  Could not connect to 10.0.0.51:3142 (10.0.0.51), connection timed out

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-updates/Release.gpg  Unable to connect to 10.0.0.51:3142:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-security/Release.gpg  Unable to connect to 10.0.0.51:3142:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/Release.gpg  Could not connect to 10.0.0.51:3142 (10.0.0.51), connection timed out

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-proposed/Release.gpg  Unable to connect to 10.0.0.51:3142:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-backports/Release.gpg  Unable to connect to 10.0.0.51:3142:

W: Failed to fetch http://ppa.launchpad.net/upubuntu-com/web/ubuntu/dists/raring/Release.gpg  Could not connect to 10.0.0.51:3142 (10.0.0.51), connection timed out

W: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by whitesmith on 2013-09-10
A quick whois reveals you're connecting to a private address. It may be down for maintenance. Wait a bit and try again.

---

### Post by Akhil_Katkar on 2013-09-10
I have been doing it from yesterday...

---

### Post by deadflowr on 2013-09-10
Open the dash and find the program "Software and Updates" and launch it.
Then go to the section Download from and choose the dropdown selection "other"
Then run the find best server option in the top right corner of the window that opens up.
Then let it run(it may take awhile).
Then when finished, click on choose best server, and then close the window, then close the software and updates window.
Then open software updater and let it run.

This of course is based on whether or not you are running Ubuntu Desktop and not the server version.

---

