---
title: "How do I resolve this error: Temporary failure resolving 'gb.archive.ubuntu.com'"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by T0990 on 2012-06-08
Hello, I am a real beginner and I am trying to make an ubuntu web server (12.04) , whilst attempting to type > sudo aptitude update && sudo aptitude dist-upgrade I received this error (after i had typed my password) :) :
> 
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise InRelease
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
0% [Connecting to gb.archive.ubuntu.com] [Connecting to security.ubuntu.com]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates InRelease
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
[INDENT]Temporary failure resolving 'security.ubuntu.com'[/INDENT]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports IRelease
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precis Release.gpg
[INDENT]Temporary failure resolving 'gb.archive.ubuntu.com[/INDENT]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg
[INDENT]Temporary failure resolving 'gb.archive.ubuntu.com'[/INDENT]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release.gpg
[INDENT]Temporary failure resolving 'gb.archive.ubuntu.com'[/INDENT]
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dist/precise/InRelease](http://gb.archive.ubuntu.com/ubuntu/dist/precise/InRelease)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-backports/InRelease](http://security.ubuntu.com/ubuntu/dists/precise-backports/InRelease)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg) Temporary failure resolving 'gb.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise/Release.gpg) Temporary failure resolving 'security.ubuntu.com'

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/release.gpg) Temporary failure resolving 'gb.archive.ubuntu.com'

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg) Temporary failure resolving 'gb.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.

No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used


I don't know what this means, so i assumed it could be to do with my internet connection and so I tried 
>  ping security.ubuntu.com

and it replied back with:

> ping: unknown host security.ubuntu.com

How should I resolve this issue?

Any help would be great.

Many Thanks

---

### Post by T0990 on 2012-06-08
Sorry, I don't actually know whether the ping will work anyway as I haven't set up the web services yet... i am just starting the server and so attempting to update aptitude before I start downloading

---

### Post by stmiller on 2012-06-08
Can you ping localhost?

What is your /etc/resolv.conf ? This is where DNS servers are specified which might be the problem.

---

### Post by drs305 on 2012-06-08
It could simply be that the repository's server is temporarily unavailable. You can either wait or change servers.

You can change the server via Software Sources. From the Ubuntu Software Center, Edit > Software Sources, Ubuntu Software tab.  Change "Download from" to another source. If you have a lot of updates you could select 'Other' and Select Best Server.

---

