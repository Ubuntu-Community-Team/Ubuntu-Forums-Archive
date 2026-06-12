---
title: "Perl Beginner Problem"
date: 2011-04-19
forum: Programming Talk
---

### Post by lorenz_b on 2011-04-19
Hi Folks,

I have a small problem here:

I have a list of files in an array @list_of_files. When comparing this list to the content (files) of a certain directory, how can I obtain another array @other_files with the files in that directory, that do not match the files in @list_of_files.

It is probably a simple task to do for experienced programmers.

cheers,
Lorenz

---

### Post by gmargo on 2011-04-19
Presumably you have already considered the simplest, albeit compute-intensive, solution of just rescanning @list_of_files for every entry of the directory list.  For shorter lists this is probably fine.  For a longer list, try translating your @list_of_files into a hash (associative array) that can be indexed simply.

Crude example:
```

#!/usr/bin/perl -w
use strict;
use warnings;

my @list_of_files = ("one", "two", "three");
my @directory_list = ("three", "four", "five");

my %hash_of_files;
$hash_of_files{$_}++ foreach (@list_of_files);

my @other_files;
foreach (@directory_list)
{
    push @other_files, $_ unless $hash_of_files{$_};
}
print "Other Files: @other_files\n";


```Output:
```

$ perl listtest.pl 
Other Files: four five

```

---

### Post by lorenz_b on 2011-04-22
thank you very much, worked fine!!

best, Lorenz

---

