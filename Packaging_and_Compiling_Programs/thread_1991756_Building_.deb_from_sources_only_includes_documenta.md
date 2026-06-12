---
title: "Building .deb from sources only includes documentation"
date: 2012-05-30
forum: Packaging and Compiling Programs
---

### Post by Shelnutt2 on 2012-05-30
Long time gentoo users. I've made my share of ebuilds but I've decided to great a .deb for the hfm.net application which is used for monitoring folding@home clients. It's a mono/.net application. I converted it to a makefile system successfully and it compiles fine. When you run make install, it properly install into /usr/local/. However after following the coomplete [packaging]("https://wiki.ubuntu.com/PackagingGuide/Complete") guide I built my .deb fine and my source file. However I soon realized my .deb only included the documentation /usr/share/doc/hfm.net and not the binary or libraries in /usr/local/bin and /usr/local/lib/hfm.net . I'm quite confused at what the issue is because it builds fine, there are no errors from debuild yet the .deb doesn't include the actual binaries.


I've got my source uploaded to a ppa.
[https://launchpad.net/~shelnutt2/+archive/hfm.net](https://launchpad.net/~shelnutt2/+archive/hfm.net)

Any ides or help would be appreciated.

---

### Post by Bachstelze on 2012-05-30
Normally, your makefile should install files into $(DESTDIR)$(prefix) (as opposed to just $(prefix), as it seems to be doing). This is because for the packaging process, the files need to be installed in a special subdir of the work directory (from which the package will be built), not on the actual system.

Alternatively, use a .install file...

---

### Post by Shelnutt2 on 2012-05-31
As far as I can tell all the installs in the makefile are prefixed with $(DESTDIR) and them either $(libdir) or $(prefix).

Maybe I'm missing where I should be looking? 
How would I go about using a .install file with debuild? I don't see it in the man page or in the documentation. That might be easiest.

edit:

The problem lies in the fact that I was not starting from the source dir. I was one layer up because there are some 3rd party libraries that were needed. So what was actually happening was that no makefiles were being run. I'm rearranging everything to be 1 top level dir, so sources can be build like debuild expects.

---

