---
title: "my first perl script"
date: 2007-09-04
forum: Programming Talk
---

### Post by frenchcr on 2007-09-04
Howdy, Ive got a file on my desktop that has 8192 zeros and ones (a bitstream) inside it, but they arent seperated by spaces so i cant load them into excel or matlab.

I wrote a perl script to pull the bitstream file (8192.0.pat) in then split it up and print it out with spaces between each 1 or 0...

```
#!/usr/bin/perl -W

chomp($me = `id -un`);
$PATH = "/home/$me/Desktop";

open(Patfile,"$PATH/8192.0.pat") or die "cannot open Patfile";

my $data = Patfile;
my @values = split(undef, $data);

foreach my $val (@values)
{
  print "$val ";
}

close(Patfile);
exit 0;


```

root@frenchcr03-lap:/home/frenchcr03/Desktop# ls
8192.0.pat  splitfilerow.perl  splitrow.perl

root@frenchcr03-lap:/home/frenchcr03/Desktop# perl splitfilerow.perl 
Unquoted string "pat" may clash with future reserved word at splitfilerow.perl line 17.
Use of uninitialized value in open at splitfilerow.perl line 7.
cannot open patfile at splitfilerow.perl line 7.

root@frenchcr03-lap:/home/frenchcr03/Desktop# 

doesnt compile ??
:confused: anyone spot the mistake....or worse have i got packages missing.

---

### Post by Jessehk on 2007-09-04
Would this do it?

```

cat <file> | sed 's/\(.\)/\1 /g'

```

```

$ echo "011011011" | sed 's/\(.\)/\1 /g'
0 1 1 0 1 1 0 1 1 

```

:)

---

### Post by EndPerform on 2007-09-04
Here's a version that gives no warnings or errors.  I didn't test this, so if it breaks, don't blame me, I'm just trying to help :)

```

#!/usr/bin/perl

use strict;
use warnings;

my $me;
chomp($me = `id -un`);
my $PATH = "/home/$me/Desktop";

open(PATFILE,"$PATH/8192.0.pat") or die "cannot open Patfile";

my $data = (<PATFILE>);
my @values = split(undef, $data);

foreach my $val (@values)
{
    print "$val ";
}

close(PATFILE);
exit 0;

```

Now, a couple of things:

Your script was complaining about Patfile.  Anytime I use a file handle, I capitalize it. 

I added use strict at the top.  This enforces good perl practices.  

I changed the -W to use warnings;    That's a matter of taste, but I think it's easier to see if warnings are turned on with that at the top rather than the -w option.

INote I added (<>) around PATFILE.  Without it, and with use strict on, Perl will complain since patfile is considered a bare word.  You didn't see this because use strict wasn't on.

That should do what you need.  I hope you don't mind the pointers :)

---

### Post by frenchcr on 2007-09-04
Just returned to find your solution...thank you :) Jessehk and EndPerform ...nice advice and mods

Did get it working a little while ago with:

```
#!/usr/bin/perl -W

open(Pattern, "8192.0.pat") || die("cannot open Pattern");

$data = <Pattern>;
@values = split(undef, $data);

open(PatSpace, ">8192.0.txt");

foreach my $val (@values)
{
  select PatSpace;
  print "$val ";
}

close(Pattern);
close(PatSpace);

exit 0;

```

Although it works it still gives me an warning:

Use of uninitialized value in regexp compilation at splitfilerow2.perl line 6, <Pattern> line 1.

:confused:

Going to try your solutions

---

### Post by eph1973 on 2007-09-04
I am also learning Perl, myself, and here is another way to do it that worked for me:

```
#!/usr/bin/perl -w

use strict;

my $file = shift @ARGV;
my $newfile = "$file.new";
unless(open ORIG_FILE, "<$file"){
  die "Cannot open file '$file': $!\n";
}
unless(open NEW_FILE, ">$newfile"){
  die "Cannot create new file: $!\n";
}
while (<ORIG_FILE>){
  s/(\d)/ $1/g;
  print NEW_FILE $_;
}

```

---

### Post by frenchcr on 2007-09-04
eph1973...thanks, its totally different but thats the beauty of Perl. :)

Using the suggestions, my final piece of code now looks like this:

```
#!/usr/bin/perl

use strict;
use warnings;

my $me;
chomp($me = `id -un`);
my $PATH = "/home/$me/Desktop";

open(PATTERN, "$PATH/8192.0.pat") || die("cannot open Pattern");

my $data = (<PATTERN>);
my @values = split(undef, $data);

open(PATSPACE, ">8192.0.txt");

foreach my $val (@values)
{
  select PATSPACE;
  print "$val ";
}

close(PATTERN);
close(PATSPACE);

exit 0;

```

...it works!  ....but i still get a warning i dont understand... [B]Use of uninitialized value in regexp compilation at splitfilerow2.perl line 13, <PATTERN> line 1.
[/B]

---

### Post by slavik on 2007-09-04
pipe a file in and redirect the output :), note: not tested.
```

perl -ne 'while (<>) { map {s/(\d)/print $1."\n"/sge}, $_; }'

```

---

### Post by eph1973 on 2007-09-04
Try replacing 

```
my @values = split(undef, $data);
```with

```
my @values = split //, $data;
```and the message should go away.  I think it's because of instead of an empty string (which amounts to undef anyhow), you are telling it undef, so you get a minor complaint from the compiler.  I know that when you have warnings turned on, any use of undefined variables, arrays, hashes, and so forth gets the complaint.  I could be wrong on the reason, but I tried my suggestion, and did not get the warning.

---

### Post by frenchcr on 2007-09-04
thanks for all the help folks...enjoyed your sugestions..ive got them all working aswell :-({|=

---

### Post by bashologist on 2007-09-04
> my $me;
chomp($me = `id -un`);
my $PATH = "/home/$me/Desktop";
[INDENT]Could be done:
```
chomp(my $me = `id -un`);
```
This might be easier:
```
my $PATH = "$ENV{HOME}/Desktop";
```[/INDENT]
> open(PATTERN, "$PATH/8192.0.pat") || die("cannot open Pattern");
[INDENT]I think an "or" would work better than a "||" in this case. I forget why but I always do it.
```
open PATTERN, "$PATH/8192.0.pat" or die "$PATH/8192.0.pat: $!\n";
```
That's how I would write some of it. That looks really good for a first script, are you reading a book on this? n_n[/INDENT]

---

### Post by ghostdog74 on 2007-09-04
> **Jessehk said:**
> Would this do it?

```

cat <file> | sed 's/\(.\)/\1 /g'

```


:)
no need for cat
```

sed  's/\(.\)/\1 /g' file

```

---

### Post by nanotube on 2007-09-05
here's a python solution:
```

f = open('8192.0.pat', 'r')
mystring = f.readline()
newstring = ' '.join(list(mystring))
f = open('newfile.txt', 'w')
f.write(newstring)

```

admittedly, doesn't match the elegance of the sed approach :)

---

### Post by ghostdog74 on 2007-09-05
> **nanotube said:**
> here's a python solution:
```

f = open('8192.0.pat', 'r')

```

open() opens a file in read mode by default, so you can save some keystroke:)
```

f=open("file")

```

> 
```

mystring = f.readline()
newstring = ' '.join(list(mystring))
f = open('newfile.txt', 'w')
f.write(newstring)

```

remember to close the file handle if you are using this method. Also, OP is using Perl. 
> 
admittedly, doesn't match the elegance of the sed approach :)
elegance is in the eye of the beholder.

---

### Post by nanotube on 2007-09-05
> **ghostdog74 said:**
> open() opens a file in read mode by default, so you can save some keystroke:)
```

f=open("file")

```

heh, true, it's just a personal preference for me to note the mode explicitly.

```
remember to close the file handle if you are using this method.  
```

my understanding is that when the python program exits, all file handles are closed automatically? so there's no need to explicitly close for something short like this?

> Also, OP is using Perl.

i know - just wanted to share a python solution. :)

> elegance is in the eye of the beholder.

true, true. :)

---

### Post by frenchcr on 2007-09-05
many many thanks...i got more than i bargained for there, even learned how to do it in python =D>:grin::biggrin:

---

