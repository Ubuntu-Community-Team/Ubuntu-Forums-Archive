---
title: "Missing PATH environmental variable"
date: 2009-08-18
forum: Programming Talk
---

### Post by BalleClorin on 2009-08-18
I'm trying to execute a perl script through a bash script.
The construct is basicly:

for every file of type $1 in current directory
script.pl filename

The bash script and the perl script both work separately, but the perl script seems to be unable to locate the environmental PATH variable when called from within the bash script.

Of course I could edit the perlscript and use absolute paths to the external tools, but  that wouldn'tbe very elegant would it...

---

### Post by slakkie on 2009-08-18
You could do this:

in the bash script: export PATH=your_path

or in the perl script: $ENV{'PATH'}=your_path;

y.sh
```

#!/bin/bash

export PATH=$PATH:/path/to/path
./y.pl

```

y.pl
```

#!/usr/bin/perl

print $ENV{PATH} . "\n";

```

---

### Post by BalleClorin on 2009-08-18
The perl script was already using $ENV{'PATH'}.
But I located the problem, the bash script is a modified example I found somewhere on the web, and it modified the PATH variable. I left the line alone because I didn't understand what it did. I've been meaning to learn bash scripting for a while, but haven't gotten that far yet. Funny how I usually figure out the problems myself right after I post for help.

Thanks anyway.

---

