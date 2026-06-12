---
title: "Help with perl"
date: 2009-07-14
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2009-07-14
Ok so I've been learning perl today and doing well so far using [this]("http://www.comp.leeds.ac.uk/Perl/matching.html") tutorial, but on the Regular Expressoins chapter it gives no examples what so ever to implementing them.  
The task to print all the lines of a specific file, with line numbers only at sentences with a; x, the, or The.  It's building upon previous code which is this:
```

open(INFO, "/home/matt/documents/funny_electricity.txt");
@lines = <INFO>;
close(INFO);
$i = 1;
print "\n\n";
foreach $line (@lines)
{
    if ($line ne "\n")
    {
        print "$i   ";
        print "$line";
    }
    else
    {
        print "$i\n";
    }
    $i++;
}

```

What is the syntax to finding sentences only with an x, the word "the", or "The" using regular expressions?

Thanks.

---

### Post by ghostdog74 on 2009-07-14
why don't you read the official Perl documentation instead.? Learn the basics first before going to regex

```

perldoc perl 

```
or 
```

perldoc perltoc

```

for regex, ```
perldoc perlretut
```

---

### Post by c0mput3r_n3rD on 2009-07-14
Never mind I got it.
```

open(INFO, "/home/matt/documents/funny_electricity.txt");
@lines = <INFO>;
close(INFO);
$i = 1;
print "\n\n";
foreach $line (@lines)
{
    if ($line ne "\n")
    {
        if($line =~ [x])
        {
            print $i;
            print $line;
        }
        elsif($line =~ /the/)
        {
            print $i;
            print $line;
        }
        elsif($line =~ /The/)
        {
            print $i;
            print $line;
        }
        else
        {
            print "   ";
            print $line;
        }
    }
    
    $i++;
}

```

It's amazing how just stepping away for a minute lets you clear your mind.  :D Thanks anyway

---

### Post by myrtle1908 on 2009-07-14
You can shorten that to this:-

```
use strict;
use warnings;

open(F, "stuff.txt") || die "Could not open: $!\n";
while (<F>) {
	print "$.\t$_" if /x|the/gi;
}
close(F);
```

Also a couple of pointers ...

1. It is good to get into the habit of placing 'use strict' and 'use warnings' at the top of your scripts.  These will give you hints as to problems with your code.

2. The expression /x|the/gi means line with either 'x' or 'the' ('g' means global ie. the whole line in this case, 'i' means case insensitive).

3. $. is current line number

4. Best to check if 'open' fails and die.

A decent wrap of special Perl variables here: [http://www.kichwa.com/quik_ref/spec_variables.html](http://www.kichwa.com/quik_ref/spec_variables.html)

---

### Post by c0mput3r_n3rD on 2009-07-14
Awsome.  Thank you very much. :D

---

### Post by slavik on 2009-07-14
Dude ...

>  Regular expressions
A regular expression is contained in slashes, and matching occurs with the =~ operator. The following expression is true if the string the appears in variable $sentence.
[COLOR="Red"]
$sentence =~ /the/[/COLOR]

The RE is case sensitive, so if

$sentence = "The quick brown fox";

then the above match will be false. The operator !~ is used for spotting a non-match. In the above example

[COLOR="Red"]$sentence !~ /the/[/COLOR]

is true because the string the does not appear in $sentence. 

Examples in red and that is actually a nice intro to regex in Perl ...

---

