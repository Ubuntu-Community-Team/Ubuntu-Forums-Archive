---
title: "Perl packager--@INC when bundling multifile project"
date: 2011-07-05
forum: Programming Talk
---

### Post by ceclauson on 2011-07-05
Hello.  I'm trying to use the Perl packager (pp) utility to bundle a multifile project into an executable, but when I try to run the resulting executable, it complains about not being able to find dependent files in @INC

Here are my files
mymain.pl:
[PHP]
#!/usr/bin/perl

#file main.pl

use strict;
use warnings;

require 'aux.pl';

my $mssg = get_mssg();

print $mssg;
print "\n";
[/PHP]

aux.pl:
[PHP]

#file aux.pl

use strict;
use warnings;

sub get_mssg() {
    return "Hello, there";
}

1;
[/PHP]

Here's what happens at the command line:
```

cclauson@grendel:~/Desktop/perltest$ pp mymain.pl aux.pl -o mymain
cclauson@grendel:~/Desktop/perltest$ ./mymain
Can't locate aux.pl in @INC (@INC contains: /tmp/par-cclauson/cache-9e568f1d1f2ce9e2aa87d9efcf609800325cad51/inc/lib /tmp/par-cclauson/cache-9e568f1d1f2ce9e2aa87d9efcf609800325cad51/inc CODE(0x2beab98) CODE(0x2beb018)) at script/mymain.pl line 8.

```

Any help would be appreciated.  Thanks in advance.

---

### Post by slavik on 2011-07-07
1. modules are usually named with .pm in the end.
2. learn about "use lib"
3. you module code is terribad (no package declaration?)
4. learn about Module::Pluggable (you might not need it, but useful to know)

---

### Post by ceclauson on 2011-07-08
Thanks for the reply, but still no luck.

new aux.pm:
[PHP]
#file aux.pm                                                                                                                                                                                                

use strict;
use warnings;

package aux;

sub get_mssg() {
    return "Hello, there";
}

1;

[/PHP]

new main.pl:

[PHP]
#!/usr/bin/perl                                                                                                                                                                                             

#file mymain.pl                                                                                                                                                                                             

use strict;
use warnings;

use lib '.';

require 'aux.pm';

my $mssg = aux::get_mssg();

print $mssg;
print "\n";

[/PHP]

result:
```


% pp aux.pm mymain.pl -o mymain
% ./mymain
Can't locate aux.pl in @INC (@INC contains: CODE(0x167cae0) /tmp/par-cclauson/cache-215f58808ba7a9121e5f8dce734e5213cbfee5ab/inc/lib /tmp/par-cclauson/cache-215f58808ba7a9121e5f8dce734e5213cbfee5ab/inc CODE(0x1496ba8) CODE(0x1497028)) at script/mymain.pl line 10. 

```

---

### Post by ceclauson on 2011-07-22
I figured it out.  The correct command is:

```

% pp -M aux mymain.pl -o mymain

```

---

