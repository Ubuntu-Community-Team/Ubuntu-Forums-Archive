---
title: "perl - array of hashes"
date: 2007-08-23
forum: Programming Talk
---

### Post by jimmymus on 2007-08-23
EDIT : I found a way to do what I'm doing. I can't figure out how to delete this thread.


Holy cow =/ I don't think I understand what's going on when I'm making an array of hashes.

Here is my code

@k = ();
$k_quantity = <STDIN>;

for($i = 0; $i < $k_quantity; $i++)
{
	@k[$i] = {int(rand(500)) => int(rand(500))};
	while ($x, $y) = each(@k[i])
	{
		print "x is ", $x, " and y is ", $y, "\n";
	}
}

I know I need to use the ' -> ' operator at some point but I can't find anything online that makes sense to me. And my perl book is in the mail =/

Thanks!

---

### Post by slavik on 2007-08-24
@k[$i] = {int(rand(500)) => int(rand(500))}; is weird/wrong;

@k[$i] says you want to access and array stored there.

what you are attempting to store is a hash ref;

change that @k to $k;

then @k is an array of hash references.

then, in the each part. you access the elements by $k[$i] but you want to dereference them as hashes, therefore enclose it in %{ } ...

the -> would be used if you wanted to access individual members/values of the hash. ie: $k[$i]->{key}

---

### Post by PaulFr on 2007-08-24
Will the following help ?```
#!/usr/bin/perl
use strict;

my @k = ();               # declare an empty array
my $k_quantity = <STDIN>; # read a numeric from input
if ($k_quantity < 5) { $k_quantity = 5; }
  
# Populate the values
my $i; my $j;
for ($i = 0; $i < $k_quantity; $i++) {
          # Create a hash of 5 entries
          my %h_values;
          for ($j = 0; $j < 5; $j++) {
                  $h_values{$j} = int(rand(500));
          }
          # Push a reference onto the array
          push @k, \%h_values;
}
  
#  @k is an array of references to hashes
  
$i = 1;
foreach my $entry (@k) {
  
          print "Entry index : $i\n";
  
          # Print out the hash contained in this entry
          $j = 1;
          foreach my $key (sort keys %$entry) {
                  print "   $j) Key: $key has value " . $$entry{$key} . "\n";
                  # Can also be written as
                  # print "   $j) Key: $key has value " . $entry->{$key} . "\n";
                  $j++;
          }
          $i++;
}
exit 0;
```

---

### Post by slavik on 2007-08-24
paul, just to be more "Perl hackerish" that code can be twice as short :P

but it is very close to C (verbose and easy to follow) ;)

---

### Post by PaulFr on 2007-08-24
TMTOWTDI, but I find the verbose version always more maintainable :-)

---

### Post by slavik on 2007-08-24
> **PaulFr said:**
> TMTOWTDI, but I find the verbose version always more maintainable :-)

personally, I almost always have 2 versions of my code. first version is verbose and the other is as short as possible :)

priority que (uses default variables) :)
```

sub enqueue {
	push @{ $_{"$_[0]"} }, $_[1];
}

sub dequeue {
	foreach(sort { $a <=> $b } keys %_) { print "p=$_\n"; return shift @{ $_{$_} } if ($#{ $_{$_} } > -1); }
}

```

---

### Post by pmasiar on 2007-08-24
> **slavik said:**
> 
```

sub enqueue {
	push @{ $_{"$_[0]"} }, $_[1];
}

```

Scary. I know this is very idiomatic perl, and with some effort I even can decode what this code is doing, but... scary. 

This is exactly why Perl has reputation of "executable white noise". Imagine someone returning to this code after 2 years programming something else... Total loss. Just say no! :-)

---

### Post by slavik on 2007-08-24
I know, but I intended to do it this way (for fun).

a more readable version:
sub enque {
  my ($priority, $item) = @_; #array assignment :)
  push @{ $data{$priority} }, $item; #array acting like a stack/que :)
}

(intended for people who are interested in how that push line works)
important thing to understand is the @{ $data{$priority} } part, it goes into hash called data. then it goes to the value passed in the $priority variable and dereferences it as an array (since nothing exists there, it creates the array) and puts the item at the end of the array.

also, in Perl, arrays are actually doubly linked circular lists (I forget where I read this).

---

