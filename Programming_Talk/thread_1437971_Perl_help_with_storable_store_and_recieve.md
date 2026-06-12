---
title: "Perl help with storable store and recieve"
date: 2010-03-24
forum: Programming Talk
---

### Post by Xender1 on 2010-03-24
In Perl I am trying to save a data structure I have using the Perl module Storable. I read the perldoc and I can't figure out what I am doing wrong. Here is the sub that does the saving, to it is passed a reference to the array.
```

sub Save {
	use Storable;
	my $array_ref = $_[0];
	print "Enter filename to save data too: ";
	chomp (my $filename = <STDIN>);
	store $array_ref, $filename;
}

```
and here is my sub for loading the data, getting passed same parameter of a reference to the array.
```

sub Load {
	use Storable;
	my $array_ref = $_[0];
	print "Enter filename to load data from: ";
	chomp (my $filename = <STDIN>);
	$array_ref = retrieve($filename);
}	

```
A file gets created when I do the save.. not sure how to view it but it creates something. Whenever I do the load I do not get any errors, but when I try and check the array ref nothing is there. Any ideas?

---

### Post by Some Penguin on 2010-03-24
It's the same reason why the following will *not* change the value of $value:

```

my $value = "foo";
my $refToValue = \$value;
my $anotherValue = "bar";

$refToValue = \$anotherValue;

print $value, "\n";

```


Think about what is actually being changed.

---

### Post by Xender1 on 2010-03-24
All that is being changed is where $refToValue is pointing, changing this does not change what memory address $value points to and where it is pointing is still "foo".

if in your code i wanted to change $value i would have to do:
```

my $value = "foo";
my $refToValue = \$value;
my $anotherValue = "bar";

my $refToOther = \$anotherValue;

$value = $$refToOther;

print $value, "\n";

```

So in my code, I am now trying (assuming that what is happening in save is correct)
```

sub Load {
	use Storable;
	my $array_ref = $_[0];
        my @temp = @$array_ref;
	print "Enter filename to load data from: ";
	chomp (my $filename = <STDIN>);
	my $ref = retrieve($filename);
        @temp = @$ref;
}

```
This still isnt working, I feel like it is more complicated because I am passing in just a reference to the array, maybe I should pass in my array? Im not sure.

---

### Post by Some Penguin on 2010-03-25
Still no good.   Creating an array on the stack, populated with the contents of a different array, doesn't mean that you have the same array -- it's two independent arrays.

Either return the (new and different) reference you get from the 'retrieve', or copy the contents of the array referenced there, to the array that's referenced by the argument passed in.

---

