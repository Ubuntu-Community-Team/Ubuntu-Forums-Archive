---
title: "[Perl] Array of Hashes and LinkExtractor"
date: 2011-07-12
forum: Programming Talk
---

### Post by tauh on 2011-07-12
Hi!

I'm trying to extract all the links from a webpage to a array. I'm using Perl and the module [HTML::LinkExtractor]("http://search.cpan.org/~podmaster/HTML-LinkExtractor-0.13/LinkExtractor.pm").
I am new to array of hashes which the method [links]("http://search.cpan.org/~podmaster/HTML-LinkExtractor-0.13/LinkExtractor.pm#$LX->links()") returns.

I want to be able to pick a specific index (example 0 and only print the url).

This what i have done so far:
```

#!/usr/bin/perl -w
use LWP::Simple;
use HTML::LinkExtractor;
use strict;

my $url = "http://www.pub.se";
my $data = get($url);

my $linkExc = new HTML::LinkExtractor();
$linkExc->parse(\$data);

my @list = $linkExc->links;

print $list[1]{"href"};

```
This code says *Use of uninitialized value in print at test.pl line 14*.

Help? Anyone? ;)

---

### Post by Some Penguin on 2011-07-12
To quote the documentation re: the 'links' method,
[http://search.cpan.org/~podmaster/HTML-LinkExtractor-0.13/LinkExtractor.pm](http://search.cpan.org/~podmaster/HTML-LinkExtractor-0.13/LinkExtractor.pm)
"This method returns a reference to an ArrayOfHashes, which basically looks like (Data::Dumper output)"

Don't use a /reference/ to an array as an array.

---

### Post by dethorpe on 2011-07-13
Not used Linkextractor but as stated by previous poster links() returns Reference to ArrayOfHash. So need to dereference to use it.
 
Assuming you'd like a little more help on references the last lines should look like this:
 
```
 
my $listref = $linkExc->links;
 
print $listref->[1]{"href"};

```
 
So the array reference returned by links() goes into a scaler ($linkref), then you dereference it using "->" to get the element you want.
 
Hope that helps.

---

### Post by tauh on 2011-07-13
> **dethorpe said:**
> Not used Linkextractor but as stated by previous poster links() returns Reference to ArrayOfHash. So need to dereference to use it.
 
Assuming you'd like a little more help on references the last lines should look like this:
 
```
 
my $listref = $linkExc->links;
 
print $listref->[1]{"href"};

```
 
So the array reference returned by links() goes into a scaler ($linkref), then you dereference it using "->" to get the element you want.
 
Hope that helps.

Thank you! That's exactly what i was looking for. :)

---

