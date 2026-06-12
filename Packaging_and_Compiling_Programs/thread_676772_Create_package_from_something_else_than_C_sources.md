---
title: "Create package from something *else* than C sources ?"
date: 2008-01-24
forum: Packaging and Compiling Programs
---

### Post by TomG on 2008-01-24
Hi,

I created a modest application and I'd like to create .DEB package.
There are tons a tutorials or applications for that but the problem is that I only found stuff to create package from **C sources**.
But my application is coded in FreePascal and GTK.

So, how to create a .DEB from :
 - other language than C ?
and/or
 - from binary/compiled stuff ?
 
Thanks.
TomG

---

### Post by peabody on 2008-01-24
I'm no debian packaging expert, but from my understanding, the rules file can have just about anything put into it, doesn't have to be a configure script.

However, I believe you need to put some way to have the files copied to a fake installation root.  That root is then how the files get packaged up.

[http://doc.ubuntu.com/ubuntu/packagingguide/C/ch04s06.html](http://doc.ubuntu.com/ubuntu/packagingguide/C/ch04s06.html)

Just write your own script to do it rather than rely on make.

---

### Post by TomG on 2008-01-25
Will see this, Thx.

---

### Post by dholbach on 2008-01-29
Check out [http://wiki.ubuntu.com/PackagingGuide/Lists/ReferencePackages](http://wiki.ubuntu.com/PackagingGuide/Lists/ReferencePackages) and [http://wiki.ubuntu.com/PackagingGuide/Complete](http://wiki.ubuntu.com/PackagingGuide/Complete)

[http://doc.ubuntu.com/ubuntu/packagingguide/](http://doc.ubuntu.com/ubuntu/packagingguide/) is deprecated.

---

### Post by plugwash on 2008-01-30
the rules file that dh_make writes is just a template to get you started. The rules file is a makefile that can be modified to do whatever is nessacery to build the package. The build-stamp target (where you build the code if that is required) and the install-stamp target (where you copy the code into a directory tree and set permissions on it as if you were installing it) and the clean target (where you clean everything up afterwards) are the main ones you are likely to need to edit if your package does not have a makefile based build system.

It is possible (though not generally permitted by the main and universe sections of ubuntu and the main and contrib sections of debian, the exception being things like images that don't really have source) to have binaries in the orig.tar.gz . It is not possible to put binaries directly in the diff.gz but you can always uuencode them (decoding them as part of the build process and removing the decoded versions at the end of the build).

---

