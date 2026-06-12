---
title: "Can't view DVD"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Nasa01 on 2008-10-30
Hi

For some reason I cant view DVDs on either my laptop nor on my desktop. Both hav Ubuntu 8.04 installed.

When I insert a DVD i get the following error message from Totem: "An eroor occurred, can't read from resource". I tried installing VLC but it also does not work.

Any ideas??

Cheers.

---

### Post by Interpreter on 2008-10-30
Just to avoid misunderstandings, I take it you got your codecs right and set and blah blah?
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")
If not do so, otherwise please let us know ;)

---

### Post by Zeedok on 2008-10-30
Have you tried following the instructions on this wiki page:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I think the crucial package is libdvdcss2, but to get it you'll have to add the medibuntu repositories.

Hope that helps - oh, by the way, to get DVD menus working properly you'll need to remove the totem-gstreamer package (in synaptic) and install totem-xine instead.

Have fun.

---

