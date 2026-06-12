---
title: "How to make Opera work with 64-bit?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by dnns123 on 2008-05-08
The only versions are Sparc, PowerPC and i386
Do I download the Sparc?
I have an Ubuntu 64-bit running under an Intel 2.4GHz core 2 duo

---

### Post by sy88 on 2008-05-08
No, SPARC is something else entirely.  Get the i386 version.

---

### Post by dnns123 on 2008-05-08
i got the .deb but it says i have the wrong architechure...

---

### Post by sy88 on 2008-05-08
Woops, is it 32 bit?  You're looking for a 64 bit version.  I'm not sure about their website but have you tried using apt-get?  apt-get should steer you in the right architecture.

Actually, it's probably better that you use apt-get rather than using the .deb files.

---

### Post by dnns123 on 2008-05-08
I dont see the Opera Web Browser in the synaptic package manager.

---

### Post by dnns123 on 2008-05-08
nevermind, i give up...

---

### Post by Sef on 2008-05-08
There is a [64-bit version of Opera]("ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/").  It is a beta version, 9.5. Just click on the bottom one (.deb.)

---

### Post by dnns123 on 2008-05-08
Thanks, but now i have a prob:
This is what it says in the terminal

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
Segmentation fault

---

### Post by dnns123 on 2008-05-08
Nevermind, i found the new version and it looks sexy. Just the way people said it was.

---

