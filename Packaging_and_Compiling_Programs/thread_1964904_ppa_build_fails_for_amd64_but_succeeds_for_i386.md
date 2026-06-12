---
title: "ppa build fails for amd64 but succeeds for i386"
date: 2012-04-24
forum: Packaging and Compiling Programs
---

### Post by berndporr on 2012-04-24
I've created a debian source package and uploaded that to the launchpad ppa. It builds fine for i386 but fails for amd64:
[https://launchpadlibrarian.net/102997287/buildlog_ubuntu-precise-i386.comedirecord_1.22-2_BUILDING.txt.gz](https://launchpadlibrarian.net/102997287/buildlog_ubuntu-precise-i386.comedirecord_1.22-2_BUILDING.txt.gz)
[https://launchpadlibrarian.net/102999286/buildlog_ubuntu-precise-amd64.comedirecord_1.22-2_FAILEDTOBUILD.txt.gz](https://launchpadlibrarian.net/102999286/buildlog_ubuntu-precise-amd64.comedirecord_1.22-2_FAILEDTOBUILD.txt.gz)

the error is:
dpkg-shlibdeps: error: couldn't find library libcomedi.so.0 needed by debian/comedirecord/usr/bin/comedirecord (ELF format: 'elf32-i386'; RPATH: ''). dpkg-shlibdeps: error: couldn't find library libiir.so.1 needed by debian/comedirecord/usr/bin/comedirecord (ELF format: 'elf32-i386'; RPATH: ''). dpkg-shlibdeps: error: couldn't find library libQtGui.so.4 needed by debian/comedirecord/usr/bin/comedirecord (ELF format: 'elf32-i386'; RPATH: ''). dpkg-shlibdeps: error: couldn't find library libQtCore.so.4 needed by debian/comedirecord/usr/bin/comedirecord (ELF format: 'elf32-i386'; RPATH: ''). dpkg-shlibdeps: error: couldn't find library libpthread.so.0 needed by debian/comedirecord/usr/bin/comedirecord (ELF format: 'elf32-i386'; RPATH: ''). dpkg-shlibdeps: error: couldn't find library libstdc++.so.6 needed by debian/comedirecord/usr/bin/comedirecord (ELF format: 'elf32-i386'; RPATH: ''). dpkg-shlibdeps: error: couldn't find library libm.so.6 needed by debian/comedirecord/usr/bin/comedirecord (ELF format: 'elf32-i386'; RPATH: ''). dpkg-shlibdeps: error: couldn't find library libgcc_s.so.1 needed by debian/comedirecord/usr/bin/comedirecord (ELF format: 'elf32-i386'; RPATH: ''). dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/comedirecord/usr/bin/comedirecord (ELF format: 'elf32-i386'; RPATH: ''). 
seems so that shlibdeps is looking for the 32 bits libraries.

Any ideas why this is the case?

---

### Post by MadCow108 on 2012-04-26
is there something even building in those logs?
I don't see any output but maybe thats some qt thing.

if possible enable a verbose build, it might give some clues.
can you post a link to the source/ppa?

---

### Post by bregma on 2012-04-26
Are you by any chance trying to package a pre-built binary?  That's what the logs are telling me.  That will, of course, fail.

---

