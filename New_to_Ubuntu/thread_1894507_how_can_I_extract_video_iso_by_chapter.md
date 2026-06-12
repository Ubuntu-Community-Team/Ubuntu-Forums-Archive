---
title: "how can I extract video iso by chapter?"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by mimihu88 on 2011-12-12
I've tried something like:
"mplayer input.iso -chapter 1-1 -v -dumpstream -dumpfile output.vob"
but it always extract the entire iso to a big vob file not the chapter 1.
Anyone can help?
Thanks in advance!

P.S: I want a _**command line **_

After some more try I've solved the problem by modify the command line as below:
mplayer -chapter 1-1 -v -dumpstream -dumpfile output.vob -dvd-device input.iso dvd://1

---

### Post by jtarin on 2011-12-12
[Maybe follow this thread.]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2006-October/063365.html")

dvdnav could be what your looking for.

---

