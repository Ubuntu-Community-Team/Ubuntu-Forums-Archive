---
title: "Error when building crosstool-ng-1.17.0"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by SHINYFATHIMA on 2013-01-11
When i am trying to build crosstool-ng-1.17.0 using ct-ng build i am getting the below error please help me to resolve this issue. Thanks in Advance.

shiny@ubuntu:~/crosstool-ng-1.17.0$ ct-ng build
[INFO ]  Performing some trivial sanity checks
[INFO ]  Build started 20130111.120042
[INFO ]  Building environment variables
[INFO ]  =================================================================
[INFO ]  Retrieving needed toolchain components' tarballs
[ERROR]   
[ERROR]  >>
[ERROR]  >>  Build failed in step 'Retrieving needed toolchain components' tarballs'
[ERROR]  >>        called in step '(top-level)'
[ERROR]  >>
[ERROR]  >>  Error happened in: do_cloog_get[scripts/build/companion_libs/cloog.sh@728]
[ERROR]  >>        called from: main[scripts/crosstool-NG.sh@543]
[ERROR]  >>
[ERROR]  >>  For more info on this error, look at the file: 'build.log'
[ERROR]  >>  There is a list of known issues, some with workarounds, in:
[ERROR]  >>      '/opt/crosstool-ng-1.17.0/share/doc/crosstool-ng/ct-ng.1.17.0/B - Known issues.txt'
[ERROR]   
[ERROR]  (elapsed: 1:38.73)
[01:39] / make: *** [build] Error 1
:D:D:D

---

