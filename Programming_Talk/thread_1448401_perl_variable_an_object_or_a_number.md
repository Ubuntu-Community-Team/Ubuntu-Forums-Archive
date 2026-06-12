---
title: "perl: variable an object or a number"
date: 2010-04-06
forum: Programming Talk
---

### Post by Xender1 on 2010-04-06
So I have a method and the second argument will either be an object or a number. I am having  a hard time running an if statement that checks this. Here is my code so far in the method:
```

	my $obj = shift;
	my $something = shift; #number or obj thing
	#print "LALALALAAL   >>> $something <<<<    LALALA \n";
	if ($something =~ /^-?\d/) { #a number
		return ($obj->{len} > $something);
	}
	else {
		return ($obj->{len} > $something->{len});
	}

```
When i run a test with it being a number, it works correctly, then when i pass the object to it, i get this
```

....Operation """": no method found, argument in overloaded package at /hello.pm line 71.

```

my method is overloading the greater than but i do not see why it does not work.

---

### Post by tgalati4 on 2010-04-06
Try removing the comment:  #a number 

then rerun your tests.

---

### Post by Xender1 on 2010-04-06
i removed the comment at the end of each if but still not luck. line 71 is that if statement too

---

### Post by tgalati4 on 2010-04-06
I know that <<< is a reserved delimiter in PHP; don't know about perl.  Try removing >>> and <<<< from your previous statement.

---

### Post by Xender1 on 2010-04-06
Still no luck, this is what i have at the top to have it know to use the overloaded operator. 
```

use overload
	'+' => 'add',
	'-' => 'sub',
	'>' => 'gtn',
	'<' => 'ltn'
;

```
and here is the full method, still with removing the <<<< and >>>> i get that error, but its ony when i do the if statement when $something is an object that the error occurs.
```

sub gtn {   
	my $obj = shift;
	my $something = shift; #number or obj thing
	if ($something =~ /^-?\d/) { 
		return ($obj->{len} > $something);
	}
	else {
		return ($obj->{len} > $something->{len});
	}
}

```

---

### Post by tgalati4 on 2010-04-06
I don't have my perl ebooks on this machine, but there are some decent docs in the repositories:

sudo apt-get install perl-doc
perldoc perlop  (I'm thinking it's an operator preference issue.)
man perl  (to see an overview of the subjects)

What version of perl?

perl -v

Update:  I just pasted your code into gedit with perl highlighting.  Sometimes tightening up the code helps to find the problem.

sub gtn {
    my $obj = shift;
    my $something = shift;
    if ($something =~ /^-?\d/) {return ($obj->{len} > $something)};
    else {return ($obj->{len} > $something->{len})};
}

---

### Post by Xender1 on 2010-04-06
im using perl 5.10.0 and have the use 5.010000; in my module. Another thing i tried to do was check if it was an object as opposed to checking if it was a number
```

sub gtn {    #compare object to number or to other object (both same type of obj)
	my $obj = shift;
	my $something = shift; #number or obj thing
	if ($something->{len} == '') {return ($obj->{len} > $something->{len});}
	else {return ($obj->{len} > $something);}
}

```
So there you can see my if statement is checking to see if there is something in the len but i am getting "Can't use string ("6") as a HASH ref while "strict refs" in use"

---

### Post by Some Penguin on 2010-04-06
Well, if $something is a scalar instead of a reference, treating it as a hash reference isn't going to work.

---

### Post by gmargo on 2010-04-06
> **Xender1 said:**
> So I have a method and the second argument will either be an object or a number. I am having  a hard time running an if statement that checks this. 

Use **ref()** to differentiate types; see the **perlfunc(1)** man page for the documentation.
Here's an example of **ref()**:
```

#!/usr/bin/perl -w
use strict;
use warnings;

# Example of "ref()"

use LWP::UserAgent;

my (@bb, %cc);
my $a_scalar = 0x5a5a;
my $b_array  = \@bb;
my $c_hash   = \%cc;
my $d_obj    = LWP::UserAgent->new();
my $e_code   = sub { print "Howdy" };

print "ref(scalar) = \"".ref($a_scalar)."\"\n";
print "ref(array)  = \"".ref($b_array)."\"\n";
print "ref(hash)   = \"".ref($c_hash)."\"\n";
print "ref(obj)    = \"".ref($d_obj)."\"\n";
print "ref(code)   = \"".ref($e_code)."\"\n";

__END__

ref(scalar) = ""
ref(array)  = "ARRAY"
ref(hash)   = "HASH"
ref(obj)    = "LWP::UserAgent"
ref(code)   = "CODE"


```

---

### Post by tgalati4 on 2010-04-06
From man perlfunc:

       Remember the following important rule: There is no rule that relates
       the behavior of an expression in list context to its behavior in scalar
       context, or vice versa.  It might do two totally different things.
       Each operator and function decides which sort of value it would be most
       appropriate to return in scalar context.  Some operators return the
       length of the list that would have been returned in list context.  Some
       operators return the first value in the list.  Some operators return
       the last value in the list.  Some operators return a count of
       successful operations.  In general, they do what you want, unless you
       want consistency.

---

### Post by Xender1 on 2010-04-06
I got my code to this now, and it works except for when its an object it returns '' as opposed to 1 or 0.... but im getting close to the answer thanks so much for the ref idea works very well. (also tried changing cmp to eq still no luck);

SOLVED!!! 
just got rid of the second if statement and it worked.. strange yes, but im not complaining. here is the code that works now.
```

sub gtn {
	my $obj = shift;
	my $something = shift; #number or obj thing
	my $ref = \$something;
	if (ref($ref) eq "SCALAR") {
		return ($obj->{len} > $$ref);
	}
	return ($obj->{len} > $$ref->{len});
}

```

---

