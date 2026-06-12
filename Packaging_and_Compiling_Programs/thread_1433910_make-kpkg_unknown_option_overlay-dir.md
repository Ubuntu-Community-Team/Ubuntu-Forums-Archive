---
title: "make-kpkg unknown option: overlay-dir"
date: 2010-03-19
forum: Packaging and Compiling Programs
---

### Post by pbrane on 2010-03-19
I am trying to compile 2.6.33 kernel using this guide
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")
and I want to use the Ubuntu kernel configuration. However make-kpkg doesn't seem to have the *--overlay-dir* option anymore. Anyone have any ideas on how to accomplish this build?

---

### Post by gomyhr on 2010-03-22
> **pbrane said:**
> I am trying to compile 2.6.33 kernel using this guide
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")
and I want to use the Ubuntu kernel configuration. However make-kpkg doesn't seem to have the *--overlay-dir* option anymore. Anyone have any ideas on how to accomplish this build?

It looks like it's the other way around... make-kpkg doesn't seem to have the *--overlay-dir* option *yet*. It seems it is only available in Lucid. From [https://launchpad.net/ubuntu/+source/kernel-package/+changelog](https://launchpad.net/ubuntu/+source/kernel-package/+changelog) on Available diffs: 11.015 to 12.032, search for "overlay", and you'll find:

```

+kernel-package (12.006) unstable; urgency=low
+
+  * [9fe0183]: Added a new feature: overlay directory
+    This commits add an overlay feature. The specified directory should
+    contain files that will be placed in the ./debian directory of the
+    kernel sources, in preparation to building the debian packages,
+    replacing the files normally found in /usr/share/kernel-package. Inn
+    theory, this should provide all the features official kernel images
+    might need to use kernel-package, without any formal support from
+    kernel-package. It should also address the need for any users that
+    needed to add content to ./debian, and more conveniently than before. 
+
+ -- Manoj Srivastava <srivasta@debian.org>  Mon, 13 Apr 2009 01:27:49 -0500

```

Since this is in the diff from the Karmic version to the Lucid version, I suppose it's only available in Lucid. I see from your profile page [http://ubuntuforums.org/member.php?u=459043](http://ubuntuforums.org/member.php?u=459043) that you're on Karmic.

---

### Post by pbrane on 2010-03-23
Oh good point. I hadn't thought of that. I assumed that the page had just been updated for lucid. That explains everything. Thanks.

---

