---
title: "Clean and easy Cinelerra install on Dapper"
date: 2006-06-11
forum: Outdated Tutorials &amp; Tips
---

### Post by franck.galbrun on 2006-06-11
Just follow this blog post:
[http://www.kiberpipa.org/~gandalf/blog/?p=47](http://www.kiberpipa.org/~gandalf/blog/?p=47)

It consists of activating universe and multiverse, and add the following repos:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./
then, depending of your architecture:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./
or
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/) ./
or
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/) ./

And then of course, update your package list and install cinelerra with synaptic or apt-get.

---

