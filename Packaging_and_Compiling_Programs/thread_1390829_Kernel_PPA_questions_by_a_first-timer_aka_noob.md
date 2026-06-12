---
title: "Kernel PPA questions by a first-timer aka noob"
date: 2010-01-26
forum: Packaging and Compiling Programs
---

### Post by vishalrao on 2010-01-26
Attended the first couple of sessions of [http://ubuntuforums.org/showthread.php?t=1387651](http://ubuntuforums.org/showthread.php?t=1387651) and went ahead and did this: [http://ubuntuforums.org/showpost.php?p=8726150&postcount=5](http://ubuntuforums.org/showpost.php?p=8726150&postcount=5)

I followed whatever wiki pages I could to basically carry out the "bug fix" steps but the package being the linux kernel on lucid but wiki pages seem to be pending for kernels specifically :)

Looks like I don't have any beginner's luck on my side, hence some questions:

* When running "dch -i" it appears to modify debian/changelog but later on when doing "debuild -S" it appears to overwrite with standard debian.master/changelog causing loss of my changes. Probably same for the debian/control file (updating maintainers fields). What might I be doing wrong and how can I fix it?

* If I am able to build source packages, I created a "debdiff original.dsc new.dsc > new.debdiff" but this seems to only have changelog/control file changes. How can I generate/extract pure source code patch to show source changes? It's basically just 3 lines added to drivers/ata/libata-core.c :)

Thanks, if I need to post more info, please ask of course. And I will also post followup questions as I hope to get this built and test it on my own PC before announcing the PPA.

---

### Post by vishalrao on 2010-01-26
OK, the package in the PPA has finally built after a couple of attempts at trying to figure out the ABI-not-found and ABI-hash-check failures for generic and generic.modules.

Remaining questions/problems:

* When I built the package locally, even though the "version" I intended is 2.6.32-11.16~vishalrao3 it seems to be using regular 2.6.32-11.15 config/systemmap and the GRUB menu entry is also the older version even though "uname -a" shows the new version. How do I fix this?

* Would anyone care to review the package (_source.changes, .dsc and .diff.gz files) in my PPA for any glaringly obvious amateur mistakes.

FYI, this does resolve the SSD NCQ issue I have been facing. I hope to see if its just me or other users also facing such problems.

PPA location: [https://launchpad.net/~vishalrao/+archive/kernels](https://launchpad.net/~vishalrao/+archive/kernels)

---

