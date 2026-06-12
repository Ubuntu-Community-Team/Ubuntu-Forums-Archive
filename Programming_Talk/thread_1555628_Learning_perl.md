---
title: "Learning perl"
date: 2010-08-18
forum: Programming Talk
---

### Post by subho1990 on 2010-08-18
I am learning perl. I have been having some problems with this code


$VAR1={
'apple'=>146.50,
'pineapple'=>23.67
};
print $VAR1{'apple'};


but it not work!

how i work this?

---

### Post by Xyro on 2010-08-18
Try this:

```

#!/usr/bin/perl
use strict;
use warnings;

my %var1;

%var1 = (
          "apple" => 146.50,
          "pineapple" => 23.67
        );
 
print $var1{"apple"};

```

---

### Post by subho1990 on 2010-08-18
what was wrong with my code? is the {} the problem?

---

### Post by gmargo on 2010-08-18
In your code, $VAR1 is a reference to a hash, but you are using it as though it was a hash.  So you need one more level of indirection, like this:
```

print $$VAR1{'apple'};

```

If you are a perl beginner, you would be very wise to follow Xyro's example, and begin every perl program with the preamble:
```

#!/usr/bin/perl
use strict;
use warnings;

```

---

