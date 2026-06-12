---
title: "getting Bash exit code in Perl"
date: 2009-04-22
forum: Programming Talk
---

### Post by PGScooter on 2009-04-22
I am unable to get the exit code from a bash command I ran from perl. Here, the folder "nonexistant" does not exist. The exit code is 2, but the variable 'error' has a value of 512. Thanks!


```

use strict;
use warnings;

my $var=`ls nonexistant`;
my $error=`echo "$?"`;
print "\nERROR IS: $error\n";

```

---

### Post by unutbu on 2009-04-22
[PHP]my $retval=system('ls nonexistant')>>8;
print "\nERROR IS: $retval\n";
# ERROR IS: 2
my $retval=system('ls')>>8;
print "\nERROR IS: $retval\n";
# ERROR IS: 0[/PHP]

---

### Post by ghostdog74 on 2009-04-22
from perldoc -f system
> 
 The return value is the exit status of the program as returned by the "wait" call.  To get the actual exit value, shift
               right by eight (see below). See also "exec".  This is not what you want to use to capture the output from a command, for
               that you should use merely backticks or "qx//", as described in "‘STRING‘" in perlop.  Return value of &#8722;1 indicates a
               failure to start the program or an error of the wait(2) system call (inspect $! for the reason).



check the perldoc -f system for more info. 

Otherwise, I would advise you not to apply system call at all for your case.
If you want to "ls" a directory, either use opendir() and readdir()
( see perldoc -f opendir or perldoc -f readdir or perldoc perlopentut).

Or:

```

while(<*>){
  print $_;
}

```

always read your docs!

---

### Post by Arndt on 2009-04-23
> **unutbu said:**
> [PHP]my $retval=system('ls nonexistant')>>8;
print "\nERROR IS: $retval\n";
# ERROR IS: 2
my $retval=system('ls')>>8;
print "\nERROR IS: $retval\n";
# ERROR IS: 0[/PHP]

There is some information on how to decode an exit status in the man page for 'wait' (system call), expressed through some C macros. There may be better information somewhere, but otherwise one has to look at the definition of those macros, and ends up in /usr/include/bits/waitstatus.h; for example:

```
/* If WIFEXITED(STATUS), the low-order 8 bits of the status.  */
#define	__WEXITSTATUS(status)	(((status) & 0xff00) >> 8)

/* If WIFSIGNALED(STATUS), the terminating signal.  */
#define	__WTERMSIG(status)	((status) & 0x7f)
```

---

### Post by ghostdog74 on 2009-04-23
its already documented:  perldoc -f system. 
> 
  You can check all the failure possibilities by inspecting $? like this:

                   if ($? == &#8208;1) {
                       print "failed to execute: $!\n";
                   }
                   elsif ($? & 127) {
                       printf "child died with signal %d, %s coredump\n",
                           ($? & 127),  ($? & 128) ? ’with’ : ’without’;
                   }
                   else {
                       printf "child exited with value %d\n", $? >> 8;
                   }



---

### Post by PGScooter on 2009-04-23
thank you for your replies and explanations. I will do some reading :)

---

