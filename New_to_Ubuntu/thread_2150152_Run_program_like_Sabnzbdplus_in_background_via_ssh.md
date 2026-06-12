---
title: "Run program like Sabnzbdplus in background via ssh and disconnect"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by verbin on 2013-05-31
Hey Ubuntu users,

I wanted to know how to run a program like sabnzbdplus via ssh and disconnect from ssh and let the program run on the background?

When i now ssh to my machine i can run sabnzbdplus but when i try to close my ssh session sabnzbdplus stops.

---

### Post by sanderj on 2013-05-31
Most easy solution: run SABnzbd as a daemon (service) on Ubuntu. See [http://wiki.sabnzbd.org/install-ubuntu-repo](http://wiki.sabnzbd.org/install-ubuntu-repo) . Problem solved.

---

### Post by SlugSlug on 2013-05-31
Above is best. But for other things you want to run and disconnect you can use either 'screen' or 'nohup'

---

