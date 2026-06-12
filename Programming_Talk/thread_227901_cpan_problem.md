---
title: "cpan problem"
date: 2006-08-02
forum: Programming Talk
---

### Post by careca on 2006-08-02
from root shell i type: cpan
then i try to install CPAN module and i get error message

```
cpan> install CPAN
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Wed, 02 Aug 2006 05:29:49 GMT
Running install for module CPAN
Running make for A/AN/ANDK/CPAN-1.87.tar.gz
CPAN: Digest::MD5 loaded ok
Checksum for /root/.cpan/sources/authors/id/A/AN/ANDK/CPAN-1.87.tar.gz ok
Scanning cache /root/.cpan/build for sizes
CPAN-1.87/
CPAN-1.87/t/
CPAN-1.87/t/30shell.t
CPAN-1.87/t/50pod.t
CPAN-1.87/t/CPAN/
CPAN-1.87/t/CPAN/modules/
CPAN-1.87/t/CPAN/modules/02packages.details.txt
CPAN-1.87/t/CPAN/modules/03modlist.data
CPAN-1.87/t/CPAN/CpanTestDummies-1.55.pm
CPAN-1.87/t/CPAN/authors/
CPAN-1.87/t/CPAN/authors/id/
CPAN-1.87/t/CPAN/authors/id/A/
CPAN-1.87/t/CPAN/authors/id/A/AN/
CPAN-1.87/t/CPAN/authors/id/A/AN/ANDK/
CPAN-1.87/t/CPAN/authors/id/A/AN/ANDK/CHECKSUMS@588
CPAN-1.87/t/CPAN/authors/id/A/AN/ANDK/CPAN-Test-Dummy-Perl5-Build-Fails-1.01.tar.gz
CPAN-1.87/t/CPAN/authors/id/A/AN/ANDK/CPAN-Test-Dummy-Perl5-Make-Zip-1.01.zip
CPAN-1.87/t/CPAN/authors/id/A/AN/ANDK/CPAN-Test-Dummy-Perl5-BuildOrMake-1.01.tar.gz
CPAN-1.87/t/CPAN/authors/id/A/AN/ANDK/CPAN-Test-Dummy-Perl5-Make-Failearly-1.01.tar.gz
CPAN-1.87/t/CPAN/authors/id/A/AN/ANDK/CPAN-Test-Dummy-Perl5-Make-1.02.tar.gz
CPAN-1.87/t/CPAN/authors/id/A/AN/ANDK/CPAN-Test-Dummy-Perl5-Build-1.01.tar.gz
CPAN-1.87/t/CPAN/authors/id/A/AN/ANDK/CHECKSUMS
CPAN-1.87/t/CPAN/authors/id/A/AN/ANDK/NotInChecksums-0.000.tar.gz
CPAN-1.87/t/CPAN/authors/id/A/AN/CHECKSUMS
CPAN-1.87/t/CPAN/authors/id/A/CHECKSUMS
CPAN-1.87/t/CPAN/authors/id/CHECKSUMS
CPAN-1.87/t/CPAN/authors/01mailrc.txt
CPAN-1.87/t/CPAN/TestConfig.pm
CPAN-1.87/t/12cpan.t
CPAN-1.87/t/02nox.t
CPAN-1.87/t/01loadme.t
CPAN-1.87/t/10version.t
CPAN-1.87/t/03pkgs.t
CPAN-1.87/t/30shell.pod
CPAN-1.87/t/00signature.t
CPAN-1.87/t/README.shell.txt
CPAN-1.87/t/11mirroredby.t
CPAN-1.87/lib/
CPAN-1.87/lib/CPAN.pm
CPAN-1.87/lib/CPAN/
CPAN-1.87/lib/CPAN/Debug.pm
CPAN-1.87/lib/CPAN/FirstTime.pm
CPAN-1.87/lib/CPAN/Admin.pm
CPAN-1.87/lib/CPAN/Tarzip.pm
CPAN-1.87/lib/CPAN/Version.pm
CPAN-1.87/lib/CPAN/Nox.pm
CPAN-1.87/lib/CPAN/HandleConfig.pm
CPAN-1.87/inc/
CPAN-1.87/inc/Test/
CPAN-1.87/inc/Test/Builder.pm
CPAN-1.87/inc/Test/More.pm
CPAN-1.87/PAUSE2003.pub
CPAN-1.87/Changes
CPAN-1.87/MANIFEST
CPAN-1.87/scripts/
CPAN-1.87/scripts/cpan
CPAN-1.87/META.yml
CPAN-1.87/ChangeLog
CPAN-1.87/Changes.old
CPAN-1.87/ChangeLog.old
CPAN-1.87/MANIFEST.SKIP
CPAN-1.87/PAUSE2005.pub
CPAN-1.87/Todo
CPAN-1.87/SIGNATURE
CPAN-1.87/README
CPAN-1.87/Makefile.PL
Removing previously used /root/.cpan/build/CPAN-1.87

  CPAN.pm: Going to build A/AN/ANDK/CPAN-1.87.tar.gz

Importing PAUSE public key into your GnuPG keychain... done!
(You may wish to trust it locally with 'gpg --lsign-key 450F89EC')
Checking if your kit is complete...
Looks good
Writing Makefile for CPAN
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible

```

What's wrong?

---

### Post by ifokkema on 2006-08-04
Do you have 'make' installed?
Maybe this will help:
```
sudo apt-get install build-essential
```
Hope this helps!

---

