---
title: "How to append time/date to file in perl?"
date: 2009-12-23
forum: Programming Talk
---

### Post by UbuKunubi on 2009-12-23
I have made a file upload cgi script for my website, but I found that when two pictures are uploaded with the same file as a previous one (for example DSC_001, being the format for files from mobile phones) is overwritten by the new one.

I'm thinking the solution to this is to append the time and date to the end of the filename before the suffix - my problem being this is the first time I've had any experience of perl.

Thanks in advance,
Ubu.

---

### Post by ghostdog74 on 2009-12-23
perldoc -f localtime or use Time::localtime

---

### Post by myrtle1908 on 2009-12-23
The "poor mans" way is to use a combination of time and rand eg.

[PHP]my $filename = 'DSC_001-' . time . rand;[/PHP]

A better approach is to use the File::Temp module to create a filename for you eg.

[PHP]use strict;
use warnings;
use File::Temp qw/tempfile/;

my (undef, $filename) = tempfile('DSC_001-XXXX', OPEN => 0);
print $filename;[/PHP]

... which may yield something like: DSC_001-7jbH

---

### Post by UbuKunubi on 2009-12-27
> **myrtle1908 said:**
> The "poor mans" way is to use a combination of time and rand eg.

[PHP]my $filename = 'DSC_001-' . time . rand;[/PHP]

A better approach is to use the File::Temp module to create a filename for you eg.

[PHP]use strict;
use warnings;
use File::Temp qw/tempfile/;

my (undef, $filename) = tempfile('DSC_001-XXXX', OPEN => 0);
print $filename;[/PHP]

... which may yield something like: DSC_001-7jbH

Many thanks for the reply, which seems to have my problem solved, I've just one further question before I can mark this thread as solved:

Have I interpreted your solution correctly if I change the line in the .cgi file from:
```
 open( UPLOAD, ">$upload_dir/$filename" ) or die "$!";
```
to
```
 open ( UPLOAD, ">$upload_dir/ time . rand . $filename" ) or die "$!";
```

to produce a filename similar to 7jbHDSC_001.jpg, rather than plain DSC_001.jpg?

Many thanks for your help,
Ubu

---

