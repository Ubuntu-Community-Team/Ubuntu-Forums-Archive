---
title: "How does this get compiled? Python C Extension"
date: 2012-12-17
forum: Packaging and Compiling Programs
---

### Post by slimjimmrtim on 2012-12-17
Hi there, I want to learn how

tarball: [http://kaizer.se/publicfiles/keybinder/keybinder-3.0-0.3.0.tar.gz](http://kaizer.se/publicfiles/keybinder/keybinder-3.0-0.3.0.tar.gz)
homepages: [http://kaizer.se/wiki/keybinder/](http://kaizer.se/wiki/keybinder/)
github: [https://github.com/engla/keybinder](https://github.com/engla/keybinder)

gets compiled. Specifically I want to know about the python portion. It is a Python C extension. I want to learn because I hope to one day be able to make it work in Python 3.x (topic for another day).

Over the last few days I have written a few "hello world" type Python C-Extensions to try and learn the process, but doing so has hardly made a dent in my confusion.

Right now it seems as if a bunch of files are merged and linked which means I don't even really know what source it is I will need to be editing. It seems to me that several of the files are sort of merged at some point. And it seems like there are a lot of files that become auto generated and hardly human readable thus sometimes throwing me off. 

When I run

./configure
make
sudo make install

how do all these files come together to create something in /usr/local/lib/python2.7/dist-packages ?

I know this is a big topic, so, what can I do to teach myself?

Thank You.

---

