---
title: "perl script to extract html code"
date: 2007-10-15
forum: Programming Talk
---

### Post by midspot on 2007-10-15
Hi all,

I'm a former .net developer diving into the perl world...

I've been trying all afternoon to extract a portion of an html file using perl and create a new html file with the extracted code.

In this case I want to extract everything between the table tags in the starting html file and create a new file with only the code I selected.

Any help would be greatly appreciated... I thought this could be accomplished with grep or awk via a shell script, but I didn't have any luck there either...

thanks

---

### Post by pmasiar on 2007-10-16
slavik is ardent Perl evangelist, proposing Perl solutions everywhere, but somehow missed this post. I will try.

First, trying to parse HTML by hand is sucker's game. One of best assets of Perl is CPAN (Perl code archive), you as beginner might not know about it. Google to the rescue.

Another option would be to use cleaner language which gradually becomes Perl's successor: Python. very similar to Perl, but some important choices were made differently. Perl advocates powerful code, and "lets you enough rope to hang yourself". Python has focus on readability of code. As joke goes, Perl looks like executable line noise, Python is executable pseudocode.

ElementTree is excellent Python library for parsing XML. Compared to Perl, Python is "batteries included", ET is standard since Py2.5.

---

### Post by ghostdog74 on 2007-10-16
> **midspot said:**
> 
In this case I want to extract everything between the table tags in the starting html file and create a new file with only the code I selected.


post a sample of that html page, and the perl code you had come up with...

---

### Post by midspot on 2007-10-16
I actually got it working using sgrep with the following code:

sgrep '"<table" .. "</table>"' test.txt 

thanks

---

### Post by slavik on 2007-10-16
without knowing more about the problem, here's the Perl code I have come up with:
```
cat index.html | perl -e '$_ = join("",<>); s|(<table.*</table>)|print $1|ise;'
```

of course, if this is done on a *nix system, try to use the grep family of tools. :)

EDIT: I didn't miss it, I just didn't get to it :P

---

### Post by wkimberly on 2008-12-22
For those that find this thread and want to know how to parse an HTML table or code from a site (like me) there is a simple way of doing it. Perl has a module that does this: HTML::TableExtract ([http://kobesearch.cpan.org:/htdocs/HTML-TableExtract/HTML/TableExtract.html](http://kobesearch.cpan.org:/htdocs/HTML-TableExtract/HTML/TableExtract.html)), the examples are a good start, don't forget to add "my $te" to each variable declaration when using "use strict".

Also, to download the HTML data directly you could use:

```
#!/usr/bin/perl
use strict;
use warnings;
use HTML::TableExtract;
use LWP::Simple;
my $html = get("http://ubuntuforums.org");
my $table = HTML::TableExtract->new;
$table->parse($html);
# Table parsed, extract the data.
```

---

