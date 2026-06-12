---
title: "Make dpkg-source include removal of debian files in diff?"
date: 2009-05-19
forum: Packaging and Compiling Programs
---

### Post by wdaniels on 2009-05-19
Hi, I'm trying to build a package where upstream are distributing the beginnings of some debian packaging in the release tarballs.

Though I'm going to try to get them to stop doing that, I'm not too sure how to deal with it in the meantime. The problem is that dpkg-source ignores my deletion of the original files under debian when generating the diff and I couldn't find any option that will pursuade it otherwise.

Eventually, I just converted the package to a 3.0 (quilt) format because that will delete debian from the orig tarball anyway when unpacking the source, and everything seemed fine until I tried to upload it to a launchapd PPA and discovered that I can only use format 1.0 there :(

I've never done much packaging really, so I'm sure I must be missing some simple solution. I'd rather not start removing the offending files ad-hoc from the rules script and google hasn't been much help so far, so I thought perhaps it's best to jusk ask how people usually deal with this situation...any help much appreciated!

---

