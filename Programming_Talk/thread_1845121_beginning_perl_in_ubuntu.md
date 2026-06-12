---
title: "beginning perl in ubuntu"
date: 2011-09-16
forum: Programming Talk
---

### Post by manish411 on 2011-09-16
```


 #!/usr/bin/perl
 $inputline = <STDIN>;
 print ($inputline );


```

while running the simple programming
in file pr1
I am getting the following problem

```


./pr1: line 2: syntax error near unexpected token `;'
./pr1: line 2: ` $inputline = <STDIN>;'


```

---

### Post by nvteighen on 2011-09-16
This works for me:

```

#!/usr/bin/env perl

use strict;
use warnings;

my $input = <STDIN>;
print $input;

```

EDIT: How are you executing your code?

---

### Post by cgroza on 2011-09-16
I don't think you are using the perl interpreter to execute that code.
I typed the same thing in bash, and got the exact same error message.

---

### Post by Arndt on 2011-09-16
> **manish411 said:**
> ```


 #!/usr/bin/perl
 $inputline = <STDIN>;
 print ($inputline );


```

while running the simple programming
in file pr1
I am getting the following problem

```


./pr1: line 2: syntax error near unexpected token `;'
./pr1: line 2: ` $inputline = <STDIN>;'


```

You have blanks at the start of all lines. This doesn't matter for the perl code, but it disables the #! line, so when seeing ./pr1, bash will treat it as a bash script. Remove the blank.

---

