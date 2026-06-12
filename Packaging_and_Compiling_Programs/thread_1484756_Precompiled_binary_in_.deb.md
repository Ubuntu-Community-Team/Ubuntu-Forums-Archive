---
title: "Precompiled binary in .deb"
date: 2010-05-16
forum: Packaging and Compiling Programs
---

### Post by BalleClorin on 2010-05-16
I'm packaging a python application which depends on ffmpeg. The upstream maintainer insists on using a precompiled ffmpeg. I know I shouldn't do that, but this is temporary until I can make launchpad build a ffmpeg with the same configure line as the included precompiled one.

I can get the file copied into the correct place using debian/install, but somehow it gets corrupted. The 2.8 mb file gets reduced to 208 bytes. accoring to file it is still a 32bit elf binary though. I have already ruled out dh_strip and upload error as source. I also had a theory about dh_install treating the file wrong because it went into an invalid path for a binary, but I tried putting it in /usr/bin but with the same results.

Again, I know that this is a BAD thing to do, but as I said, it's only temporary, and the package will only stay in a PPA, it will not be uploaded to Ubuntu.

Anybody have any thoughts about why this happens?

---

### Post by BalleClorin on 2010-05-20
bump

---

### Post by SevenMachines on 2010-05-21
> **BalleClorin said:**
> Again, I know that this is a BAD thing to do
yes, yes it is :)

building an altered ffmpeg package shouldnt be difficult though

on the problem you're having, do you have a link to your ppa package or can you post the source & packaging if possible, it'd easier to tell whats happening that way

---

### Post by BalleClorin on 2010-05-22
Here's the latest build with the corrupted binary:
[https://launchpad.net/~damnvid/+archive/ppa/+build/1737910](https://launchpad.net/~damnvid/+archive/ppa/+build/1737910)

I'm working on the ffmpeg package, eventually I'll get there...

---

### Post by BalleClorin on 2010-05-23
Never mind, I overcame the problems I had with the ffmpeg build. But I'd still like to know why this happened though, if anybody knows…

---

