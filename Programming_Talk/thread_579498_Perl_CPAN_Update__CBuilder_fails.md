---
title: "Perl CPAN Update / CBuilder fails"
date: 2007-10-18
forum: Programming Talk
---

### Post by pkn on 2007-10-18
I have installed a fresh gutsy and want to update perl modules first.

```
sudo perl -MCPAN -e shell
```

I performed the default init configuration as usual.
As I first step I want to update the CPAN Bundle as suggested. But this fails right within the first dependency module CBuilder.

It seems as if there are some basics missing (usr/bin/ld: crti.o: No such file: No such file or directory)
anyone has a clue what might help?

Here is the output of CBuilder install:

```
cpan> install ExtUtils::CBuilder
Running install for module ExtUtils::CBuilder
Running make for K/KW/KWILLIAMS/ExtUtils-CBuilder-0.19.tar.gz
  Is already unwrapped into directory /home/andreas/.cpan/build/ExtUtils-CBuilder-0.19

  CPAN.pm: Going to build K/KW/KWILLIAMS/ExtUtils-CBuilder-0.19.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for ExtUtils::CBuilder
cp lib/ExtUtils/CBuilder.pm blib/lib/ExtUtils/CBuilder.pm
cp lib/ExtUtils/CBuilder/Platform/Windows.pm blib/lib/ExtUtils/CBuilder/Platform/Windows.pm
cp lib/ExtUtils/CBuilder/Platform/aix.pm blib/lib/ExtUtils/CBuilder/Platform/aix.pm
cp bleadcheck.pl blib/lib/ExtUtils/bleadcheck.pl
cp lib/ExtUtils/CBuilder/Platform/cygwin.pm blib/lib/ExtUtils/CBuilder/Platform/cygwin.pm
cp lib/ExtUtils/CBuilder/Platform/VMS.pm blib/lib/ExtUtils/CBuilder/Platform/VMS.pm
cp lib/ExtUtils/CBuilder/Platform/Unix.pm blib/lib/ExtUtils/CBuilder/Platform/Unix.pm
cp lib/ExtUtils/CBuilder/Platform/darwin.pm blib/lib/ExtUtils/CBuilder/Platform/darwin.pm
cp lib/ExtUtils/CBuilder/Platform/os2.pm blib/lib/ExtUtils/CBuilder/Platform/os2.pm
cp lib/ExtUtils/CBuilder/Platform/dec_osf.pm blib/lib/ExtUtils/CBuilder/Platform/dec_osf.pm
cp lib/ExtUtils/CBuilder/Base.pm blib/lib/ExtUtils/CBuilder/Base.pm
Manifying blib/man3/ExtUtils::CBuilder::Platform::Windows.3pm
Manifying blib/man3/ExtUtils::CBuilder.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/01-basic....ok 1/11/usr/bin/ld: crti.o: No such file: No such file or directory
collect2: ld returned 1 exit status
error building /tmp/compilet.so from /tmp/compilet.o at /home/andreas/.cpan/build/ExtUtils-CBuilder-0.19/blib/lib/ExtUtils/CBuilder/Base.pm line 212.
# Failed test 3 in t/01-basic.t at line 26
#  t/01-basic.t line 26 is: ok $b->have_compiler;
t/01-basic....NOK 3/11/usr/bin/ld: crti.o: No such file: No such file or directory
collect2: ld returned 1 exit status
error building t/compilet.so from t/compilet.o at /home/andreas/.cpan/build/ExtUtils-CBuilder-0.19/blib/lib/ExtUtils/CBuilder/Base.pm line 212.
t/01-basic....dubious                                                        
        Test returned status 25 (wstat 6400, 0x1900)
DIED. FAILED tests 3, 8-11
        Failed 5/11 tests, 54.55% okay
t/02-link.....ok 1/5/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
error building t/compilet from t/compilet.o at /home/andreas/.cpan/build/ExtUtils-CBuilder-0.19/blib/lib/ExtUtils/CBuilder/Base.pm line 212.
t/02-link.....dubious                                                        
        Test returned status 25 (wstat 6400, 0x1900)
DIED. FAILED tests 4-5
        Failed 2/5 tests, 60.00% okay
Failed Test  Stat Wstat Total Fail  List of Failed
-------------------------------------------------------------------------------
t/01-basic.t   25  6400    11    9  3 8-11
t/02-link.t    25  6400     5    4  4-5
Failed 2/2 test scripts. 7/16 subtests failed.
Files=2, Tests=16,  0 wallclock secs ( 0.20 cusr +  0.23 csys =  0.43 CPU)
Failed 2/2 test programs. 7/16 subtests failed.
make: *** [test_dynamic] Error 25
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force

cpan>
```

---

