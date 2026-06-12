---
title: "Problems with putty  apt-get on Ubuntu 12.04.5"
date: 2015-07-14
forum: New to Ubuntu
---

### Post by yand on 2015-07-14
My server Ubuntu 12.04.5 LTS (GNU/Linux 3.2.0-87-generic x86_64)then I wanna install the ubuntu-desktop, 
first, i run
```
apt-get update
```

I get this
```
Err http://us-west-2.clouds.archive.ubuntu.com precise Release.gpg  Temporary failure resolving 'us-west-2.clouds.archive.ubuntu.com'
Err http://security.ubuntu.com precise-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err http://us-west-2.clouds.archive.ubuntu.com precise-updates Release.gpg
  Temporary failure resolving 'us-west-2.clouds.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://us-west-2.clouds.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Temporary failure resolving 'us-west-2.clouds.archive.ubuntu.com'


W: Failed to fetch http://us-west-2.clouds.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Temporary failure resolving 'us-west-2.clouds.archive.ubuntu.com'


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Temporary failure resolving 'security.ubuntu.com'


W: Some index files failed to download. They have been ignored, or old ones used instead.



```

Any idea what is happening and how to fix it?
Thanks

---

### Post by Anakondarh on 2015-07-15
Hi yand, and welcome to Ubuntu and the Ubuntu Forums.

The problem you're having means that your system can't reach the online repositories to download the latest software info. Notice the "Failed to fetch" and "Temporary failure resolving" messages.

Because of the "failure resolving" message, it seems like some sort of DNS issue, meaning the system doesn't know how to convert those URLs to IP addresses.

Possible causes:

1) The sites were down when you tried. Unlikely.
2) Your system can't reach the Internet. Much more likely. Can you copy here the output of ```
ping -c 2 google.com
```? This command will try to ping (see if it can reach and get a response back) google.com. The "-c 2" flag will make it try only twice.

This ping test is one of the easiest ways to quickly see if your system is actually connected to the Internet or not.

Post the output and we can go from there.

---

