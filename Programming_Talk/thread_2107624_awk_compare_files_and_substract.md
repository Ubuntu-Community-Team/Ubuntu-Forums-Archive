---
title: "awk compare files and substract"
date: 2013-01-22
forum: Programming Talk
---

### Post by djmental on 2013-01-22
Hi guys,

I want to compare file1 and file2 using awk. And then using the output to file3.

file1
4
3
2

file2
5
10
1

So the output in file3 would be 
1
7
1

Any idea on how to do this? I'm a newbie:oops:

Thx in advance

---

### Post by Lars Noodén on 2013-01-22
You'd have to run it through something else first to turn it into multiple columns.  If there are only two files, then [diff](http://manpages.ubuntu.com/manpages/precise/en/man1/diff.1posix.html) is enough.

```

diff -y x1 x2 | awk -F '[| \t]+' '{ A = $1 - $2; if ( A<0 ) A = -A; print A }'

```

The File Separator (FS) can contain a regular expression, like the one above given by -F.

---

### Post by djmental on 2013-01-23
Sorry I forgot to mention I'm using HP-UX. HP-UX doesn't seem to accept the -y parameter.

Any further options?

---

### Post by Lars Noodén on 2013-01-23
Ok.  The non-standard diff came back to bite us.  My awk is weak so I'm not sure of another way without escalating to perl.

```

#!/usr/bin/perl

use strict;
use warnings;
use integer;

my $file1 = "./file1";
my $file2 = "./file2";

open( FILE1, "$file1" ) or die ("Could not open '$file1' : $! \n");
open( FILE2, "$file2" ) or die ("Could not open '$file2' : $! \n");

while ( my $line1 = <FILE1> ) {
    my $line2 = <FILE2> || last;

    chomp( $line1 ); chomp( $line2 );

    my $diff = abs($line1 - $line2);

    print qq($diff\n);

}

close( FILE2 );
close( FILE1 );

```

I wish they wouldn't make non-standard extensions to core utilities.  That cuts down on portability.

---

### Post by steeldriver on 2013-01-23
Here's a handy native bash 'read-from-multiple-files' that I just stole from member Vaphell :)

```
$$ while read -u3 a; read -u4 b; do echo $(($a-$b)); done 3< file1 4< file2
-1
-7
1

```For clarity, I've omitted the absolute function

---

### Post by Lars Noodén on 2013-01-23
You both always have awesome answers.

---

### Post by djmental on 2013-01-23
Thx guys!

Gonna try this out tomorrow!

---

