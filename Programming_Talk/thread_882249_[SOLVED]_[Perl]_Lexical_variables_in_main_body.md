---
title: "[SOLVED] [Perl] Lexical variables in main body?"
date: 2008-08-06
forum: Programming Talk
---

### Post by ConMan318 on 2008-08-06
How can variables in the main body of a Perl script be made private?  In the book I have on Perl, it says that variables declared with 'my' are private to the block they are declared in, which makes sense.  Problem is, in the main body of the program there is no block, so apparently all my variables there can be accessed by all functions even if I don't pass them in the arguments to the function.  I don't want to give all my functions access to all my variables in main.  These functions that shouldn't even recognize the variable can even change its contents!  And with 'strict' and 'warnings' enabled!

```

#!/usr/bin/perl
use strict;
use warnings;

my $var = 42;
&nothing;
print "$var\n";
exit;

sub nothing {
    print "$var\n";
    $var += 3;
}

```

```

$ ./test
42
45

```

How can this be remedied?




EDIT: Well I realized that it can be fixed by putting curly braces around the main body.  Is this the correct way to do it?  For all I know this could have other detrimental affects on the program that I don't realize right now.



RE-EDIT: Alright, upon further investigation I have found that this is the right way to do that. :p

---

