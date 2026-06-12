---
title: "awk: replace lines from 2 files starting with same pattern"
date: 2010-04-17
forum: Programming Talk
---

### Post by Lampi on 2010-04-17
hello

I have two files with multiple lines, each of them uses the same patterns at the start of line, say:

file1
```
T 1 some text and figures mixed up on one line, starting pattern is 'T 1'
T 2 some other text and figures mixed up on one line, starting pattern is 'T 2'
Y some more text ... starting pattern is Y
```

file2
```
T 1 some DIFFERENT text compared to file1, same starting pattern 'T 1'
T 2 some other DIFFERENT text compared to file1, same starting pattern 'T 2'
Y some more text DIFFERENT to file1, but starting pattern again is letter Y
Z here is some text that does NOT come up in file1 - it needs to stay untouched, starting pattern is Z
```

so, how do I replace the lines in file2 with the lines in file1 according to the starting patterns 'T 1' 'T 2' Y, without touching the line in file2 with starting pattern Z?

thanks in advance!

---

### Post by gmargo on 2010-04-17
What made you put "awk" in the subject line?  Is this a homework problem?  (Could be done in awk; I would use perl.)

---

### Post by Lampi on 2010-04-17
> **gmargo said:**
> What made you put "awk" in the subject line?
I thought it's the best suit for the problem

> **gmargo said:**
> Is this a homework problem?
Nope

---

### Post by piyush.neo on 2010-04-17
Do u have to explicitly change file2 or just produce the output with changed lines??

---

### Post by Cracauer on 2010-04-17
Are the keys unique?

You read file2 into a hashtable indexed by your key and then while traversing file1 you split it into key and value and if the key is in the hashtable you echo the value from the hashtable.

If the keys are not unique then you need to think about what will happen with duplicates.

---

### Post by Lampi on 2010-04-18
> **piyush.neo said:**
> Do u have to explicitly change file2 or just produce the output with changed lines??
I need to explicitly change file2

> **Cracauer said:**
> 
Are the keys unique?
Oops ... it's good you ask this, since there might be one ore more identical keys. In those cases it would be nice to just get all of them into file2, but only if there are already the same keys.

Maybe gmargo is right and awk is not the best choice for this, so: how would this look f.e. in perl?

---

### Post by gmargo on 2010-04-18
Here's a simple perl implementation.  The substituted results are written to standard output.

```

#!/usr/bin/perl -w
# vim: ts=8 sts=4 sw=4 et :
use strict;
use warnings;
use diagnostics;

#--------------------------------------------------------------------------
# http://ubuntuforums.org/showthread.php?t=1456489
#--------------------------------------------------------------------------

#--------------------------------------------------------------------------
# List of patterns to identify lines to match/modify.
my @patterns = (
    qr{^T 1 },
    qr{^T 2 },
    qr{^yabba dabba doo },
    qr{^Y },
);
#--------------------------------------------------------------------------

sub Usage
{
    print STDERR "Usage: $0 file1 file2\n";
    exit 1;
}
Usage() unless @ARGV == 2;
my ($f1, $f2) = @ARGV;
#print "f1=\"$f1\" f2=\"$f2\"\n";

my @pats = ((undef) x @patterns);

open FI, "<", $f1 or die "Cannot open $f1: $!";
while (<FI>)
{
    my $line = $_;      # don't deal with line endings
    foreach my $pi (0 .. $#patterns)
    {
        if (!$pats[$pi] && $line =~ $patterns[$pi])
        {
            $pats[$pi] = $line;
            last;
        }
    }
}
close FI;

#foreach my $pi (0 .. $#patterns)
#{
#    print "pats[$pi]=".(defined $pats[$pi] ? $pats[$pi] : "undef")."\n";
#}

open FI, "<", $f2 or die "Cannot open $f2: $!";
while (<FI>)
{
    my $line = $_;      # don't deal with line endings
    foreach my $pi (0 .. $#patterns)
    {
        if ($pats[$pi] && $line =~ $patterns[$pi])
        {
            $line = $pats[$pi];
            last;
        }
    }
    print $line;    # Results to stdout
}
close FI;

exit 0;


```

---

