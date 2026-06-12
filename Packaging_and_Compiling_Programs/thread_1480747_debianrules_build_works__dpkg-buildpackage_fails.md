---
title: "debian/rules build works / dpkg-buildpackage fails"
date: 2010-05-11
forum: Packaging and Compiling Programs
---

### Post by agent8131 on 2010-05-11
Trying to build a package and I cannot figure out why running "debian/rules build" runs without error but "dpkg-buildpackage" fails with:

ld -Wl,-Bsymbolic-functions       -melf_x86_64   -melf_x86_64   -melf_x86_64 -r -o built_in.o head.o
ld: unrecognized option '-Wl,-Bsymbolic-functions'
ld: use the --help option for usage information

dpkg-buildpackage: error: debian/rules build gave error exit status 2

Can someone please explain what is different when dpkg-buildpackage calls "debian/rules build" compared to running "debian/rules build" from a shell?

Thanks.

---

### Post by SevenMachines on 2010-05-13
the difference between the two is described in steps in the manual page of dpkg-buildpackage, essentially before the various calls to debian/rules dpkg-buildpackage sets up environmental variables and checks all our dependencies. 
I'm guessing your problem is somewhere in your rules file but if you can post more information/files/output i'll try and take a better guess

> $man dpkg-buildpackage extract

1. It prepares the build environment  by  setting  various  environment
          variables (see ENVIRONMENT VARIABLES).

   2. It checks that the build-dependencies and build-conflicts are satis&#8208;
          fied (unless -d is specified).

       3. If a specific target has been  selected  with  the  -T  or  --target
          option,  it  calls  that  target  and stops here. Otherwise it calls
          fakeroot debian/rules clean to clean the build-tree (unless  -nc  is
          specified).

       4. It  calls  dpkg-source  to  generate  the  source  package (unless a
          binary-only build has been requested with -b, -B or -A).

       5. It  calls  debian/rules  build  followed  by  fakeroot  debian/rules
          binary-target  (unless  a  source-only build has been requested with
          -S). Note that binary-target is either binary (default case,  or  if
          -b is specified) or binary-arch (if -B is specified) or binary-indep
          (if -A is specified).

       6. It calls gpg to sign the .dsc file (if any,  unless  -us  is  speci&#8208;
          fied).

       7. It  calls  dpkg-genchanges  to generate a .changes file.  Many dpkg-
          buildpackage options are forwarded to dpkg-genchanges.

       8. It calls gpg to sign the .changes file (unless -uc is specified).

       9. If -tc is specified, it will call fakeroot debian/rules clean again.

---

