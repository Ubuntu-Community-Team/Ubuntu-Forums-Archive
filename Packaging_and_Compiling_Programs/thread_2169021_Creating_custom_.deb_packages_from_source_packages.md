---
title: "Creating custom .deb packages from source packages"
date: 2013-08-20
forum: Packaging and Compiling Programs
---

### Post by invictus on 2013-08-20
Hi,

I am trying to create a custom package of a source bundle. In this specific case it is the current development version of Rsyslog without most of the optional modules (however, that should be irrelevant since this question is more generic). This means heavy customization of the ./configure options.

As this is a package that will conflict with the Ubuntu built-in Rsyslog package, I want the finished package (when installed) to install itself (with ALL dependencies... there are 2 additional source libraries) under /opt/rsyslog.

Is there any good tutorials on how to properly package source packages into .deb packages?

---

### Post by hamishmb on 2013-08-29
What you could do is something along the lines of:

./configure <options> && make && sudo checkinstall

This would then create a deb package. I've never used this, so I'm not entirely sur how to use it.
What I did was make the source tree and prepare it myself, to submit to launchpad. I'm not sure if you want to submit to launchpad, but anyhow here's the tutorial I used: [http://ubuntuforums.org/showthread.php?t=929498](http://ubuntuforums.org/showthread.php?t=929498) 

Hope this helps :)

---

