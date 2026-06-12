---
title: "Perl Looping Problem"
date: 2009-07-15
forum: Programming Talk
---

### Post by dellwood on 2009-07-15
Hi, 

I have created a config file reader called "Engine.pm" -- which dictates the basic sytax of a config file (Shown Below):

```

package Engine;

use warnings;
use strict;
use Exporter;

our @ISA = qw( Exporter );
our @EXPORT =    qw( engine %User_Preferences %commands );
our @EXPORT_OK = qw( engine %User_Preferences %commands );

our %User_Preferences;
our %commands;

sub engine {

        #Read Config File
        print "Opening the config file...";
        open CONFIG, "config.txt" or die $!;
        print "done\n";

        print "Reading the config file...";
        while (<CONFIG>) {
        chomp;                  # no newline
        s/#.*//;                # no comments
        s/^\s+//;               # no leading white
        s/\s+$//;               # no trailing white
        next unless length;     # anything left?
        my ($var, $value) = split(/\s*=\s*/, $_, 2);
        $User_Preferences{$var} = $value;
        }
        print "done\n";

         {
                my( $command, $number ) = split( /:/, $User_Preferences{"COMMAND"} );
                if( $command eq "ADDUSER") {
                        #store info in command hash
                        $commands{$command} = $number;

                }

        }

print "Closing the config file...";
close CONFIG or die "Error closing config: $!\n";
print "done\n";
1;

```

And Here is the config file (config.txt -- it's only got the .txt because it may be run on multiple [win] platforms):

```
##########################
##Test Suite Config File##
##########################

# ldap values

HOST            = #host
PORT            = #port
BINDUSER        = #binduser
BINDPASS        = #binpass
VERSION         = #version
TREE            = #tree
BINDUSERDOTTED  = #binduserdotted

COMMAND         = ADDUSER:1000
                                                                                                                         
```

The problem is

```
if( exists $User_Preferences{"COMMAND"} )
```

Which is a one time deal, but as you can see, the engine currently holds two options, ADDUSER and DELUSER (and many more will be added later).  My minds about used up for the day after reading through the regular expressions sections in three different perl book ](*,) :shock: , so I'm having a hard time coming up with a way for it do repeat the process for all intances of 'COMMAND' it sees.

All help on this is appreciated :).

-Josh

---

### Post by slavik on 2009-07-16
are you writing this for any specific reason? (look for Config::Simple)

---

### Post by soltanis on 2009-07-16
Any Config package is portable and should do exactly what you're trying to accomplish for you.

---

