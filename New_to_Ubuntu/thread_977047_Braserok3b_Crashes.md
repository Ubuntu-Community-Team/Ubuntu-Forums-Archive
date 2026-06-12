---
title: "Brasero/k3b Crashes"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Repubhippy on 2008-11-09
I am new to ubuntu and looking to troubleshoot an issue where Brasero, and K3B crash as soon as I try to add files to an audio CD.  THe Screen in Brasero goes black, I then have to force quit.  K3b refuses to recognize mp3 files.  I installed the additions (sudo apt-get install ubuntu-restricted-extras) Is there a place (like the Windows Event Log) That I can trouble shoot this.

I did find this in the syslog:
Nov  9 16:13:45 edLinux kernel: [338567.676307] brasero[24606]: segfault at 0 ip b70ba6df sp bfe83e0c error 6 in libpthread-2.8.90.so[b70b0000+15000]

Nov  9 16:14:05 edLinux kernel: [338587.640819] brasero[24632]: segfault at ffffffff ip b72b55d7 sp bfccfaa0 error 4 in libglib-2.0.so.0.1800.2[b725e000+b5000]

---

### Post by perlluver on 2009-01-07
I don't know if you have got it solved yet, but have you tried installing the K3B Extra Package?  You can find under System>Administration>Synaptic Package Manager, and search for K3B, and you will find the package.

---

