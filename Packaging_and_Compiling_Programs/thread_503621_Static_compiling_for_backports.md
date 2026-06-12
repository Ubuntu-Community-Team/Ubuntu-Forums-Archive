---
title: "Static compiling for backports"
date: 2007-07-18
forum: Packaging and Compiling Programs
---

### Post by 3rdalbum on 2007-07-18
I'd like to backport some new programs to Ubuntu 6.06. I have successfully compiled and packaged Pidgin, Audacity 1.3.3, and a couple of other programs for Dapper in a Dapper virtual machine.

I'm having trouble with compiling Abiword. It requires libwv 1.2 (and I assume libwv-dev) to compile, but although there's a "wv" package, that doesn't help the compiling at all.

I can take the libwv-1.2 package from Feisty and use it with Abiword, but what if there were lots of dependencies that were not present in Dapper? Could I statically compile them in, without dragging in hundreds of megabytes of other supporting libraries? The last thing I want to do is inadvertently create a Debian package that you could burn to a CD and boot from :-)

I use Feisty as my host OS, running Dapper inside a VM.

---

