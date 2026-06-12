---
title: "Which packages depend on/recommend this package?"
date: 2009-03-03
forum: Repositories &amp; Backports
---

### Post by Stochastic on 2009-03-03
Is there any easy way to find which packages in the Ubuntu repository rely on or recommend a particular package?

---

### Post by bapoumba on 2009-03-05
Maybe [http://packages.ubuntu.com](http://packages.ubuntu.com) is what you are looking for. Example with gedit : [http://packages.ubuntu.com/intrepid/gedit](http://packages.ubuntu.com/intrepid/gedit)

---

### Post by WatchingThePain on 2009-03-05
Hi,
ldd prints the shared libraries required by each program or shared library specified on the command line.

---

### Post by Stochastic on 2009-04-22
To give an update (I knew I hadn't explained it clear enough):

apt-rdepends -reverse packagename

is what I was looking for.

---

### Post by ashmew2 on 2009-04-27
If you want to download the dependencies for a specific package , give build-dep a try..
```

sudo apt-get -d build-dep <package name>
```

---

### Post by skagedal on 2013-04-27
Thank you for answering your own question, I was looking for the answer to this and what I found was this thread.

However, apt-rdepends --reverse did not work for me, for some reason. It claimed it was unable to locate the package in question (libpeas-1.0.0).

Instead, I found this:

```
apt-cache rdepends packagename
```

That worked for me.

---

### Post by lisati on 2013-04-27
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

