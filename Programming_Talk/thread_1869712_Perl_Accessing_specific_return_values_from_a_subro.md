---
title: "Perl: Accessing specific return values from a subroutine?"
date: 2011-10-26
forum: Programming Talk
---

### Post by Amblikai on 2011-10-26
Hi folks, i ave a question which my weak google-fu won't allow me to answer. Could you help?

I'm calling a subroutine in perl and it returns mutliple values. However, i only want to access 1 of those values. 

What's the best way to go about this? I understand that the return values are an array, but how do you access the index of the array returned by the subroutine without explicitly renaming the array?

Some example Code for clarity:
```

my $var=foo($arg1, $arg2);
sub foo {
  my ($arg1, $arg2)=@_;  
  return($arg1, $arg2);
}

```
Where i want $var in the above code to equal $arg2.
In other words, how do i access the index of the return array from a subroutine?

Thanks in Advance.

---

### Post by karlson on 2011-10-26
> **Amblikai said:**
> Hi folks, i ave a question which my weak google-fu won't allow me to answer. Could you help?

I'm calling a subroutine in perl and it returns mutliple values. However, i only want to access 1 of those values. 

What's the best way to go about this? I understand that the return values are an array, but how do you access the index of the array returned by the subroutine without explicitly renaming the array?

Some example Code for clarity:
```

my $var=foo($arg1, $arg2);
sub foo {
  my ($arg1, $arg2)=@_;  
  return($arg1, $arg2);
}

```
Where i want $var in the above code to equal $arg2.
In other words, how do i access the index of the return array from a subroutine?

Thanks in Advance.

Change the code to:
```

my @arr = foo($arg1, $arg2);

```

Since you are returning an array...

---

### Post by Amblikai on 2011-10-26
Hi, thanks for your reply. I understand that an array is being returned, my question is how to directly access a specific value of that array. (I don't want the whole array).

In other words, is there an easier way to do this:
```

my @var=foo($arg1, $arg2);
my $str=$var[$#var];

sub foo {
  my ($arg1, $arg2)=@_;  
  return($arg1, $arg2);
}
```

$str now equals $arg2. But i wondered if it was possible to access the index of the returned value array directly without having to assign it to an intermediate array.

Does that make sense?
Should i continue to use the above method?
Thanks.

---

### Post by Lars Noodén on 2011-10-26
Do you mean something like this?

```

my (undef, $str)=foo($arg1, $arg2);

sub foo {
  my ($arg1, $arg2)=@_;  
  return($arg1, $arg2);
}
```

You can use undef for placeholders.

---

### Post by karlson on 2011-10-26
> **Amblikai said:**
> Hi, thanks for your reply. I understand that an array is being returned, my question is how to directly access a specific value of that array. (I don't want the whole array).

In other words, is there an easier way to do this:
```

my @var=foo($arg1, $arg2);
my $str=$var[$#var];

sub foo {
  my ($arg1, $arg2)=@_;  
  return($arg1, $arg2);
}
```

$str now equals $arg2. But i wondered if it was possible to access the index of the returned value array directly without having to assign it to an intermediate array.

Does that make sense?
Should i continue to use the above method?
Thanks.

You can probably do something like this:
```

my $var = foo($arg1, $arg2)[-1];

```

or use Lars' solution.

In addition to that if you only want 1 item why return 2?

---

### Post by gmargo on 2011-10-26
All you need to do is wrap the call to foo() in parentheses and index normally.

Here's a little test program:
```

#!/usr/bin/perl -w
use strict;
use warnings;
use diagnostics;

sub foo { return @_ }

# return array into array, yields whole array
my @v_array = foo("one", "two", "three");
print "v_array=@v_array\n";

# return array, index normally to yield scalars
my $v_0 = (foo("one", "two", "three"))[0];
my $v_1 = (foo("one", "two", "three"))[1];
my $v_2 = (foo("one", "two", "three"))[2];
my $v_L = (foo("one", "two", "three"))[-1];
print "v_0=$v_0\n";
print "v_1=$v_1\n";
print "v_2=$v_2\n";
print "v_L=$v_L\n";

# return array, index as array slice
my @v_S = (foo("one", "two", "three"))[0,2];
print "v_S=@v_S\n";

```Results:
```

v_array=one two three
v_0=one
v_1=two
v_2=three
v_L=three
v_S=one three

```

---

### Post by Amblikai on 2011-10-26
Ah excellent gmargo! That's exactly what i was looking for, i knew there must be a way.

Many thanks!

---

