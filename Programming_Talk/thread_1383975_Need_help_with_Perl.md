---
title: "Need help with Perl"
date: 2010-01-17
forum: Programming Talk
---

### Post by Puzzled Guy on 2010-01-17
Hi

I have a program for renaming files. I give it all the proper input but it doesn't seem to work.
This is the program:
```

#!/usr/bin/perl

use strict;
use warnings;

my($dir, $oldpat, $newpat);
print "Directory: ";
chomp($dir=<STDIN>);
print "Old pattern: ";
chomp($oldpat=<STDIN>);
print "New pattern: ";
chomp($newpat=<STDIN>);

opendir(DH, $dir) || die "Cannot open $dir: $!";
my @files=readdir DH;
close(DH);

my $oldname;
foreach(@files) {
    $oldname=$_;
    s/$oldpat/$newpat/;
    next if (-e "$dir/$_");
    if (! rename "$dir/$oldpat", "$dir/$_") {
        warn "Could not rename $oldname to $_: $!";
    } else {
        print "File $oldname renamed to $_\n";
    }
}

```

Here is the input and the resulting output:
```

hope@Hope-Laptop:~/Desktop/Perl$ perl renamer.pl
Directory: /home/hope/Desktop/Perl
Old pattern: uni
New pattern: bi
Could not rename uniword.pl to biword.pl: No such file or directory at renamer.pl line 24, <STDIN> line 3.
hope@Hope-Laptop:~/Desktop/Perl$

```

---

### Post by jpkotta on 2010-01-18
If you're just looking for a renaming solution, use the rename command.
```
rename s/uni/bi/ *
```

The bug is that you should use $oldname in the rename line.

---

### Post by Puzzled Guy on 2010-01-18
Could you please post the corrected line?

---

### Post by Axos on 2010-01-18
if (! rename "$dir/$old**name**", "$dir/$_") {

---

### Post by Puzzled Guy on 2010-01-18
Thanks! Here is the output I get now:
```
hope@Hope-Laptop:~/Desktop/Perl$ perl renamer.pl
Directory: /home/hope/Desktop/Perl
Old pattern: uni
New pattern: bi
File uniword.pl renamed to biword.pl
hope@Hope-Laptop:~/Desktop/Perl$ perl renamer.pl
Directory: /home/hope/Desktop/Perl
Old pattern: bi
New pattern: uni
File biword.pl renamed to uniword.pl
hope@Hope-Laptop:~/Desktop/Perl$ 
```

Oops! The problem was caused when I typed $oldpat instead of $oldname.
So the error was really my fault.

Note to self: Check for typos before asking for help

---

