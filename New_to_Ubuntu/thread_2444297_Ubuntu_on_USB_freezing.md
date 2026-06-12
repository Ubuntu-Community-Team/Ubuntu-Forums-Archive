---
title: "Ubuntu on USB freezing"
date: 2020-05-28
forum: New to Ubuntu
---

### Post by tit-elmund on 2020-05-28
Dear forumers,
I have a little request if anyone could help me. I have a full install of Ubuntu on a 64 GB USB 3.0 SanDisk flashdrive (350 MB/s + read/write) and from time to time, it freezes up for up to 12 seconds. I have a full install of just Ubuntu on the drive with a boot, main and swap partition, the swap partition is 4 GB, the same size as my RAM. Could anyone suggest a fix for the unresponsiveness?

I also heard that the -ck kernel pathes could help - could anyone please point me to a layman's guide to installing them (even if it doesn't help, I would like to try them out, the relevant info and PPAs I found are pretty much outdated)? I am using Ubuntu MATE 18.04.4 LTS i686. The kernel is 5.3.0-28 generic i686.

Thank you very much.

---

### Post by dino99 on 2020-05-28
First  you might find the reason(s): 'journalctl -b' and 'System Monitor Processes' should point to a bottleneck.
When you get a short freeze, is it due to special action ? (transfer/load/graphic/...)
I suppose some harware limitations are in the place: the flashdrive is 3.0, but what about the connected port ?
Anyway there is a race somewhere between usb/port/ram/bus

---

### Post by tit-elmund on 2020-05-29
Okay, what should I look out for when checking journalctl? The short freezes are random, maybe they appear more often when copying files or performing software installs. Anyway, the port is fine, it is a 3.0 port and copying works at the usbs rated speed. What about the -ck patches?

---

### Post by tit-elmund on 2020-05-29
This is what comes up consistently when freezing:
maj 29 15:43:56 Tit-Lenovo-ideapad-330-17AST pulseaudio[1553]: [pulseaudio] shm.c: mmap() failed: Pomnilnika ni mogo&#269;e dodeliti
maj 29 15:43:56 Tit-Lenovo-ideapad-330-17AST pulseaudio[1553]: [pulseaudio] protocol-native.c: Disabling srbchannel, reason: Failed to allocate shared writable memory pool.
maj 29 15:43:56 Tit-Lenovo-ideapad-330-17AST pulseaudio[1553]: [pulseaudio] shm.c: mmap() failed: Pomnilnika ni mogo&#269;e dodeliti
maj 29 15:43:56 Tit-Lenovo-ideapad-330-17AST pulseaudio[1553]: [pulseaudio] pstream.c: Failed to create permanent mapping for memfd region with ID = 2113341418
maj 29 15:43:56 Tit-Lenovo-ideapad-330-17AST pulseaudio[1553]: [pulseaudio] pstream.c: Ignoring received block reference with non-registered memfd ID = 2113341418
maj 29 15:43:56 Tit-Lenovo-ideapad-330-17AST pulseaudio[1553]: [pulseaudio] pstream.c: Ignoring received block reference with non-registered memfd ID = 2113341418
maj 29 15:43:56 Tit-Lenovo-ideapad-330-17AST pulseaudio[1553]: [pulseaudio] pstream.c: Ignoring received block reference with non-registered memfd ID = 2113341418

---

### Post by dino99 on 2020-05-30
Looks like you hit a pulseaudio/canberra problem 

Maybe you can open a report on [https://gitlab.freedesktop.org/pulseaudio/pulseaudio/-/issues?scope=all&utf8=%E2%9C%93&state=opened](https://gitlab.freedesktop.org/pulseaudio/pulseaudio/-/issues?scope=all&utf8=%E2%9C%93&state=opened)
with above output and a hardware description (got via lshw) to help the pulse team.

---

