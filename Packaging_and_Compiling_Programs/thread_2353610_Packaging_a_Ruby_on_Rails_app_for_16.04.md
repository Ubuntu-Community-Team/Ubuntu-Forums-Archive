---
title: "Packaging a Ruby on Rails app for 16.04"
date: 2017-02-23
forum: Packaging and Compiling Programs
---

### Post by sbutton on 2017-02-23
Hi,

I'm trying to work out how to turn a RoR app into a .deb package. This should be fairly simple, as there's no actual "compile" step needed for Ruby, but I'm getting lost with the amount of options. I've been looking at pkgr, but this only supports up to 14.04. I've also looked at Mina and git-buildpackage, but these seem too compllicated for what I need. Really, I just want to take my existing git repo which I've downloaded and turn that into a .deb file, which will overwrite anything already there with a newer version. 

Hope that makes sense.

Thanks,

Steve Button

---

### Post by sbutton on 2017-02-28
Having looked into this a bit further, and particularly after reading through [this]("https://www.debian.org/doc/manuals/packaging-tutorial/packaging-tutorial.en.pdf") tutorial, I can see that using "dpkg-deb --build" is the way to go for this.

---

