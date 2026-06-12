---
title: "Perl Sort"
date: 2007-09-21
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-09-21
I have a bunch of log files stored in an array that I need to sort.  In code, looks like this:

@files = sort(@files);
foreach $_ (@files)
{
     print $_;
}

which prints:

log1.txt
log10.txt
log11.txt
log2.txt
log3.txt
...
log9.txt

Issue is that I want log10.txt and log11.txt to come after log9.txt.  Anyone know how to do this?  The default sort routine sorts by comparing character by character and does not really understand the ordering of numbers within an alphanumeric text.

---

### Post by slavik on 2007-09-21
define your own compare subroutine and call sort as such:
sort \&comapare @files. or you can rename files to have 2 digits.

---

### Post by eph1973 on 2007-09-21
Although, there may be a more clever solution, this one here works, assuming the only files you want to ensure get sorted out like that are named "log<number>.txt".  Otherwise it would treat other named files just like a regular sort.
```

#!/usr/bin/perl

use strict;

my %logHash;
my @sortedLogs;
my @noLogs;
sub byValues { $logHash{$a} <=> $logHash{$b} }

while(<>) {
    chomp;
    if(/^log\d+\.txt$/){
        /\d+/;
        $logHash{$_} = int $&;
    } else {
        push(@noLogs, $_);
    }
}

@noLogs = sort @noLogs;
@sortedLogs = sort byValues keys %logHash;

if(@noLogs){
    for(@noLogs){
        if($_ lt $sortedLogs[0] && @sortedLogs) {
            print "$_\n";
        } elsif(@sortedLogs) {
            while(@sortedLogs){
                my $logName = shift @sortedLogs;
                print "$logName\n";
            }
            print "$_\n" if @noLogs;
        } else {
            print "$_\n";
        }
    }
} else {
    for(@sortedLogs) {
        print "$_\n";
    }
}

```

---

### Post by ghostdog74 on 2007-09-22
> **SNYP40A1 said:**
> I have a bunch of log files stored in an array that I need to sort.  In code, looks like this:

@files = sort(@files);
foreach $_ (@files)
{
     print $_;
}

which prints:

log1.txt
log10.txt
log11.txt
log2.txt
log3.txt
...
log9.txt

Issue is that I want log10.txt and log11.txt to come after log9.txt.  Anyone know how to do this?  The default sort routine sorts by comparing character by character and does not really understand the ordering of numbers within an alphanumeric text.
look at perldoc -q sort
> 
  How do I sort an array by (anything)?

       Supply a comparison function to sort() (described in "sort" in perlfunc):

           @list = sort { $a <=> $b } @list;

       The default sort function is cmp, string comparison, which would sort "(1, 2, 10)" into "(1, 10, 2)".  "<=>", used above, is the
       numerical comparison operator.




---

