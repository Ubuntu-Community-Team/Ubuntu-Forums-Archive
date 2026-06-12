---
title: "i am trying to package openssl 1.0.2h for trusty/amd64"
date: 2016-05-26
forum: Packaging and Compiling Programs
---

### Post by nevbear666 on 2016-05-26
hello ubuntu community,

i am trying to package openssl for trusty/amd64 for my launchpad ppa, and i am having problems getting it packaged.

ive been following this tutorial:

[http://packaging.ubuntu.com/html/packaging-new-software.html](http://packaging.ubuntu.com/html/packaging-new-software.html)

trying to build inside of an lxc container. the hello project builds fine, unfortunately openssl 1.0.2h with all 1.0.2g patches deployed doesnt.

it went on for a while and finally threw me a diff into my tmp directory in the container.

i am guessing that i am missing some packet, as this has been the reason it broke earlier. i finally had that find.pl containing packet installed, and now it goes on for a while longer, but still breaks.

the difference is, either i am blind or i am not seeing what its telling me this time as error.

heres the full diff (ps: i couldnt attach, diff is bigger than the allowed limit for that kind of file):

[http://pastebin.com/7b8w70M7](http://pastebin.com/7b8w70M7)

any help is highly appreciated
thanks in advance

---

### Post by nevbear666 on 2016-05-27
do you need additional info?

---

