---
title: "[SOLVED] Perl wantarray"
date: 2008-11-13
forum: Programming Talk
---

### Post by cybo on 2008-11-13
does anyone know what does wantarray function in perl does? i looked it up in [**_here_**]("http://perldoc.perl.org/functions/wantarray.html"). 

below is its contents:



Returns true if the context of the currently executing subroutine or eval is looking for a list value. Returns false if the context is looking for a scalar. Returns the undefined value if the context is looking for no value (void context).

    return unless defined wantarray;	# don't bother doing more
    my @a = complex_calculation();
    return wantarray ? @a : "@a";

wantarray()'s result is unspecified in the top level of a file, in a BEGIN , UNITCHECK , CHECK , INIT or END block, or in a DESTROY method.

This function should have been named wantlist() instead.



i can't understand what it is trying to say. what is meant by context, void context and non-void context? 

i tried the following code but i always get the same result - error

```

#!/usr/bin/perl
use warnings;
use strict;
&my_sub();
&my_sub("something");
&my_sub("something", "something");

sub my_sub {
  if (defined wantarray) {
    print "wantarray\n";
  } else {
    print "error\n";
  }
}

```

Also does anyone know any dedicated perl forums for newbies and perl gurus wanna be?

thanx

---

### Post by unutbu on 2008-11-13
wantarray is a magic token that is defined within each function. It is true when the function was called in an array context, and it is false when the function is called in a scalar context.

Here is an example:
[PHP]#!/usr/bin/perl
use strict;
use warnings;
my $result;
my @result;

$result=&my_sub("something", "something");
print "my_sub returns scalar:\n$result\n";

print "-"x80,"\n";
@result=&my_sub("something", "something");
print "my_sub returns array:\n";
foreach $result (@result) {
    print "$result\n"
}

sub my_sub {
    my @data=@_;
    if (wantarray) {
	return @data;
    } else {
	my $data=join('+',@data);
	return $data;
    }
}
[/PHP]
Result:
```
my_sub returns scalar:
something+something
--------------------------------------------------------------------------------
my_sub returns array:
something
something

```

Here is a dedicated perl forum: [http://perlmonks.org/](http://perlmonks.org/)
If you google "perl forum" you will find many others too.

---

### Post by scoon on 2008-11-13
Hey there, 

Check out the side bar of the url you posted.  You'll find these: 

[HTML]<h2>Links:</h2> 
      <ul> 
        <li><a href="http://search.cpan.org">CPAN</a></li> 
        <li><a href="http://www.perl.org">Perl.org</a></li> 
        <li><a href="http://www.perl.com">Perl.com</a></li> 
        <li><a href="http://perlbuzz.com">Perl Buzz</a></li> 
        <li><a href="http://www.perlfoundation.org/perl5/index.cgi">Perl 5 Wiki</a></li> 
        <li><a href="http://jobs.perl.org">Perl Jobs</a></li> 
        <li><a href="http://www.pm.org">Perl Mongers</a></li> 
        <li><a href="http://www.perlmonks.org">Perl Monks</a></li> 
        <li><a href="http://planet.perl.org">Planet Perl</a></li> 
        <li><a href="http://use.perl.org">Use Perl</a></li> 
      </ul>[/HTML]

For what it is worth, I always learn something new whenever I visit Perl Monks.

Thanks.

---

