---
title: "Ubuntu kernel compilation error"
date: 2016-01-04
forum: Packaging and Compiling Programs
---

### Post by chick2 on 2016-01-04
Is this the right place to ask questions about compiling the Ubuntu kernels?  I've been compiling with the BFQ scheduler, but it seems that I'm always running into a problem with the ABIs which lead to an error that looks like this

```

debian/rules.d/4-checks.mk:3: recipe for target 'abi-check-generic' failed

```

My process for obtaining and compiling is this:

```
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-wily.git
git branch bfq
git checkout bfq
chmod a+x debian/scripts/*
chmod a+x debian/scripts/misc/*
./debian/scripts/misc/getabis 4.2.0 22.27
nano debian.master/changelog (I modify the version to indicate that I've added the bfq code) 
patch -p1 --ignore-whitespace -i 0001-block-cgroups-kconfig-build-bits-for-BFQ-v7r9-4.2.patch 
patch -p1 --ignore-whitespace -i 0002-block-introduce-the-BFQ-v7r9-I-O-sched-for-4.2.patch 
patch -p1 --ignore-whitespace -i 0003-block-bfq-add-Early-Queue-Merge-EQM-to-BFQ-v7r9-for-4.2.0.patch 
fakeroot debian/rules clean
fakeroot debian/rules editconfigs
fakeroot debian/rules binary-headers binary-generic
```

It would be nice to do a `git pull` or 'git rebase` to just update my copy of the code, and I think that is the intention...  But when I do that, I am no longer able to recompile without getting the error described above.  Can someone with better understanding of the compile process than I currently have, educate me please?

---

### Post by Bucky Ball on 2016-01-04
*Thread closed*.
[URL="http://ubuntuforums.org/showthread.php?t=2308636"]
Duplicate here[/URL]. Please do not post duplicates. Thanks.

---

