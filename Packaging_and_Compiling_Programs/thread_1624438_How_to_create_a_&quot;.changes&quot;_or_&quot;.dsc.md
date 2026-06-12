---
title: "How to create a &quot;.changes&quot; or &quot;.dsc&quot; files?"
date: 2010-11-17
forum: Packaging and Compiling Programs
---

### Post by aullidolunar on 2010-11-17
Hi!

I'd like to upload my deb to my launchpad ppa account.
My files are in:

**/home/me/program-0.1/src**

and my makefile is on the parent level:

**/home/me/program-0.1/makefile**

the compilations is correct and I can easly generate the deb using this:

**dpkg-deb --build program-0.1**

Can you help me generate ".changes" and ".dsc" files?

Thanks

---

### Post by SevenMachines on 2010-11-18
dpkg-deb isn't the thing to use for packaging up your software, as it describes itself, its a 'Debian package archive (.deb) manipulation tool'. Thats why it looks for a DEBIAN directory used by .deb packages rather than the lower case debian directory that is used when actually building a package. 
In your source directory you can run

> # Build a debian package but dont sign it
$ debuild -b -us -uc 

# Build source and sign it, this is what you want to upload to a ppa
$ debuild -S

---

