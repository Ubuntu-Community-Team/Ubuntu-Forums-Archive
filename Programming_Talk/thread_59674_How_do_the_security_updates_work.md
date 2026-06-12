---
title: "How do the security updates work"
date: 2005-08-24
forum: Programming Talk
---

### Post by bob k on 2005-08-24
I come from the old school where we left a chunk of memory at the end of a module for patches and inserted a jmp to the patch area where the patch was located and did a return.

As I understand it now the os has become somewhat modulerized, do they remove the module and insert a new module with corrections, and if they do, how do they handel linkage.

I ask this because after patching this and that with a few os patches, the system becomes sluggish and a reinstall with the current image seems to resolve this issue.

Bob

---

### Post by toojays on 2005-08-30
The security updates in Ubuntu just replace every file in the package with new files. An update for a particular program doesn't actually take effect until you restart the program.

This isn't going to slow down individual programs, but I can imagine scenarios where it could slow down the whole computer until the next time you login.

The method you describe makes sense when you are patching binaries, and want the patch size to be small. But in the Free Software world, we tend to just patch the source code, recompile it, and ship a brand new executable to the customer.

Dynamic linking is performed at runtime by a program called ld.so. You can read the man page of this program to get an overview of what it does. The runtime linker is capable of dealing with many kinds of changes to shared libraries, but like I mentioned above, it is only invoked when a program is first started---patches to most running programs in Ubuntu will only take effect then the program is restarted.

---

### Post by bob k on 2005-09-01
Thanks that's what I was looking for. Reading the kernal documents, they didn't talk about real-time linkage. This will get me to the right path.

Bob

---

