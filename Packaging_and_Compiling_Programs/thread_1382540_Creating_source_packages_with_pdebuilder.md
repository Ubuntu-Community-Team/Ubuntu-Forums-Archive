---
title: "Creating source packages with pdebuilder"
date: 2010-01-16
forum: Packaging and Compiling Programs
---

### Post by slakkie on 2010-01-16
Hello to all,

I'm currently busy with packaging and I'm running into a smallish problem. For a PPA upload I need the *_source.{changes,dsc} files. But my pdebuild didn't create these files.

According to [http://pbuilder.alioth.debian.org/#sourcechanges](http://pbuilder.alioth.debian.org/#sourcechanges) pdebuild doesn't create a source package when using --use-pdebuild-internal. 

How do I solve this?

1) Is there another command that tells pdebuild to create the *_source.* files even when I use --use-pdebuild-internal?
2) Do I need to use hooks to satisify the (build-)dependencies and don't use --use-pdebuild-interal?
3) Some other method of doing this? 

Btw, I'm running on Debian testing, so simply adding jaunty sources in my sources.list and running build-dep isn't an option.

---

### Post by SevenMachines on 2010-01-16
i tend to use debuild directly then test the resulting package using pbuilder but for pdebuild you might want to try
$pdebuild --debbuildopts -S
which should generate the changes file

---

### Post by slakkie on 2010-01-16
Thanks, I will give that a try.

---

### Post by slakkie on 2010-01-18
That worked like a charm, thank you very much.

---

