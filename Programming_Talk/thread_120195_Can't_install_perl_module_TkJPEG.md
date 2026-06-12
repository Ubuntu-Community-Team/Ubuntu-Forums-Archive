---
title: "Can't install perl module Tk::JPEG"
date: 2006-01-21
forum: Programming Talk
---

### Post by Boss Happy on 2006-01-21
Hi,
I'm very new to Ubuntu, and have been trying to get perl to install the Tk::JPEG module.  A program I'm trying to compile (vocpsystem) needs it.

I'm on Breezy Badger. I have the following packages:
perl-tk
libtk-img
libimage-info-perl

when I run: *sudo perl -MCPAN -e 'install Tk::JPEG'*

I get a lot of messages which end in:
[FONT="Courier New"][SIZE="2"]t/zzScrolled.................NOK 66# Test 66 got: "589x341+0+32" (t/zzScrolled.t at line 104 fail #2)
#    Expected: "589x341+0+0" (Sizechk: geometry has not changed not reset for -height => 24+(5))
#  t/zzScrolled.t line 104 is:             ok($newgeo, $oldgeo, "Sizechk: geometry has not changed not reset" .
t/zzScrolled.................NOK 94# Test 94 got: "589x341+17+32" (t/zzScrolled.t at line 104 fail #4)
#    Expected: "589x341+0+32" (Sizechk: geometry has not changed not reset for -width => 80+(5))
t/zzScrolled.................FAILED tests 66, 94
        Failed 2/94 tests, 97.87% okay
t/zzText.....................ok
t/zzTixGrid..................ok
Failed Test    Stat Wstat Total Fail  Failed  List of Failed
-------------------------------------------------------------------------------
t/JP.t            0    11   294  582 197.96%  4-294
t/zzScrolled.t               94    2   2.13%  66 94
 (3 subtests UNEXPECTEDLY SUCCEEDED), 23 subtests skipped.
Failed 2/47 test scripts, 95.74% okay. 293/2619 subtests failed, 88.81% okay.
make: *** [test_dynamic] Error 255
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force
[/SIZE][/FONT]

I've tried to run: *sudo perl -MCPAN -e 'force install Tk::JPEG'*
but it give the same results.

I did some digging on Bugzilla and didn't find anything.  I check on the forums and have found a handful of references to this same issue but no comments on how to resolve.

I also tried to install the rpm perl-Tk-JPEG-2.013-5.i386.rpm via *wajig rpminstall perl-Tk-JPEG-2.013-5.i386.rpm*  however this simply fails without any error messages.

Any and all assistance is greatly appreciated.  

Thanks, 
Jason

---

