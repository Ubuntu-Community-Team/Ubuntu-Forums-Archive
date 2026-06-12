---
title: "Perl: use variables from main in a module?"
date: 2007-10-25
forum: Programming Talk
---

### Post by Cene on 2007-10-25
Hello,

I've been writing little Perl script (more on that once I get it working. ;)). I meant it to be very basic, and to use modules for advanced functionality. That's fine, except that I must use at least four different variables from the main script to do anything in the module. However, I cannot seem to use the vars from main in the sub in the module. Can it be done? I tried Googling, but found nothing useful.

I get "Use of uninitialized value in concatenation (.) or string at modules/*thenameofthemodule.pm* line *x* <GEN0> line 1." and "Use of uninitialized value in pattern match (m//)....." errors if I try to run it now..

TIA,
Cene

---

### Post by pmasiar on 2007-10-26
What did you tried? You need to export names from a module to make them available outside.

---

### Post by slavik on 2007-10-26
you can make the variables global using the 'our' keyword :)

---

### Post by skeeterbug on 2007-10-26
> **Cene said:**
> Hello,

I've been writing little Perl script (more on that once I get it working. ;)). I meant it to be very basic, and to use modules for advanced functionality. That's fine, except that I must use at least four different variables from the main script to do anything in the module. However, I cannot seem to use the vars from main in the sub in the module. Can it be done? I tried Googling, but found nothing useful.

I get "Use of uninitialized value in concatenation (.) or string at modules/*thenameofthemodule.pm* line *x* <GEN0> line 1." and "Use of uninitialized value in pattern match (m//)....." errors if I try to run it now..

TIA,
Cene


I thought you could go:

MODULE_NAME::Variable

---

### Post by yanaek on 2011-05-05
i have the same problem. i need to use variable from main script (which is not a package), in a module (package).

what you guys wrote here is OK when one wants to do it in reverse (use variable which is defined in module/package, in the main script)

---

### Post by shawnhcorey on 2011-05-05
You can use the full-qualified name to access variables in a different package.  This is not consider to be the best practice.  Having a module rely on variables in main means it is tightly coupled to main and would be harder to re-use.  Instead, consider a way to set the variables in the package through some function.

How to use fully-qualified names:

```
#!/usr/bin/env perl

use strict;
use warnings;

our $var = 'test';

package Foo;

our $var = 'foo';

sub foo {
  print "Foo's var: $var\n";
  print "main's var: $::var\n";
  print "again main's var: $main::var\n";

}

package main;

Foo::foo();
print "main's var: $var\n";
print "Foo's var: $Foo::var\n";

```

---

### Post by yanaek on 2011-05-05
thanks for quick reply!

my program has main script and package, let's call it 'Common.pm'

in main script it reads command line arguments and parameters (with a help of Getopt)

i want to use thos variables in function defined in module

Main.pl
```

use Getopt::Std

getopt('vn'); # key-value switches

our $opt_v; # here we have one of the variables

```

now in Common.pm i have logging function, which changes 'verbosity' level of messages, according to $opt_v value.

function from Common.pm is also used in other modules, so just passing the opt_v as argument will not work (other modules need to acces it too)

is there a 'good' practice' how to do such thing?

---

### Post by yanaek on 2011-05-06
OMG sorry for the mess but it was so easy.

in module/package one has to define the variable as global

```

use vars qw($LOGFILE $LOGLEVEL); #don't know if it is necessary

our $LOGFILE = "./LOGFILE.log";
our $LOGLEVEL = 1;  # LOGLEVEL will be overriden by -v parameter

```

and then here comes the solution, one needs to use

```

$Common::LOGLEVEL = $opt_v;

```

to change global variables from main script (but residing in that module)

---

