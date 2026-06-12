---
title: "help with perl exam revision..."
date: 2010-06-17
forum: Programming Talk
---

### Post by ja660k on 2010-06-17
Hey all, Perl exam tomorrow. 
and theres a question in the sample exam that i dont quite understand.
the code is very perlish

Briefly explain each line
```

package Counter;
sub TIESCALAR { 
    my $class = shift; 
    my $value = shift || 0; 
    bless \$value => $class;
} 
sub FETCH { return ++ ${$_[0]};}
sub STORE { return ${$_[0]} = $_[1];}

```
and my understanding is..
tiescalar takes a package name, and creates an object to $class with the value of $value
and
store and fetch. im confused on :(
any help would be great.

---

### Post by trent.josephsen on 2010-06-17
Here's a rewrite without using names special to tying:

```
package Counter;
sub new {
    my($class,$value) = @_;
    $value ||= 0;
    my $self = \$value;
    return bless $self, $class;
}

sub fetch {
    my($self) = @_;
    return ++$$self;
}

sub store {
    my($self,$new_value) = @_;
    return ($$self = $new_value);
}
```

$_[N] is the Nth element of @_.  Keep in mind that objects are references, and can be references to anything.  Here's how you would use this code:

```
my $counter = new Counter(); # Counter starts at 0 by default
$a = $counter->fetch; # $a = 1
$a = $counter->fetch; # $a = 2
$a = $counter->fetch; # $a = 3

$counter->store(-1); # start over from -1
$a = $counter->fetch; # $a = 0
$a = $counter->fetch; # $a = 1
$a = $counter->fetch; # $a = 2
```

In the original, the names TIESCALAR, FETCH and STORE are interesting if you try to tie the variables.  [http://perldoc.perl.org/perltie.html](http://perldoc.perl.org/perltie.html)

---

### Post by ja660k on 2010-06-17
ahh, right. now it makes sense... thanks, alot

---

