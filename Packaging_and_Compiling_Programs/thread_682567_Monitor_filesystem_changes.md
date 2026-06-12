---
title: "Monitor filesystem changes"
date: 2008-01-30
forum: Packaging and Compiling Programs
---

### Post by MarkusThielmann on 2008-01-30
I'm trying to create a small script, which "translates" a commercial installer for a closed source product into a simple to maintain .deb package.

In order to make sure that I do not miss any changes the installer makes, I'm in need for a simple method for tracking the installers changes to the filesystem.

Any ideas?

---

### Post by stroyan on 2008-01-30
You can get information about file system access with the strace command.
But it won't be really simple to find the interesting system calls among the rest.
The strace command uses ptrace.  That it will prevent setuid programs from changing uid.
```
strace -f -e trace=file -o logfile installer-command
```

---

### Post by SanskritFritz on 2008-01-30
I would make a snapshot of the filesystem (ls -R or similar) before and after the install. Then I would simply compare the results.

---

