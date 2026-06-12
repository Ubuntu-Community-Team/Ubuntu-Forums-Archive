---
title: "Perl Script Array Problem"
date: 2009-06-19
forum: Programming Talk
---

### Post by dellwood on 2009-06-19
Hi, 

My father has recently handed over the reigns of a our church website to someone who, honestly doesn't know what they're doing.  So to help him out, I though I'd write a script that does the one thing on the site that must be done every week: update the page that contains all the sermon audio files ( new one every week ).  

The script:

```

#!/usr/bin/perl
use warnings;
use strict;

#User input
print "Date of sermon: ";
my $date = <STDIN>;
print "Name of sermon: ";
my $name = <STDIN>;
print "Pastor who gave sermon: ";
my $pastor = <STDIN>;
print "Name of mp3 file: ";
my $mp3 = <STDIN>;
chomp( $date, $name, $pastor, $mp3 );


open TABLE, "table.html" or die "Could not opn file: $!\n";

my @table = <TABLE>;
my @first = @table[0..6];
my @second = @table[7..-1];
my @newhtml = ( 
"<TR>",
"<TD vAlign=top width=\"10%\"><p class=sermondate>$date</p></td>",
"<TD vAlign=top width=\"60%\"><p class=sermonseason>$name</p></td>",
"<TD vAlign=top width=\"20%\"><p class=sermonspeaker>$pastor</p></td>",
"<TD vAlign=top width=\"10%\"><p class=sermonlink><A href=\"$mp3\">Listen</a></p></td>"
);

#puts the arrays back together

push ( @first, @newhtml );
my @new = ( @first, @second );

open OUTPUT, ">table.html" or die "Couldn't write to file: $!\n";

print OUTPUT @new;

close OUTPUT or die "Error closing file: $!\n";

```

Also, the (orignial) HTML file: >>[http://www.pastie.org/517903](http://www.pastie.org/517903)<<.  I know it's just the table, but this is just for testing purposes.  
Also, don't badger me about tables -- it's not my site :D.

The script simply adds *(EDIT)* a line in the table on the website, with the info the user has given ( the mp3 files already have to be uploaded ).

The only problem is, the @second array seems to hold nothing. When @second is combined with @first to form @new, it seem only @first is added.  Am I combining the arrays wrong?  Is [7..-1] incorrect?

As always, all help is greatly appreciated :).

-jhl

---

### Post by slavik on 2009-06-19
7..-1 is incorrect. use 7..$#table

---

### Post by nvteighen on 2009-06-19
IMO there are several issues...

First, adding a line into the text will include whatever sermon you input into 2008 Sermons.

Second, clearly define and split the code into functions. Please. Your task needs at least this following and completely independent steps:

1. Getting user input.
2. Getting input file and parse it.
3. Processing user input into some usable way.
4. Adding the new data to the old.
5. Process the updated data from 4 into output format.
6. Output.

This will be much easier if you create/use a common data structure to hold the table. At first sight, an array of hash references sounds really good for this.

This should (unless I missed something) allow you to scale the script to render standards complying XHTML without too much hassle (just modifying the parsing and outputting criteria).

Third, Perl has something great called regexps :) Use that to define limits in text, rather than hardcoded array indexes...

---

### Post by dellwood on 2009-06-19
Thanks for both the replies.  While slavik told me exactly what I wanted to know, nvteighen gave me some good tips, so I am thankful for both :).

@nvteighen:

> 
First, adding a line into the text will include whatever sermon you input into 2008 Sermons.


I'm not exactly sure what you mean by this.  Are you saying I will or won't lose the 2008 sermons?

> 
Second, clearly define and split the code into functions. Please. Your task needs at least this following and completely independent steps:

1. Getting user input.
2. Getting input file and parse it.
3. Processing user input into some usable way.
4. Adding the new data to the old.
5. Process the updated data from 4 into output format.
6. Output.


I am still learning perl (for my summer job...been do nothing but for 7.5 hours / day since Monday :-| ) and I have not gotten to functions yet, though I know from other languages how they 'function' (no pun intended), so I'll look into that soon.

> 
This will be much easier if you create/use a common data structure to hold the table. At first sight, an array of hash references sounds really good for this.


Do you mean like 


```

my @array = ( $hash1{key}, $hash2{key}, $hash3{key}, ... );

```

with each hash referring to a line of HTML?

...or something completely different :D.

> 
This should (unless I missed something) allow you to scale the script to render standards complying XHTML without too much hassle (just modifying the parsing and outputting criteria).

I'm lost at the scaling part.  Doesn't "scaling" refer to being able to handle large amounts of web traffic?  I'm not sure that's an issue here, but I guess it could be a good habit to get into (if that's what you mean ).

> 
Third, Perl has something great called regexps  Use that to define limits in text, rather than hardcoded array indexes... 


Not sure here either.  Know what regular expressions are, know what hard coded means, but don't know how to use it to define limits in text.

Again, if you dumb it down a bit for a (perl) newbie, it would be most appreciated :)

-jhl

---

