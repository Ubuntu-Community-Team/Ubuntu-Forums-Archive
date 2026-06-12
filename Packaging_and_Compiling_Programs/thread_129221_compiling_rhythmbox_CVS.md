---
title: "compiling rhythmbox CVS"
date: 2006-02-13
forum: Packaging and Compiling Programs
---

### Post by akurashy on 2006-02-13
well i give up i don't know what's wrong with this I have tried all, i have checked if i have the dev packages from repo and downloaded apart too, I can't compile rhythmbox 

It gives me this error 

checking for GSTREAMER_0_8... checking for GSTREAMER_0_10... configure: error: GStreamer not found, or older than version 0.8.2/0.9.7 

I have both installed =/ (of course i first installed one.. then it didn't detect it then installed another then well no success)

any ideas?

---

### Post by akurashy on 2006-02-13
Nevermind this have been resolved :D

---

### Post by zemex34 on 2007-02-19
How did you resolve this?

---

### Post by scrawl on 2008-03-20
That would interest me, too, I got the same problem :(

---

### Post by akurashy on 2008-03-21
For me to answer a 2 years old post is a bit insane... I remember uninstalling gstreamer deb package and recompiling it with the sources and it worked. 

Just so you go in the safe side.. check you have the -dev packages
libgstreamer0.10-dev 

else if you really really want gst then compile gstreamer from the scratch

---

### Post by bruce89 on 2008-03-21
Of course, now GNOME use Subversion.

---

