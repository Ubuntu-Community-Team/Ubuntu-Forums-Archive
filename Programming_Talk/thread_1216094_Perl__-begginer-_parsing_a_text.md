---
title: "Perl  -begginer- parsing a text"
date: 2009-07-17
forum: Programming Talk
---

### Post by Tanchistu on 2009-07-17
I've got this text stored in a variable:

```

  147  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=69793
  148  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=69792
  149  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=69791
  637  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=34443
  638  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=34442
  639  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=34441
  709  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=1103
  710  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=1102
  711  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=1101

```

I want to output the UtranCell's values in another variable;

If I use:

```
($cellsdown) = ($command =~ /Cell=(\d+)/);
```

multiple times, I will only get the first value (69793) every time... so I can't use a loop as I intended, what should I do?

---

### Post by c0mput3r_n3rD on 2009-07-17
Do you have it stored in an array?

---

### Post by Tanchistu on 2009-07-17
I've got it stored in $command, so I guess it's a scalar variable.

---

### Post by c0mput3r_n3rD on 2009-07-17
Store the file(?) into an array, and step it through like so:
```


 $x = 0;
while (<FILE>)
{
   ($cellsdown[x]) = ($command =~ /Cell=(\d+)/);
   $x++;
}

```

---

### Post by ghostdog74 on 2009-07-17
```

$string="
  147  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=69793
  148  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=69792
  149  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=69791
  637  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=34443
  638  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=34442
  639  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=34441
  709  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=1103
  710  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=1102
  711  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=1101";

@s = split /.*UtranCell/,$string;
foreach (@s){
    chomp;
    s/=//g;
    print $_."\n";
}

```

---

### Post by Tanchistu on 2009-07-17
OK, do I really have to save the content of the variable in a file?

Now my code looks like this:

```
$command = `$moshell_path $Site \'confl\\nlt ^U.*ll\\nst all 0.*0'`;
if ($command =~ /Checking ip contact...OK/)
{
	print "Connected\n";
	print "$command\n";

	($cellsdown) = ($command =~ /Cell=(\d+)/);
		
	print "$cellsdown\n";

}
else { #Site cannot be contacted
	print "Node $Site cannot be contacted\n";
}
```

can't I just step through the variable as it was a file?

I have to go to sleep now, it's 6:25AM in my time zone.8-) 

I'll pick this up tomorrow morning (5pm:))

Thanks for your help

---

### Post by Tanchistu on 2009-07-17
Thanks ghostdog74, I have tried your solution and it works, I don't understand how it works, but it works.

I will try to understand your solution tomorrow, also I will look over the tutorial in your signature.

Thanks everyone.

---

### Post by myrtle1908 on 2009-07-18
Yet another way ...

```
use strict;
use warnings;

my $string="
  147  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=69793
  148  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=69792
  149  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=69791
  637  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=34443
  638  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=34442
  639  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=34441
  709  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=1103
  710  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=1102
  711  0 (LOCKED)    0 (DISABLED)  RncFunction=1,UtranCell=1101
";

my @s = ($string =~ m/.*?UtranCell=(.*)$/mg);
print join("\n", @s);
```

---

### Post by Tanchistu on 2009-07-18
OK, thanks to all, I have finished my first script and it works the way I intended. I understand all the lines in the script but this one:

```
my @s = ($string =~ m/.*?UtranCell=(.*)$/mg);

```

I understand what =~ does but I don't understand the bold parts of the line:

my @s = ($string =~ **m**/**.*?**UtranCell=**(.*)$**/**mg**);

I know what .* is but I don't know how it works with ? and $ and I can't find how m and mg works, probably because Google doesn't work to well with single characters.

Can someone please explain to me how this works.

---

### Post by Mirge on 2009-07-18
> **Tanchistu said:**
> OK, thanks to all, I have finished my first script and it works the way I intended. I understand all the lines in the script but this one:

```
my @s = ($string =~ m/.*?UtranCell=(.*)$/mg);

```I understand what =~ does but I don't understand the bold parts of the line:

my @s = ($string =~ **m**/**.*?**UtranCell=**(.*)$**/**mg**);

I know what .* is but I don't know how it works with ? and $ and I can't find how m and mg works, probably because Google doesn't work to well with single characters.

Can someone please explain to me how this works.

.* means match 0 or more characters, the ? after it makes it non-greedy. The (.*) captures the match... $ means "end of line"... m means multiline, g means global... m and g being flags.

Google around for a Perl regular expressions tutorial.

---

### Post by master_kernel on 2009-07-18
> **Tanchistu said:**
> OK, thanks to all, I have finished my first script and it works the way I intended. I understand all the lines in the script but this one:

```
my @s = ($string =~ m/.*?UtranCell=(.*)$/mg);

```

I understand what =~ does but I don't understand the bold parts of the line:

my @s = ($string =~ **m**/**.*?**UtranCell=**(.*)$**/**mg**);

I know what .* is but I don't know how it works with ? and $ and I can't find how m and mg works, probably because Google doesn't work to well with single characters.

Can someone please explain to me how this works.
And the m// command means "match" as opposed to s/// which is "search and replace".
Non-greedy means that Perl will match as few characters as possible as long as it matches the expression.
(.*), as stated above, captures the match and puts it in a variable, in this case, the array @s.
$, also as stated above, means end of line. So it's saying capture everything after UtranCell= up to the end of the line and put it in @s. The "." matches any character (not a newline, unless you use "s" at the end of the command as a flag), and the "*" means match zero or more of the preceding character set.
The "g" means global, and allows multiple matches. Otherwise you'd end up with one number in your array, which would not be useful.

---

### Post by master_kernel on 2009-07-18
I highly recommend reading *Learning Perl* if you really want to get to know basic Perl.

---

### Post by Mirge on 2009-07-18
> **master_kernel said:**
> I highly recommend reading *Learning Perl* if you really want to get to know basic Perl.

As I already mentioned :) +1

---

