---
title: "Exclude files when packaging"
date: 2010-08-12
forum: Packaging and Compiling Programs
---

### Post by MrQuincle on 2010-08-12
Dear all,

After using checkinstall for a while for local use, I have been creating packages via:
[list]
[*]dh_make -e [email]my@email.com[/email] --createorig
[*]debuild -S -kMYKEY
[*]sudo pbuilder build mypackage.dsc
[*]dput ppa:robot3d-team/ppa-robot3d mypackage*.changes
[/list]

I am wondering, when and how do I **exclude files**? I want to exclude at least the .bzr files. I really like Bazaar by the way! 

When I read the Packaging guide at [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete) there are only some rather vague CDBS exclude variables. But I am not packaging using cdbs, I just used dh_make -l (shared library).

Thanks in advance!

Anne

---

### Post by SevenMachines on 2010-08-13
I've used DH_ALWAYS_EXCLUDE before with svn files well enough. sould do the trick
from man debhelper
>     DH_ALWAYS_EXCLUDE
           If set, this adds the value the variable is set to to the -X
           options of all commands that support the -X option. Moreover,
           dh_builddeb will rm -rf anything that matches the value in your
           package build tree.

           This can be useful if you are doing a build from a CVS source tree,
           in which case setting DH_ALWAYS_EXCLUDE=CVS will prevent any CVS
           directories from sneaking into the package you build. Or, if a
           package has a source tarball that (unwisely) includes CVS
           directories, you might want to export DH_ALWAYS_EXCLUDE=CVS in
           debian/rules, to make it take effect wherever your package is
           built.

           Multiple things to exclude can be separated with colons, as in
           DH_ALWAYS_EXCLUDE=CVS:.svn


---

