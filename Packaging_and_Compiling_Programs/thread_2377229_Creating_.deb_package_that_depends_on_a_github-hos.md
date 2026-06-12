---
title: "Creating .deb package that depends on a github-hosted dependency"
date: 2017-11-10
forum: Packaging and Compiling Programs
---

### Post by n0vafacing on 2017-11-10
I have some programs I'd like to create a .deb package for, and I'm currently using checkinstall to do so. The package is created without a problem, but it isn't installing the dependencies properly. I've tried several ways to remedy this, and none have worked:
-Have the entire installation sequence in configure script
-Have the entire installation sequence in Makefile (more on this below, slight issue here)
-Have the installation sequence in a separate shell script that is called from the Makefile
The issues with each of these have been as follows:
-The configure script way doesn't seem to be executing, and if it is it is not as sudo. I am installing keyczar from google, so for installation purposes this does need to be done as sudo. But basically, the repo never gets cloned, the shared libraries are never copied, nothing.
-The Makefile way didn't seem to want to work at all, like above nothing happened as far as cloning or copying/running the hammer.sh installer from keyczar.
-The third one was the same as both above. 
Now, the real kicker is that this process works perfectly if I just cd into the containing directory and do ./configure && make && sudo make install, which makes me think that it's something up with me not setting the right parameters on checkinstall (or maybe checkinstall is the wrong utility for my use case). I've RTFM'ed checkinstall and I'm pretty sure I'm doing it properly, but any general info on how to install a dependency that's from git has to happen would be much appreciated, because google has no answers and neither does my Linux development book.

---

### Post by ian-weisser on 2017-11-10
You seem to be using the deb format for a purpose it was not designed for.

debs are not generic packages. They are intended to be used in a very specific way.
debs may *only* depend upon other debs. Non-deb dependencies are not permitted.

One solution is to also package the dependencies.
Another solution is to shift to dependencies that are already packaged.
Another solution is to use a different packaging format that is less strict than deb...like Snappy or AppImage.

---

### Post by n0vafacing on 2017-11-10
Hmm, after reading some more specification it seems you're right. I didn't think about packaging the dependency as well, so I'm going to give that a try.

---

### Post by Ravi_ on 2018-02-17
I need git 2.10.3 deb package. I can install using tar download however i need deb package so that i can install using puppet scripts.
Can any one help to create a deb package for git 2.10.3.

---

