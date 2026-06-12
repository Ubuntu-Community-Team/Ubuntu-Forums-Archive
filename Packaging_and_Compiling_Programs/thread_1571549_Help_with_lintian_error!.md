---
title: "Help with lintian error!"
date: 2010-09-09
forum: Packaging and Compiling Programs
---

### Post by hakermania on 2010-09-09
missing-dependency-on-libc needed by ./usr/bin/some
I created a file named shlibs in /DEBIAN containing
gcc -Wl /lib/libc.so
but new error comes: pkg-has-shlibs-control-file-but-no-actual-shared-libs
What do I do wrong? that you in advance!

---

### Post by dodle on 2010-09-10
You can check out the lintian tags explanations here: [http://lintian.debian.org/tags.html](http://lintian.debian.org/tags.html)

Here are the explanations of the specific errors that you mentioned:
[missing-dependency-on-libc](http://lintian.debian.org/tags/missing-dependency-on-libc.html)
[pkg-has-shlibs-control-file-but-no-actual-shared-libs](http://lintian.debian.org/tags/pkg-has-shlibs-control-file-but-no-actual-shared-libs.html)

It looks like you do not need the [color=red]shlibs[/color] file in the [color=blue]DEBIAN[/color] directory, but you need to add [color=red]${shlibs:Depends}[/color] to the [color=red]Depends[/color] line in [color=red]DEBIAN/control[/color].

---

### Post by SevenMachines on 2010-09-10
/DEBIAN suggests to me that you are manually creating a deb archive file rather than packaging the source. These two things are very different and it'll be unsurprising that lintian will complain if you're doing the first. It's a much better idea to look over the packaging guide in the forum stickies and properly 'debianize', its easier (usually :) ) than it looks and only needs to be done once!

---

