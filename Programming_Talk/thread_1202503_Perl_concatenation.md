---
title: "Perl concatenation"
date: 2009-07-02
forum: Programming Talk
---

### Post by vicpascow on 2009-07-02
I have a folder that contains ~1000 .csv files (the folder ONLY has .csv files).

I am looking to write a Perl script to merge all of these files into one "master" file.

So, if one file contained:
a,a,a
b,b,b

and another contained:
c,c,c

the result would be:
a,a,a
b,b,b
c,c,c

I previously had written:

[INDENT]#!/usr/bin/perl -w
use strict;
use warnings;
	
opendir (DIRECTORY, $ARGV[0]); 
open (OUTPUT, ">results.csv"); 

my $file;
my $line;

while (defined($file = readdir(DIRECTORY))) {
	foreach $line($file) { 
		print OUTPUT do { local( @ARGV, $/ ) = $file ; <> }
	}
}
		
close(OUTPUT);
closedir(DIRECTORY);[/INDENT]

But this did not yield the appropriate results.

Any suggestions?

---

### Post by ghostdog74 on 2009-07-02
```

while(<>){print};

```
on command line
```

perl myscript.pl *csv > newfile
OR
perl -ne "print;" *.csv > newfile

```

---

### Post by monkeyking on 2009-07-02
Do you just want to cat the files?
Like

cat fil1.csv fil2.csv ... >> master.csv

Theres a billion was of doing it, I would use a simple bash

```

#!/bin/bash

for i in $(ls dir/*.csv);do
    cat $i >> master.csv
done



```

---

### Post by ghostdog74 on 2009-07-02
> **monkeyking said:**
> 
```

#!/bin/bash

for i in $(ls dir/*.csv);do
    cat $i >> master.csv
done



```
```

cat *csv > master.csv

```

---

### Post by monkeyking on 2009-07-02
cheers ghostdog :)

---

