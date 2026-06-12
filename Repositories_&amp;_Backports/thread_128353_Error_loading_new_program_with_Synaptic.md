---
title: "Error loading new program with Synaptic"
date: 2006-02-11
forum: Repositories &amp; Backports
---

### Post by treyr on 2006-02-11
I receive the following error with any program I try to load / install with Synaptic. The same error appears with apt-get as well. Any idea's on where to go fix this?

E: /var/cache/apt/archives/ettercap-common_1%3a0.7.3-1_i386.deb: files list file for package `libfontconfig1-dev' is missing final newline

---

### Post by jchau on 2006-02-11
Seems like your ettercap-common package is corrupt (or maybe just badly made).  

Your error:
```
E: /var/cache/apt/archives/ettercap-common_1%3a0.7.3-1_i386.deb: files list file for package `libfontconfig1-dev' is missing final newline
```
makes me think that maybe when you downloaded the ettercap-common package, maybe you never finished downloading it (since it is just missing a '\n' character at the end of the file).  

Perhaps you can open Synaptic Package Manager.  Then select Edit -> Fix Broken Packages.  (I never used this option & I'm not sure what it does, but it sounds like if it does anything, it fixes this).

If that doesn't work, you can just delete the file ```
/var/cache/apt/archives/ettercap-common_1%3a0.7.3-1_i386.deb
```.  You don't really need to keep it (it is just a temporary file so you won't have to keep downloading it, and if you need it, Synaptic or apt-get, will automatically download it when you do (when you need to do something with the package)).

---

### Post by treyr on 2006-02-11
[QUOTE=jchau]Seems like your ettercap-common package is corrupt (or maybe just badly made).  

Your error:
```
E: /var/cache/apt/archives/ettercap-common_1%3a0.7.3-1_i386.deb: files list file for package `libfontconfig1-dev' is missing final newline
```
makes me think that maybe when you downloaded the ettercap-common package, maybe you never finished downloading it (since it is just missing a '\n' character at the end of the file).  

Perhaps you can open Synaptic Package Manager.  Then select Edit -> Fix Broken Packages.  (I never used this option & I'm not sure what it does, but it sounds like if it does anything, it fixes this).

If that doesn't work, you can just delete the file ```
/var/cache/apt/archives/ettercap-common_1%3a0.7.3-1_i386.deb
```.  You don't really need to keep it (it is just a temporary file so you won't have to keep downloading it, and if you need it, Synaptic or apt-get, will automatically download it when you do (when you need to do something with the package)).[/QUOTE]

It does this with any package I try to load / Install. My thinking is the problem is in the libfontconfig1-dev package, but I am not sure

---

### Post by treyr on 2006-02-15
The problem is with libfontconfig1-dev. I can't remove it and can't update it. Any suggestions?

---

