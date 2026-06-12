---
title: "Increasing size limit for perl variable"
date: 2008-11-15
forum: Programming Talk
---

### Post by pardeepluna on 2008-11-15
Hi All.. 

Please direct me if i have posted on wrong thread . 

I want to know , How can we increase the size limit for perl variable.

$size = <stdin>

here while i am trying to give more than 256 char in the stdin i am getting output after terminating first 256.i.e i am getting output as 256 onward.

---

### Post by nvteighen on 2008-11-15
> **pardeepluna said:**
> Hi All.. 

Please direct me if i have posted on wrong thread . 

I want to know , How can we increase the size limit for perl variable.

$size = <stdin>

here while i am trying to give more than 256 char in the stdin i am getting output after terminating first 256.i.e i am getting output as 256 onward.

Er... Are you sure? I've entered a ~320 char long string and no problem...

---

### Post by unutbu on 2008-11-15
[PHP]#!/usr/bin/perl
use strict;
use warnings;

my $size=<STDIN>;
my $len=length($size);
print "$len\n",;
print "$size\n"[/PHP]
Can you show us your code? I'm unable to reproduce the problem.

---

### Post by indecisive on 2008-11-15
I can not replicate it either.  One principle of Perl is "No Unnecessary Limits," so I doubt that problem is genuine.  Perl's variables should, after all, be as large as necessary until they fill the memory.

---

