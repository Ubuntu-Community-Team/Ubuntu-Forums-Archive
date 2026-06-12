---
title: "PHP Memory Problem"
date: 2007-09-11
forum: Programming Talk
---

### Post by 71fnRVVm on 2007-09-11
Hey everyone,

I'm having a problem with a PHP script, and I don't really know why.

Basically, what this script does (the portion that is apparently causing a problem) is take a string and split it.

An incoming string (called $teachers) may look like:  "1, 2, 4, 9, 3", and it sends it to an array...

Here's the code:```

	$finished = 0;
	$cur_pos = 0;
	$next_pos = 0;
	$countT = 0;
	while ($finished != 1) {
		$next_comma = strpos($teachers, ",", $cur_pos);
		if ($next_comma == FALSE) {
			$next_pos = strlen($teachers) - $cur_pos;
			$finished = 1;
			$teach[$countT] = substr($teachers, $cur_pos);
		} else {
			$next_pos = $next_comma - $cur_pos;
			$teach[$countT] = substr($teachers, $cur_pos, $next_pos);
		}
		$cur_pos = $next_pos + 1;
		$countT++;
	}
```

And I thought it was a memory problem, because the size alloted to PHP was pretty small... and so I increased it, but that didn't help.  It always returns an error such as

```

Fatal error: Allowed memory size of 8388608 bytes exhausted (tried to allocate 35 bytes) in /usr/local/apache/htdocs/ptc/step_4.php on line 43
```

But the size of memory and the line of code changes... but the problem always exists within the code I provided above.

Any ideas?  Help is appreciated

Thanks

---

### Post by smartbei on 2007-09-11
Not sure what the problem is, but out of curiosity: Why are you not using explode()? It would be:
[php]
$teach=explode(", ",$teachers);
[/php]
Failing that, is it necessary to keep track of the current array count in $countT? If all your doing is appending to the array, you can just:
[php]
$teach[]=substr($teachers, $cur_pos);
[/php]

Back to your original problem - Have you tried printing check-up statements in the loop to see if it always crashes on a particular occurence? etc.

---

### Post by Lux Perpetua on 2007-09-11
```
		$cur_pos = $next_pos + 1;
```Perhaps you meant```
		$cur_pos [highlight]+[/highlight]= $next_pos + 1;
```?

---

### Post by 71fnRVVm on 2007-09-12
Ok, well I'm not using explode because... because... ok I should be using explode.  But that won't fix my problem.

It doesn't always stop at the same line, and that's the entirety of the problem... however, it IS always within that while() statement, but it could be anywhere within.

As for the position counter... no.  I meant what I meant.  Read my code again.

---

### Post by Lux Perpetua on 2007-09-12
[quote=71fnRVVm]As for the position counter... no. I meant what I meant. Read my code again.[/quote]Okay, I may have misunderstood you, then. I thought you wanted to take a string $teachers =  "1, 2, 4, 9, 3" (for example) and parse it into the array $teach with $teach[0] = 1, $teach[1] = 2, ..., $teach[4] = 3. You should probably explain your problem better or say how the change I suggested earlier doesn't do what you want. 

Also, whether or not I misinterpreted your post, please lose the attitude. You're the one asking us to debug your program.

---

### Post by Thyme on 2007-09-12
I've had this problem many times before and it was always related to something weird I did in my code.

I would have used an array to store the teachers and explode it to get the values and then use a for loop to do some stuff. I've created a teachers string with values separated by comma's and echoed out $next_comma in the loop and the loop never seems to stop. I may have did something different to yours but I would still use explode with a for loop.

---

### Post by 71fnRVVm on 2007-09-12
Ok, well I'll be at work in a little bit.... let me convert that to using explode and see what happens.  We'll go from there.

Thanks

---

### Post by 71fnRVVm on 2007-09-13
Whatever the problem happened to be, "explode" fixed it.

Thanks for the help though

---

### Post by Thyme on 2007-09-14
Glad to have heard that 71fnRVVm :) Cheers.

---

