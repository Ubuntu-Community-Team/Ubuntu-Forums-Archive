---
title: "Building the latest rubygems into a debian package"
date: 2009-06-16
forum: Packaging and Compiling Programs
---

### Post by sbtiwari on 2009-06-16
Hi, 

This is the first time I am posting here. I am a complete newbie. I am aware its not a Debian Forum, but still, had to start somewhere.

My problem is that when I issue the 'apt-get install rubygems' command, the package that is installed is way too old, the version being 1.2.x. And when I install from source from the rubygems website, the package is the latest.

Is there a way to build the latest rubygems package into a debian package for my own usage?

Any help would be appreciated. I hope I have formed my question correctly.

Thanks!
Swati

---

### Post by InfinityCircuit on 2009-06-16
1.3.1 is in jaunty, 1.3.4 is in karmic. What version of Ubuntu are you running? Are those new enough for you?

---

### Post by mrtomservo on 2009-06-16
[http://www.linux.com/archive/articles/60383]("http://www.linux.com/archive/articles/60383")

Might be a good place to start, good luck!

---

### Post by sbtiwari on 2009-06-16
Hi,

Thanks for the help, but the above article assumed that the program that I am trying to build comes with a ./configure script.

I am trying to build rubygems into a package, the source of which does not come with a configure script. It comes with a ruby script.

Has anyone built rubygems 1.3.4 into a debian package or a package that does not come with a ./configure script?

Thanks for all the help, 
Swati

---

