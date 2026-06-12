---
title: "&quot;hidden variables&quot; in perl"
date: 2009-04-16
forum: Programming Talk
---

### Post by monkeyking on 2009-04-16
I got some small perl questions, on the strangness of hidden variables in perl.

First of all when I define/initialize variables in the beginning of my script.
[PHP]
use strict;
my (@nams, $len1, $len1);
[/PHP]
Does the parenthesis mean anything other than just saving alot some typing like
[PHP]
use strict;
my @nams;
my $len1;
my $len2;
[/PHP]

Next is something that is really puzzling me,
whiling through a file like

[PHP]
while (<HANDLE>) {
    chomp;
    if (/^(cr.+)\:(\d+)\-(\d+)$/) {
	$cr = $1;
	$start = $2;
	$end = $3;
	foreach my $ids($begin .. $end) {
	    print $ids
	}
    }
}
[/PHP]
I dont understand and see where the actual line being tokenized is? I have seen things like $_ but not here.
And hvad about "(/^(cr.+)\:(\d+)\-(\d+)$/)"
Sorry for the strangeness in the line above, but it looks like my code is being interpreted as a smiley.
Thanks in advance

---

### Post by johnl on 2009-04-16
It's voodoo perl magic.

Ok, not really.  I'm not super-knowledgeable about perl but I think I can help you here.

The result of each line (if you don't specifically assign it to a variable) is stored in $_.  And if you don't pass an argument to certain statements, their default is to operate on $_.  

So for example:

```

while (<HANDLE>) {
    # $_ here is one line from the file <HANDLE> 
    chomp; # same as $_ = chomp($_)
    if (/^(cr.+):(d+)-(d+)$/) { # does $_ match this regex?
    $cr = $1;     # store first capture in $cr
    $start = $2;  # store second capture in $start
    $end = $3;    # store third capture in $end
    foreach my $ids($begin .. $end) {  
        print $ids
    }
    }
}  

```

---

### Post by odyniec on 2009-04-16
> **monkeyking said:**
> First of all when I define/initialize variables in the beginning of my script.
[PHP]
use strict;
my (@nams, $len1, $len1);
[/PHP]
Does the parenthesis mean anything other than just saving alot some typing like
[PHP]
use strict;
my @nams;
my $len1;
my $len2;
[/PHP]
Apart from saving a few keystrokes, the parentheses also cause the three variables to be treated as a list. This is commonly used in subroutines to assign arguments to private variables:
```
sub somesub {
  my ($arg1, $arg2, $arg3) = @_;
```

@_ represents the array of arguments passed to the subroutine.

> I dont understand and see where the actual line being tokenized is? I have seen things like $_ but not here.

If no variable is specified, then it's $_. Most text operations (like input/output and pattern matching) affect $_ by default. So "<HANDLE>" is equivalent to "$_ = <HANDLE>", "if (/somepattern/)" is equivalent to "if ($_ =~ /somepattern/)", and so on.

> And hvad about "(/^(cr.+)\:(\d+)\-(\d+)$/)"

It's a regular expression that the current input line ($_) is matched against. It corresponds to a sequence of characters starting with "cr", followed by a colon, then a sequence of digits (at least one), then a hyphen, and a second sequence of digits.

---

### Post by monkeyking on 2009-04-16
Thanks johnl the invisible vars,
makes more sense now.

I still however would like some elaboration.
odyniec you talk about lists, is this the same as an array?
So the following would be valid and good perl programming
[PHP]
my($var1,$var2) = @_;
#and
@var3 = ($var1,$var2);
[/PHP]

I would like some elaboration on 
```
"(/^(cr.+)\:(\d+)\-(\d+)$/)" 
```

The "(/ /)" around simply indicates that we got regexp inside?
The "^" means the  beginning of the line?
The "\:" or "\-" means delimted by or split?
The "(cr.+)" what does the punctuation mean?
The "(\d+)" what does sequenze mean? would "1324 1234" still match?
The "$" end of line right?

Thanks for your replys

---

### Post by odyniec on 2009-04-16
> **monkeyking said:**
> odyniec you talk about lists, is this the same as an array?

Not exactly -- see [http://www.perlfoundation.org/perl5/index.cgi?array_vs_list](http://www.perlfoundation.org/perl5/index.cgi?array_vs_list).

> The "(/ /)" around simply indicates that we got regexp inside?

The slashes indicate it's a regexp. The parentheses are required by the if statement.

> The "^" means the  beginning of the line?

Yes.

> The "\:" or "\-" means delimted by or split?

It means that the particular character must be present in the input ($_) to match the regexp.

> The "(cr.+)" what does the punctuation mean?

"." - any character, "+" - occuring at least once. In other words, anything starting with "cr" will match, e.g: "cry", "crfoobar", "crisis of the economy", etc.

> The "(\d+)" what does sequenze mean? would "1324 1234" still match?

"\d+" - at least one digit but no other character, so a space won't match.

> The "$" end of line right?

Right.

See the perlre manual page for more information on Perl regexp syntax.

---

### Post by monkeyking on 2009-04-16
cheers

thank you.

You have been most helpfull

---

