---
title: "Passing variables from PHP to PERL"
date: 2010-07-20
forum: Programming Talk
---

### Post by s.fox on 2010-07-20
Hello,

I am having some trouble passing multiple variables to a perl script from php.

I have the following so far:

PHP Code -

```
<?php
$var1 = "ABC";
$var2 = "123";
exec("perl myScript.pl $var1 $var2", $output);
print_r($output);
?>
```myScript.pl -
```

#!/usr/bin/perl
$var1 = $ARGV[0];
$var2 = $ARG[1];
print "VAR1: ".$var1."\n";
print "VAR2: ".$var2;
```Currently only the first variable seems to be passed across.  Left scratching my head at this one :)  I must call the perl script from php.

Any help would be great, thank you.

-Silver Fox

---

### Post by lisati on 2010-07-20
Does adding a new line to the "print" of var2 make a difference?

---

### Post by Some Penguin on 2010-07-20
ARG != ARGV.  When you have inconsistent code like that, at least one of them is likely to be wrong...


Also, I suggest that your Perl scripts start like

```

#!/path/to/perl -w

use strict;

```

The '-w' option enables various warnings, and 'use strict' will catch some more likely issues.

---

### Post by s.fox on 2010-07-20
> **lisati said:**
> Does adding a new line to the "print" of var2 make a difference?

No,  it did not make a difference.  Thank you for the reply.

I have also just tried editing the exec on the php script to this:

```
exec('perl myScript.pl'.' '.EscapeShellArg("$var1").' '.EscapeShellArg("$var2"),$output);
```Still no joy :(

It must be something simple as var1 is okay.

-Silver Fox

---

### Post by s.fox on 2010-07-20
> **Some Penguin said:**
> 
ARG != ARGV


Typo! Haha. This solved my confusion.  Thank you again,

-Silver Fox

---

### Post by ksyz_1 on 2010-08-31
Hey.. I am working on a similar application which uses exec(). I am trying to connect a unix server using ssh (phpseclib) and running an external program like 'C' program or a fortran program. I am using exec() to run .out. My code looks this way
 
echo $ssh->exec('./a.out');
 
a.out is a executable for program to add two numbers and the inputs are hardcoded within the 'C' program.
 
This piece of code works perfectly when the inputs are hardcoded in the 'C' program. But when I try to pass the arguments to exec(), the php script becomes unresponsive. After modification to accept inputs for .out, my code looks this way,

echo $ssh->exec("./a.out");
echo $ssh->exec("10 20");
 
where a.out is for a simple program to add two numbers and 10 and 20 are inputs. I did modify the code as below and tried few options
 
$ssh->exec("./a.out '10' '20'");
$ssh->exec("./a.out ; '10 20'"); 

but none of them worked. All the above php scripts became unresponsive.
How can I provide inputs to the a.out in a new line using exec()? Could you please provide some inputs on how to provide inputs. Your inputs are greatly appreciated.. 
Thanks in advance..

---

### Post by Hellkeepa on 2010-09-01
HELLo!

You'll either have your script return a status code once it's completed, or make sure you drop all output from it so that PHP isn't waiting for an answer.

Happy codin'!

---

### Post by Some Penguin on 2010-09-01
Bigger problem:  argv != STDIN.

---

