---
title: "resursive sum on an array in PERL"
date: 2012-02-01
forum: Programming Talk
---

### Post by smasher40 on 2012-02-01
Hi, i'm trying to make this recursive way of suming all elements of an array, but my code has an error, can you guys help me out finding what's wrong.

here is my code:


#!/usr/bin/perl -w
use strict;

my $num;
my @nums;
my $soma;

printf ("# THE SCRIP WILL CALCULATE RECURSIVELY THE SUM OF THE ELEMENTS ON AN ARRAY # \n");
print "==========================================================================\n\n";


print "\n INSERT INT NUMBERS,TO FINISH JUST ENTER 0 - ZERO \n";


do
{
	print " Insert a INT number --> ";
	chomp ($num = <STDIN>);
	push (@nums,$num);
	print "\n\n";
}while ($num !=0);


printf ("\n\nThe sum of the elements of the array is  ---> ".&soma(@nums)."\n\n");






sub soma($)
{
	my @elements = @_;
	my $num_elements = 0;
	my ($nums, $soma);
	
	chomp (@elements);
	foreach $nums(@elements)
	{
		$num_elements = $num_elements +1;
	}
	#print "@elements";
	#print "\n\n";
	#print "total de elementos do array --> $num_elements";
	$soma = 0;
	if ($num_elements > 0)
	{
		foreach $nums(@elements)
		{
			print "$nums\n";			
			return soma($soma = $soma + $nums,$num_elements-1);
		}
	}
	else
	{
		return 1;
	}
}


OUTPUT

infinitive number 1

---

### Post by trent.josephsen on 2012-02-01
For starters, always wrap code in ```
 tags.

[CODE]sub soma($)
```

Do you have any idea what the ($) means?

```
foreach $nums(@elements) {
    $num_elements = $num_elements +1;
}
```

Is it possible you meant this:

```
$num_elements = $#elements + 1;
```

As for the rest of your sub, it seems you have failed to divine the meaning or use of recursion.  I'd suggest reading Wikipedia on recursion, and maybe searching for some other resources.  I kind of suspect this isn't homework, because practically nobody teaches Perl as a beginning programming language, but to be on the safe side all I'll say about your real problem is that you really need to think harder about what to do when $num_elements > 0.

---

