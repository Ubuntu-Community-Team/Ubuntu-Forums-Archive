---
title: "libmp3lame.so[.0] is nowhere to be found..."
date: 2006-10-19
forum: Packaging and Compiling Programs
---

### Post by Contrast on 2006-10-19
I'm trying to get this library so that Audacity can export .mp3 files. I looked through the threads relating to this, and couldn't find anything relating to my situation, as I'm 100% certain the lib actually isn't on my computer (In all of the other threads, the lib was already installed, and it was just a matter of the user finding it). I tried locating it through the terminal, the package manager, and Konqueror, all to no avail. I downloaded and extracted the tarball for lame-3.97, and it contains libmp3lame_vc6.dsp and libmp3lame_vc7.dsp in its libmp3lame subfolder, but I have no idea what to do with these. I took a look at the Wiki-How on the C compiler and tried following a couple of its steps, resulting in a very long list of errors. In case it's not obvious enough, I'm a newbie to Linux, and have virtually no knowledge of the command line, or anything else in this regard for that matter. Any help on this subject that keeps that in mind would be greatly appreciated.

---

### Post by baccaruda on 2006-10-26
I had the same problem, I read a thread ( I cant find it again now ) that fixed it..

From Synaptic Packet Manager I installed both

liblame0 and liblame-dev

then (despite still not seeing the file) just pointed the request box for libmp3lame.so to

/usr/lib/

that worked for me.

---

### Post by Contrast on 2006-10-27
Cool, I'll try that once this Edgy update finishes installing.

---

