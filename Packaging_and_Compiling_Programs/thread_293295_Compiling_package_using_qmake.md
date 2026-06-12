---
title: "Compiling package using qmake"
date: 2006-11-05
forum: Packaging and Compiling Programs
---

### Post by afoglia on 2006-11-05
*Never mind.  I realized that libqt3-mt-dev was not included.  (I mistakenly thought it was a dependency of some of the other build-depends.)*

I'm trying to create a deb package of a simple QT app.  (qpfstmo available at <[http://theplaceofdeadroads.blogspot.com/2006/07/qpfstmo-hdr-tone-mapping-gui-for-linux_04.html]("http://theplaceofdeadroads.blogspot.com/2006/07/qpfstmo-hdr-tone-mapping-gui-for-linux_04.html")>)  While I can configure and compile it easily in my directory, it fails when I run "sudo pbuilder build" on the dsc file.

I am including qt3-dev-tools and libqt3-headers as Build-Depends, and the config target in the rules file is set to run qmake.  The problem is the resulting Makefile compilation rule doesn't include the path /usr/include/qt3 needed for compilation.  I believe this is because the qmake process doesn't read the /usr/share/qt3/lib/libqt-mt.prl file.

I'm not familiar with qmake nor packaging (I'm closely following the procedure in the Packaging Guide); hopefully someone here can help.

---

