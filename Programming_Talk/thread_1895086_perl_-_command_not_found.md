---
title: "perl - command not found"
date: 2011-12-14
forum: Programming Talk
---

### Post by adit on 2011-12-14
This is my perl script
```
#!/usr/bin/perl
$x=2;
print $x;
```
I expect the program outputs 2.  But I get the following output.
line 2: =2: command not found

---

### Post by Lars Noodén on 2011-12-14
I'm unable to duplicate your error but you might try adding warnings and restricting unsafe constructs to see if it will generate clues:

```

#!/usr/bin/perl

use strict;
use warnings;

my $x=2;
print $x;

```

---

### Post by karlson on 2011-12-14
> **adit said:**
> This is my perl script
```
#!/usr/bin/perl
$x=2;
print $x;
```
I expect the program outputs 2.  But I get the following output.
line 2: =2: command not found

Do you by chance ran it like this:

```

bash ./script

```

---

