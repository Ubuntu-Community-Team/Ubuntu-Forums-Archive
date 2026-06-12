---
title: "mplayer with ordered chapter support..."
date: 2009-10-10
forum: Packaging and Compiling Programs
---

### Post by xanas3712 on 2009-10-10
I'm looking for something that works, and so far rvm's packages don't work (gray screen for video, no audio decoding) so I'm also trying to compile a version that has this and vdpau.

In theory the git should have this so I'm using the one at repo.or.cz/mplayer-build.git

I'm running into problems building this though.

[http://pastebin.com/m1b8c0a85](http://pastebin.com/m1b8c0a85) is the link to the messages I'm getting when following the compilation instructions.  I have no idea what the deal is.  Whether I run the make -j 9 or the provided debian package builder I get the same errors.

It seems to be a problem with autoconf but I have no idea how I can resolve it.  Google hasn't been very helpful thus far.

---

### Post by xanas3712 on 2009-10-10
Ehh, I answer my own questions half the time... but since I'm a moron and others may be stupid like me I'll post what I found instead of removing the post

Basically I should have looked for similar errors on google, because when I did I found out that I didn't have libtool installed.  I also installed yasm based on another mplayer thread.  These things aren't installed by build-dep but are apparently quite important.  Once they were installed I had no trouble compiling (something this 8-virtual core i7 920 monster is great at doing) 

It seems a little glitchy but it otherwise works, so the git definitely has the ordered chapter support I was looking for.

---

