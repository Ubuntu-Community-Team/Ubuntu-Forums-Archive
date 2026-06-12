---
title: "How would i play a .mp3 or .ogg from python?"
date: 2009-04-05
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-04-05
well how would i? google returns a couple libs, but i was wondering which you would advise and some tutorial on how to use them

---

### Post by vambo on 2009-04-05
For .ogg have a look at python-pyvorbis - it's in the repo's. The examples section has a prog called ogg123, which is quite instructive. Hope this bit helps. Don't know about mp3's I'm afraid.

---

### Post by jimi_hendrix on 2009-04-05
that works, thanks

---

### Post by cabalas on 2009-04-05
Another option is to look at the python bindings for gstreamer which is also in the repos.

This site has most of the information that you would need.

[http://pygstdocs.berlios.de/](http://pygstdocs.berlios.de/)

---

### Post by imdano on 2009-04-05
> **cabalas said:**
> Another option is to look at the python bindings for gstreamer which is also in the repos.

This site has most of the information that you would need.

[http://pygstdocs.berlios.de/](http://pygstdocs.berlios.de/)Take a look at [Exaile's](http://www.exaile.org) source code if you want a real world example, that's what they use in their backend.

---

### Post by SledgeHammer_999 on 2009-04-05
I also suggest gstreamer+python bindings.

---

### Post by kostkon on 2009-04-05
+1 for Gstreamer...

---

### Post by jimi_hendrix on 2009-04-05
> **cabalas said:**
> Another option is to look at the python bindings for gstreamer which is also in the repos.

This site has most of the information that you would need.

[http://pygstdocs.berlios.de/](http://pygstdocs.berlios.de/)

i tried downloading from svn, i went to make and it got errors and about not connecting to SF

---

### Post by kostkon on 2009-04-05
Why not use [the ones from the repos]("http://packages.ubuntu.com/search?keywords=python-gst0.10&searchon=names&suite=all&section=all"), as already suggested.

---

