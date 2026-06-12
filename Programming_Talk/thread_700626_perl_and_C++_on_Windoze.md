---
title: "perl and C++ on Windoze"
date: 2008-02-18
forum: Programming Talk
---

### Post by DouglasAWh on 2008-02-18
can anybody tell me what the below means?

> 
cpan> install DBD::ADO
Running install for module 'DBD::ADO'
Running make for S/SG/SGOELDNER/DBD-ADO-2.96.tar.gz
CPAN: Digest::SHA loaded ok (v5.45)
CPAN: Compress::Zlib loaded ok (v2.008)
Checksum for C:\Perl\cpan\sources\authors\id\S\SG\SGOELDNER\DBD-ADO-2.96.tar.gz
ok
Scanning cache C:\Perl/cpan/build for sizes
............................................................................DONE

CPAN: Archive::Tar loaded ok (v1.38_01)
DBD-ADO-2.96/
DBD-ADO-2.96/Changes
DBD-ADO-2.96/ex/
DBD-ADO-2.96/ex/Enums.patch
DBD-ADO-2.96/ex/Local/
DBD-ADO-2.96/ex/Local/DBD/
DBD-ADO-2.96/ex/Local/DBD/ADO/
DBD-ADO-2.96/ex/Local/DBD/ADO/DSN.pm
DBD-ADO-2.96/ex/OpenSchema.pl
DBD-ADO-2.96/ex/Provider.pl
DBD-ADO-2.96/lib/
DBD-ADO-2.96/lib/DBD/
DBD-ADO-2.96/lib/DBD/ADO/
DBD-ADO-2.96/lib/DBD/ADO/Const.pm
DBD-ADO-2.96/lib/DBD/ADO/GetInfo.pm
DBD-ADO-2.96/lib/DBD/ADO/TypeInfo.pm
DBD-ADO-2.96/lib/DBD/ADO.pm
DBD-ADO-2.96/Makefile.PL
DBD-ADO-2.96/MANIFEST
DBD-ADO-2.96/MANIFEST.SKIP
DBD-ADO-2.96/META.yml
DBD-ADO-2.96/README
DBD-ADO-2.96/t/
DBD-ADO-2.96/t/01base.t
DBD-ADO-2.96/t/02ads.t
DBD-ADO-2.96/t/02cxn.t
DBD-ADO-2.96/t/04os.t
DBD-ADO-2.96/t/05gi.t
DBD-ADO-2.96/t/06ti.t
DBD-ADO-2.96/t/07q.t
DBD-ADO-2.96/t/11prep.t
DBD-ADO-2.96/t/12bind.t
DBD-ADO-2.96/t/12ins_b.t
DBD-ADO-2.96/t/12ins_q.t
DBD-ADO-2.96/t/13count.t
DBD-ADO-2.96/t/14rows.t
DBD-ADO-2.96/t/15large.t
DBD-ADO-2.96/t/18bc.t
DBD-ADO-2.96/t/19misc.t
DBD-ADO-2.96/t/21sth.t
DBD-ADO-2.96/t/23null.t
DBD-ADO-2.96/t/25curs.t
DBD-ADO-2.96/t/27lob.t
DBD-ADO-2.96/t/29timeout.t
DBD-ADO-2.96/t/31txn.t
DBD-ADO-2.96/t/41ddtbl.t
DBD-ADO-2.96/t/42ddcol.t
DBD-ADO-2.96/t/43ddpk.t
DBD-ADO-2.96/t/44ddfk.t
DBD-ADO-2.96/t/45ddst.t
DBD-ADO-2.96/t/51qi.t
DBD-ADO-2.96/t/DBD_TEST.pm
DBD-ADO-2.96/ToDo
CPAN: File::Temp loaded ok (v0.18)

  CPAN.pm: Going to build S/SG/SGOELDNER/DBD-ADO-2.96.tar.gz

Argument "6.42_01" isn't numeric in numeric ge (>=) at Makefile.PL line 27.

Configuring DBD::ADO ...

>>> Remember to actually *READ* the README file!
>>> And re-read it if you have any problems.

*** You're using Microsoft Visual C++ compiler or similar but
    the LIB and INCLUDE environment variables are not both set.

    You need to run the VCVARS32.BAT batch file that was supplied
    with the compiler before you can use it.

    A copy of vcvars32.bat can typically be found in the following
    directories under your Visual Studio install directory:
        Visual C++ 6.0:     vc98\bin
        Visual Studio .NET: vc7\bin

    Find it, run it, then retry this.

    If you think this error is not correct then just set the LIB and
    INCLUDE environment variables to some value to disable the check.
Warning: No success on command[C:\Perl\bin\perl.exe Makefile.PL]
Warning (usually harmless): 'YAML' not installed, will not store persistent stat
e
  SGOELDNER/DBD-ADO-2.96.tar.gz
  C:\Perl\bin\perl.exe Makefile.PL -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
Could not read 'C:\Perl\cpan\build\DBD-ADO-2.96-MAljWe\META.yml'. Falling back t
o other methods to determine prerequisites
Failed during this command:
 SGOELDNER/DBD-ADO-2.96.tar.gz                : writemakefile NO 'C:\Perl\bin\pe
rl.exe Makefile.PL' returned status 65280


again, unfortunately, this is on Windows

---

### Post by aks44 on 2008-02-18
The message says it all...
> **DouglasAWh said:**
> CPAN.pm: Going to build S/SG/SGOELDNER/DBD-ADO-2.96.tar.gz

[...]

*** You're using Microsoft Visual C++ compiler or similar but
the LIB and INCLUDE environment variables are not both set.

You need to run the VCVARS32.BAT batch file that was supplied
with the compiler before you can use it.

A copy of vcvars32.bat can typically be found in the following
directories under your Visual Studio install directory:
Visual C++ 6.0: vc98\bin
Visual Studio .NET: vc7\bin

Find it, run it, then retry this.


FYI, the Visual C++ compiler needs some environment variables to be set when running from a terminal. VCVARS32.BAT sets those environment variables according to your installation paths.

---

### Post by DouglasAWh on 2008-02-18
Why am I using C++ though?  I'm just trying to install a Perl module.  I don't understand at all.  Why the hell is installing a module so effing difficult?  

How do I make these variables in C++?  I've never touched anything C++.  I hate MSDE, Wasp and Windows.

---

### Post by aks44 on 2008-02-18
> **DouglasAWh said:**
> Why am I using C++ though?
Looks like the module you're installing needs to compile some C(++) code.

If you have MS Visual C++ installed, just run the mentioned .bat
If you don't have it... well you gotta either install it or go back to Linux... ;)

> **DouglasAWh said:**
> I don't understand at all.  Why the hell is installing a module so effing difficult?
On Linux, the GCC compilers are considered part of the default install for any developer, which makes their use "transparent".
On Windows, you need additional tools that are not part of the base system.

---

### Post by DouglasAWh on 2008-02-20
I had so many problems with that other machine that I set up another XP box to start over from scratch using the ActiveState MSI.  I tried installing through CPAN, but I still get errors saying various things such as "Make had returned a bad status, install seems impossible."

can anyone shed some light on what is going on?  The version of ActivePerl is 5.10.0.1002.

---

