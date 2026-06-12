---
title: "[SOLVED] Data Mine Scripting"
date: 2008-07-14
forum: Programming Talk
---

### Post by Yuki_Nagato on 2008-07-14
I need certain data values pulled from the source of HTML in a plethora of files I have amassed.

I have been looking into AWK and grep and such, and have been introduced to regular expressions.  Here is my problem:

As the data is stored in tables, it is stuck between <td></td> tags.  There are many arbitrary <td> tags, but the ones I need have a width attribute.  The data changes length and type between files, but I know the Strings around it.  So how would I pull data "XXX" from this scenario?

```
<td width = 500>XXX</td>
```

I was thinking a "if ('<td width = 500>' is found) -> while ('<' is not found) -> Paste the Characters of "XXX" into a text file.

Ideally, each "XXX" would be pasted onto its own line, but as I am new to all of this stuff, I am struggling.

---

### Post by nanotube on 2008-07-14
> **Yuki_Nagato said:**
> I need certain data values pulled from the source of HTML in a plethora of files I have amassed.

I have been looking into AWK and grep and such, and have been introduced to regular expressions.  Here is my problem:

As the data is stored in tables, it is stuck between <td></td> tags.  There are many arbitrary <td> tags, but the ones I need have a width attribute.  The data changes length and type between files, but I know the Strings around it.  So how would I pull data "XXX" from this scenario?

```
<td width = 500>XXX</td>
```

I was thinking a "if ('<td width = 500>' is found) -> while ('<' is not found) -> Paste the Characters of "XXX" into a text file.

Ideally, each "XXX" would be pasted onto its own line, but as I am new to all of this stuff, I am struggling.

rather than using straight regexp, use an html parsing library, where they've taken care of all the gory details for you. i'd recommend python with beautifulsoup library.

---

### Post by TreeFinger on 2008-07-14
I think the 're' module from python would work?

[http://docs.python.org/lib/module-re.html](http://docs.python.org/lib/module-re.html)

If anyone can tell me why it wouldn't I would like to hear.

---

### Post by Yuki_Nagato on 2008-07-14
-_-

It is so easy with Python.  Thank you very much for your help.  What I needed to get done was easily finished.

---

### Post by myrtle1908 on 2008-07-14
In Perl ...

```
use strict;
use warnings;

# Some HTML (note inconsistent spacing in between attributes etc) .
# you should account for this in your regular expressions or better yet use an HTML parser
my $html = '<td width   = 500>ABC</td> <td width =500>DEF</td><td width   = 500>123</td> <td width =500>456</td><td>no thanks</td>';

my @s = $html =~ /<td\s+width\s*=\s*500\s*>(.*?)</gi;

print join("\n", @s);
```

---

### Post by nanotube on 2008-07-15
> **TreeFinger said:**
> I think the 're' module from python would work?

[http://docs.python.org/lib/module-re.html](http://docs.python.org/lib/module-re.html)

If anyone can tell me why it wouldn't I would like to hear.

well, of course it would - after all, the html parsers are all basically based on a bunch of regexps themselves.

the problem is that to make it truly tolerant of variant input, you have to do some thinking and some work - all work which has already been done for you in an html parser.

so, you might make a simple regexp to fit 
```
<td width=500>stuff</td>
```

but then you might encounter things with extra spaces and tabs:
```
<td   width = 500 > some stuff </ td>
```
or things with some quotes
```
<td width="500">somestuff</td>
```
or things with units:
```
<td width=500px>stuff</td>
```
or things with more attributes
```
<td border=2 width=500>stuff</td>
```
or things with nested tags:
```
<td width=500><a href="blabla>stuff</a></td>
```
and these are just the first few that come to me.

the basic perl regexp that myrtle1908 posted, for example, would screw up on all of these except the first one (with just the spaces). 

an html parser, on the other hand, you can basically say "give me the contents of all td elements that have attribute width = 500 px", and not worry about all that.

so, if you are doing it for practice or fun, sure, go ahead and regexp it - it's good practice. but if you want to get something done quickly and without error, avoiding unforeseen border cases, use an html parser.

---

### Post by ghostdog74 on 2008-07-15
how about just getting rid of all <> ? assuming they are on a line by itself.
```

awk '/<td.*width/{gsub("<[^>]+>","");print}' file

```

---

### Post by myrtle1908 on 2008-07-15
@nanotube - Absolutely!  An HTML parser is almost always better.  I guess the only time you can get away with a simple regex is when you are in total control of the input (ie. HTML) and can guarantee the format.

---

