---
title: "Another Perl Question"
date: 2009-06-18
forum: Programming Talk
---

### Post by dellwood on 2009-06-18
Hi, 

I seem to have run into another problem in my quest to learn Perl.  The current exercise evolves the program reading though a text file, and taking out all words that end with a certain suffix ( "ink" in this case ) and printing those words to the screen.  

The Program:

```

#!/usr/bin/perl
use strict;
use warnings;

my $syllable = "ink";
while ( <> )
{
	print if /$syllable$/;
}

```

The text file:

```

bill
blink 
sink
sue
clink
bob
chink
bill

```

The output:

```

josh@josh-desktop> perl main.plx wordlist.txt   ~/perl/55
sink
clink
chink

```

As you can see, it did not pick up on "blink."  I have checked numerous times against the original program, as well as the source code online (the book is under the creative commons, [http://www.wdvl.com/Authoring/Languages/Perl/BeginningPerl/tryit.html](http://www.wdvl.com/Authoring/Languages/Perl/BeginningPerl/tryit.html)), but I really can't figure it out... am I crazy? 8-[

P.S. This is the first time file access is covered ( and the lesson's not on input, its one of those things that the books going to "cover later" ), so just thought I'd throw that out there.


Anyway...all help on this is greatly appreciated :)

-jhl

---

### Post by Mirge on 2009-06-18
I copy/pasted your list of words.

```

#!/usr/bin/perl -w
use strict;

while(<>) {
        chomp;
        print "I read: |$_|\n";
}

```

I then put the actual words between pipes after chomp()'ing off the newline. Here are the results:

```

mike@mike-kubuntu:~$ cat test.txt | ./test2.pl
I read: |bill|
**I read: |blink |**
I read: |sink|
I read: |sue|
I read: |clink|
I read: |bob|
I read: |chink|
I read: |bill|
mike@mike-kubuntu:~$

```

Notice that the "blink" word has a space after it. This is why it's not showing up in your script via regex... strip the trailing space off it and it'll work.

---

### Post by dellwood on 2009-06-18
That did it :)

Thanks!

-jhl

---

### Post by Mirge on 2009-06-18
Good :). Keep that technique in mind to check for whitespace in the future... I can almost guarantee you'll run into it again lol.

---

