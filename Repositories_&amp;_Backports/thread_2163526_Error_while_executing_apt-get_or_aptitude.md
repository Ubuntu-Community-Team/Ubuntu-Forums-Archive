---
title: "Error while executing apt-get or aptitude"
date: 2013-07-18
forum: Repositories &amp; Backports
---

### Post by tarekz on 2013-07-18
tarekz@myserver:~$ sudo apt-get update
/usr/lib/apt/methods/s3: error while loading shared libraries: libapt-pkg-libc6.
10-6.so.4.8: cannot open shared object file: No such file or directory
E: Method s3 has died unexpectedly!
E: Sub-process s3 returned an error code (127)
E: Method /usr/lib/apt/methods/s3 did not start correctly

same exact error if I try sudo aptitude update.

Any idea what is wrong?

---

### Post by tarekz on 2013-07-18
Some more details.
E: Method s3 has died unexpectedly!
E: Sub-process s3 returned an error code (127)
E: Method /usr/lib/apt/methods/s3 did not start correctly
W: Failed to fetch s3://s3.amazonaws.com/my_repo/Release.gpg
W: Failed to fetch [http://cf-mirror.rightscale.com/ubuntu_daily/2013/06/11/dists/precise/Release.gpg](http://cf-mirror.rightscale.com/ubuntu_daily/2013/06/11/dists/precise/Release.gpg)
W: Failed to fetch [http://cf-mirror.rightscale.com/ubuntu_daily/2013/06/11/dists/precise-updates/Release.gpg](http://cf-mirror.rightscale.com/ubuntu_daily/2013/06/11/dists/precise-updates/Release.gpg)
W: Failed to fetch [http://cf-mirror.rightscale.com/ubuntu_daily/2013/06/11/dists/precise-security/Release.gpg](http://cf-mirror.rightscale.com/ubuntu_daily/2013/06/11/dists/precise-security/Release.gpg)
W: Failed to fetch [http://ec2-us-east-mirror1.rightscale.com/ubuntu_daily/2013/06/11/dists/precise/Release.gpg](http://ec2-us-east-mirror1.rightscale.com/ubuntu_daily/2013/06/11/dists/precise/Release.gpg)
W: Failed to fetch [http://ec2-us-east-mirror1.rightscale.com/ubuntu_daily/2013/06/11/dists/precise-updates/Release.gpg](http://ec2-us-east-mirror1.rightscale.com/ubuntu_daily/2013/06/11/dists/precise-updates/Release.gpg)
W: Failed to fetch [http://ec2-us-east-mirror1.rightscale.com/ubuntu_daily/2013/06/11/dists/precise-security/Release.gpg](http://ec2-us-east-mirror1.rightscale.com/ubuntu_daily/2013/06/11/dists/precise-security/Release.gpg)
W: Failed to fetch [http://ec2-us-east-mirror2.rightscale.com/ubuntu_daily/2013/06/11/dists/precise/Release.gpg](http://ec2-us-east-mirror2.rightscale.com/ubuntu_daily/2013/06/11/dists/precise/Release.gpg)
W: Failed to fetch [http://ec2-us-east-mirror2.rightscale.com/ubuntu_daily/2013/06/11/dists/precise-updates/Release.gpg](http://ec2-us-east-mirror2.rightscale.com/ubuntu_daily/2013/06/11/dists/precise-updates/Release.gpg)
W: Failed to fetch [http://ec2-us-east-mirror2.rightscale.com/ubuntu_daily/2013/06/11/dists/precise-security/Release.gpg](http://ec2-us-east-mirror2.rightscale.com/ubuntu_daily/2013/06/11/dists/precise-security/Release.gpg)
W: Failed to fetch [http://ec2-us-east-mirror3.rightscale.com/ubuntu_daily/2013/06/11/dists/precise/Release.gpg](http://ec2-us-east-mirror3.rightscale.com/ubuntu_daily/2013/06/11/dists/precise/Release.gpg)
W: Failed to fetch [http://ec2-us-east-mirror3.rightscale.com/ubuntu_daily/2013/06/11/dists/precise-updates/Release.gpg](http://ec2-us-east-mirror3.rightscale.com/ubuntu_daily/2013/06/11/dists/precise-updates/Release.gpg)
W: Failed to fetch [http://ec2-us-east-mirror3.rightscale.com/ubuntu_daily/2013/06/11/dists/precise-security/Release.gpg](http://ec2-us-east-mirror3.rightscale.com/ubuntu_daily/2013/06/11/dists/precise-security/Release.gpg)
W: Failed to fetch [http://cf-mirror.rightscale.com/rightscale_software_ubuntu/latest/dists/precise/Release.gpg](http://cf-mirror.rightscale.com/rightscale_software_ubuntu/latest/dists/precise/Release.gpg)
E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by tarekz on 2013-07-19
Turns out that there is something wrong with the s3 binary. 
I recompiled the source ([https://github.com/castlabs/apt-s3/](https://github.com/castlabs/apt-s3/)).

---

