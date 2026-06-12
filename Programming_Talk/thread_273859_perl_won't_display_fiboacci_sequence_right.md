---
title: "perl won't display fiboacci sequence right"
date: 2006-10-08
forum: Programming Talk
---

### Post by baldy1324 on 2006-10-08
hi i am running the following code - ```
#!/usr/bin/perl
$n = 1000;
$first = 0;
$second = 1;
print "$first    $second";

while ($n > 0)
{
        $third = $first + $second;
        $first = $second;
        print "$third    ";
        $n--;
}

```

it runs without any errors but gives
0    11    2    2    2    2    2    2    2    2    2    2    2    2    2    2 
and then keeps repeating but just 2s not a 0 or an 11
can someone please help me:)

---

### Post by amo-ej1 on 2006-10-09
You forgot a line ;-)
```

#!/usr/bin/perl
$n = 1000;
$first = 0;
$second = 1;
print "$first  $second ";

while ($n > 0)
{
        $third = $first + $second;
        $first = $second;
        $second = $third;
        print "$third    ";
        $n--;
}

```

---

### Post by Note360 on 2006-10-09
Or you can use subroutines.

```

#!/usr/bin/env perl -w

# Excuse my shabby perl skills, because it's been a while
# $ulimit is the upper limit
# $llimit is the lower limit
sub fabSequence
{
	$ulimit = <STDIN>;
	$first = 0;
	$second = $first + 1;
	@return_list = ( $first, $second );

	until ( $ulimit < 0 )
	{
		$third = $first + $second;
		$first = $second;
		$second = $third;
		push( @return_list, $third );
		--$ulimit;
	}
	return @return_list
}

foreach $num ( &fabSequence )
{
	print $num, " ";
} 

```

---

