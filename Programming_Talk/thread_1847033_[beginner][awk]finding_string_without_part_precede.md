---
title: "[beginner][awk]finding string without part preceded by underscore"
date: 2011-09-20
forum: Programming Talk
---

### Post by Rohlik on 2011-09-20
Hello, sorry for a begginer question.

I have two files
**File 1:**
```

>5251583_3
>5251582_-1
>5220372_-3
>5220372_-2
>5252483_2

```

and **File2**
```

>5251583 25 36 59
AAAAAAAA
>5251582 399 29 29
BBBBBBBB
>5220372 48 489 49
CCCCCCCC
>5220346 3839 89 39
DDDDDDDD
>5252483 37 38 38
EEEEEEEE
>53676 36 388 09
FFFFFFFF

```

file2 is huge and has many more entries, this is just an example.

expected output would be like this:
```

>5251583_3 25 36 59
AAAAAAAA
>5251582_-1 399 29 29
BBBBBBBB
>5220372_-3 48 489 49
CCCCCCCC
>5220372_-2 48 489 49
CCCCCCCC
>5252483_2 37 38 38
EEEEEEEE


```
So I want to find line containing string (ignoring the part after "_" )from file1 in file2 and print this line (but now with the characters after "_") and the next line (containing AAAAAAA etc.) 

Thank you for your time.

---

### Post by Arndt on 2011-09-20
> **Rohlik said:**
> Hello, sorry for a begginer question.

I have two files
**File 1:**
```

>5251583_3
>5251582_-1
>5220372_-3
>5220372_-2
>5252483_2

```

and **File2**
```

>5251583 25 36 59
AAAAAAAA
>5251582 399 29 29
BBBBBBBB
>5220372 48 489 49
CCCCCCCC
>5220372 3839 89 39
DDDDDDDD
>5252483 37 38 38
EEEEEEEE
>53676 36 388 09
FFFFFFFF

```

file2 is huge and has many more entries, this is just an example.

expected output would be like this:
```

>5251583_3 25 36 59
AAAAAAAA
>5251582_-1 399 29 29
BBBBBBBB
>5220372_-3 48 489 49
CCCCCCCC
>5220372_-2 3839 89 39
DDDDDDDD
>5252483_2 37 38 38
EEEEEEEE


```
So I want to find line containing string (ignoring the part after "_" )from file1 in file2 and print this line (but now with the characters after "_") and the next line (containing AAAAAAA etc.) 

Thank you for your time.

What should happen if the next line of file 2 is

```
>5220372 71 345 72
GGGGGGGG
```

?

---

### Post by Rohlik on 2011-09-20
There will be no such line in file2. the part just after ">" (i.e. >1234) is unique name and will not repeat.

---

### Post by ofnuts on 2011-09-20
Grep-based solution:

```

# create grep pattern from list of marks (1st file)
pat=$(sed -e 's/_.*/|/' -e '$ s/|//' < $file1  | tr -d '\n')

# use grep to output matching lines and the on following
grep -E -A1 "$pat" < $file2

```

---

### Post by sisco311 on 2011-09-20
Smells like a homework question to me.

---

### Post by Rohlik on 2011-09-20
> **sisco311 said:**
> Smells like a homework question to me.

I know :) But not really, thing is the file2 is full of contigs from AbySS transcriptome assembly. I want to find certain genes in it, but the contigs have no deffined frames for protein translation. I can get these from BLAST (hence the _-3 for 3rd reverse frame) Usually I do these things by simple alignment in Geneious software, but it does not seem to work in this case.

---

### Post by Rohlik on 2011-09-20
> **ofnuts said:**
> Grep-based solution:

```

# create grep pattern from list of marks (1st file)
pat=$(sed -e 's/_.*/|/' -e '$ s/|//' < $file1  | tr -d '\n')

# use grep to output matching lines and the on following
grep -E -A1 "$pat" < $file2

```
No matter how I try it, it leaves out the part after underscore in the output. I need to have it there, i just need to filter it out for the search. 

Thank you anyways :)

---

### Post by dethorpe on 2011-09-20
Couple of questions. 
 
Is file1 hugh as well or smaller than file2?
 
How do you want duplicates handled?
 
e.g: for 5220372
 
in file 1 you have:
>5220372_-3
>5220372_-2
 
In file2 you have:
 
>5220372 48 489 49
CCCCCCCC
>5220372 3839 89 39
DDDDDDDD
 
which line in file1 matchs each of the file 2 lines, and what if there are and not the same number of lines in each file with same number. e.g 4 lines with same number in file2 and 2 in file1.

---

### Post by Rohlik on 2011-09-20
> **dethorpe said:**
> Couple of questions. 
 
Is file1 hugh as well or smaller than file2?
 
How do you want duplicates handled?
 
e.g: for 5220372
 
in file 1 you have:
>5220372_-3
>5220372_-2
 
In file2 you have:
 
>5220372 48 489 49
CCCCCCCC
>5220372 3839 89 39
DDDDDDDD
 
which line in file1 matchs each of the file 2 lines, and what if there are and not the same number of lines in each file with same number. e.g 4 lines with same number in file2 and 2 in file1.

Oh I did not see that, the duplicate in file2 is a mistake. It is not in the real file. it would be like:
```
>5220372 48 489 49
CCCCCCCC
>5220325 3839 89 39
DDDDDDDD
```

file1 is not that big, max 1200 lines, as for the file2 that is much bigger, about 60 million lines. I have cca 20 of file1 variations. Time is not really in question here, neither is RAM (I have about 256 gig on a server where the data is)

As for the duplicates in file1, I would like the output to be:

```

>5220372_-3 48 489 49
CCCCCCCC
>5220372_-2 48 489 49
CCCCCCCC

```
So the same sequence twice that differs only in the "name" (the part after >)

Thank you

---

### Post by ofnuts on 2011-09-20
> **Rohlik said:**
> No matter how I try it, it leaves out the part after underscore in the output. I need to have it there, i just need to filter it out for the search. 

Thank you anyways :)Easy enough to post-process that output and re-inject the original values...

This will create the appropriate sed command file
```

while read mark
do
    echo "s/$(echo $mark |sed -e 's/_.*//')/$mark/"
done < $file1 

```ie, generates:
```

s/>5251583/>5251583_3/
s/>5220372/>5220372_-3/
s/>5220373/>5220373_-2/
...

```Then use as 
```

sed -f $fileabove  $output_from_above >final_output

```

---

### Post by Arndt on 2011-09-20
> **Rohlik said:**
> There will be no such line in file2. the part just after ">" (i.e. >1234) is unique name and will not repeat.

But you already have two lines with 5220372 in your files.

Does it mean then, that file1 is as large as file2?

---

### Post by dethorpe on 2011-09-21
heres a quick perl script that may do what you want.
 
```
 
#! /usr/bin/perl -w
use strict;
use warnings;
 
die ("usage: $0 <file1> <file2>") if (@ARGV < 2);
my $file1_name = $ARGV[0];
my $file2_name = $ARGV[1];
 
# read file1 into hash of arrays. 
# hash key is numeric name, value is array of suffixs for that name
open (my $file1, '<', $file1_name) || die ("failed to open $file1_name. $!");
my %file1_hash = ();
while (my $line = <$file1> ) {
 chomp $line;
 my @fields = split (/_/, $line);
 push (@{$file1_hash{$fields[0]}}, $fields[1]);
}
close ($file1);
 
# Now loop through file 2 to find and print matches
open (my $file2, '<', $file2_name) || die ("failed to open $file2_name. $!");
while (my $line = <$file2>) {
 chomp $line;
 if ($line =~ m/^>/) {
  # its a numeric line 
  my ($name,$therest) = split (/ /,$line,2);
  # see if we have match for this name in file1
  if (exists $file1_hash{$name} ) {
   # we do so print the line from file2 for each suffix in file1 for the name
    # get next line which is alpha code
   my $code = <$file2>;
   foreach my $suffix (@{$file1_hash{$name}}) {
    print ("${name}_$suffix $therest\n");
    print ("$code");
   }
  }
 }
}
close ($file2);

```
 
Produces this for your test files:
 
```

>5251583_3 25 36 59
AAAAAAAA
>5251582_-1 399 29 29
BBBBBBBB
>5220372_-3 48 489 49
CCCCCCCC
>5220372_-2 48 489 49
CCCCCCCC
>5252483_2 37 38 38
EEEEEEEE

```

---

### Post by Rohlik on 2011-09-21
dethorpe I sooo want to hug you right now :D
 It's just the thing I needed! Thank you so much!

---

### Post by dethorpe on 2011-09-21
Glad to be of help.
 
(Remember to mark thread as solved if you've no more problems)
 
:)

---

