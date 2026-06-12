---
title: "Problem Finding Modules (Perl)"
date: 2009-07-20
forum: Programming Talk
---

### Post by dellwood on 2009-07-20
Hi, 

I am having trouble using *use lib* to call a directory thats inside the scripts directory ( <scriptdir>/modules ). The beginning of the file looks like this:

```

package Engine;

use warnings;
use strict;
use Exporter;
use Config::Simple;
use lib qw( ./modules );

...
if( $lplatform eq 'oest11' ) {
             require "oeslib.pm"

                       }
elsif( $lplatform eq 'sles9t11' ) {
             require "linuxlib.pm";
                       }
             
...


```

and the module looks like this:

```


package linuxlib;

use strict;
use warnings;
use Exporter;

our @ISA = qw( Exporter );
our @EXPORT    = qw( adduser deluser %configlib );
our @EXPORT_OK = qw( adduser deluser %configlib );

#Hash 

our %configlib = (
                adduser => \&adduser,
                deluser => \&deluser
);


```

But when I call $conifglib in Engine.pm, it doesn't know it exists?

Any thoughts?

Thanks :).

-Josh

---

### Post by unutbu on 2009-07-20
I think
```

use lib qw( ./modules );
```

only tells Perl where to look for (extra) modules.
You still need to put something like
```

use linuxlib;
```

in Engine.pm in order to access $configlib inside Engine.pm.

---

