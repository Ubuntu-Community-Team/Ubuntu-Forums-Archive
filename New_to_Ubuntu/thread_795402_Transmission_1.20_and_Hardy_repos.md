---
title: "Transmission 1.20 and Hardy repos"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by aimpau on 2008-05-15
According to their website, they already have 1.20 whereas the updated repos have only upto 1.06. Why is this so? I don't know how to compile "sources" of linux type. Am I doing something wrong with the repos?

---

### Post by drs305 on 2008-05-15
> **aimpau said:**
> According to their website, they already have 1.20 whereas the updated repos have only upto 1.06. Why is this so? I don't know how to compile "sources" of linux type. Am I doing something wrong with the repos?

No. The repositories take a while (or sometimes longer) to get updated. You can go to other sources to obtain the latest version or wait for the repositories to get the newest version.

---

### Post by Paqman on 2008-05-15
Nope, you're fine. The repos don't always have the latest versions that are available. If you want to stay more current, try enabling the "backports" repo (although this won't be terribly useful since Hardy is so new)

For now, GetDeb has [Transmission 1.20](http://www.getdeb.net/search.php?keywords=transmission).

Compiling from source just to get the latest version isn't recommended, by the way. Always try to install through the package manager, so that you'll keep getting updates and the dependencies remain intact.

---

### Post by aimpau on 2008-05-15
How do I do that? I've tried the main server and still no updated version.

edit:
Ok. I'll wait for it then through apt-get.
thanks!

---

### Post by Paqman on 2008-05-16
GetDeb is a site which offers pre-packaged .deb files, which are what you get from the repos. Just go to the site, download the .deb you want and click on it. It's a lot like the Windows .exe installation method.

---

### Post by kpkeerthi on 2008-05-16
> **aimpau said:**
> According to their website, they already have 1.20 whereas the updated repos have only upto 1.06. Why is this so? I don't know how to compile "sources" of linux type. Am I doing something wrong with the repos?

Ubuntu will NOT continuously keep its repositories up-to-date with upstream releases, except for security patches. 

Read up on the gory details here...
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

