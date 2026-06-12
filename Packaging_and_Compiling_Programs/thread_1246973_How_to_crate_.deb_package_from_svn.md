---
title: "How to crate .deb package from svn?"
date: 2009-08-22
forum: Packaging and Compiling Programs
---

### Post by vikjon0 on 2009-08-22
I am trying to learn how to package for Ubuntu / Debian.
I have found the guides on how to build from a tar and it looks within reach.
What I want to do it is to build the latest version from svn. Is that possible and if so where do I find info?

The only thing I could find was this
debuild -us -uc -i -I
But it gives:
cannot find readable debian/changelog anywhere!
Are you in the source code tree?

I know the source is ok because I have done make & make install.
Am I on the right track or do I need to start with the stable tar and patch it? (Do not know how to do that) 

Thankful for any clues on where to start reading.

---

### Post by arky on 2009-08-23
You need to create the changelog file.

[https://wiki.ubuntu.com/PackagingGuide/HandsOn#changelog](https://wiki.ubuntu.com/PackagingGuide/HandsOn#changelog)

---

### Post by vikjon0 on 2009-08-23
Ok, I better make sure I have/create all files described in the guide for packing a tar then. Good to know.

I think I will have to make a few test runs inside the scope of the guide before I try something new.

Thanks,

---

