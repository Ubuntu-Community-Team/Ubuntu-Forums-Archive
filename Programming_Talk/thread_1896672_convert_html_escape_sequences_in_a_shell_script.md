---
title: "convert html escape sequences in a shell script"
date: 2011-12-17
forum: Programming Talk
---

### Post by Mahkoe on 2011-12-17
I'm new to shell scripting, and I couldn't find this in any of the tutorials I've read so far. (Or on google for that matter)

I'm using a shell script to download the alt texts from xkcd. It works fine, but I can't for the life of me figure out how to convert the html escape codes(ex. $#39) to text. 

Here is my code:
```
#!/bin/bash

for i in `seq 1 10`
do
	wget http://xkcd.com/$i/
	echo $i >> alts.txt
	grep http://imgs.xkcd.com/comics/ index.html | head -1 | cut -d\" -f4 >> alts.txt
	rm index.html
done
```

---

### Post by Lars Noodén on 2011-12-17
There was a module in [libhtml-parser-perl](http://packages.ubuntu.com/oneiric/libhtml-parser-perl) called [HTML::Entities](http://search.cpan.org/~gaas/HTML-Parser-3.69/lib/HTML/Entities.pm) that will automatically convert to or from the HTML entities.   

It seems to be 8-bit, though.  :(

```

#!/usr/bin/perl                                                                 

use HTML::Entities;
use warnings;
use strict;

my $filename = shift || '-';

open (FILE, $filename )
    or die ("Could not open '$filename': $!\n");

while ( my $line = <FILE> ) {
    print decode_entities($line);
}

close( FILE );

exit (0);

```

---

### Post by ofnuts on 2011-12-17
> **Lars Noodén said:**
> There was a module in [libhtml-parser-perl]("http://packages.ubuntu.com/oneiric/libhtml-parser-perl") called [HTML::Entities]("http://search.cpan.org/%7Egaas/HTML-Parser-3.69/lib/HTML/Entities.pm") that will automatically convert to or from the HTML entities.   

It seems to be 8-bit, though.  :(Should be more than enough for the XKCD hidden supplements :)

Otherwise a shot of SED using commands built from an ASCII table should do the job.

---

