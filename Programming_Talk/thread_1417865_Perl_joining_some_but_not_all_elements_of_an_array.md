---
title: "Perl: joining some but not all elements of an array"
date: 2010-02-27
forum: Programming Talk
---

### Post by motoperpetuo on 2010-02-27
i understand that the following code will join all the elements of the array @output and place them in the variable $definition, separated by spaces:
```

$definition = join(' ',@output);

```
is there any good way to join all of the elements in @output except for the first (that is, all the elements except $output[0]) ? does perl let you use 'join' to join some elements in an array, but not all? 

note that the number of elements in @output varies. i know how to get the number of elements in the array @output by using something like 
```

$elements = $#output;

```
i just don't know how to use this information to get 'join' to do what i want.

---

### Post by ghostdog74 on 2010-02-27
see ```
perldoc -f splice
```

---

### Post by Some Penguin on 2010-02-27
splice() is destructive, making it not necessarily the best choice.

@foo[offset1..offset2], however, will work:

```

#!/usr/bin/perl -w
use strict;

my @rgc = ('a', 'b', 'c', 'd');
print join(",", @rgc[1..($#rgc)]), "\n";
exit 0;

```

---

