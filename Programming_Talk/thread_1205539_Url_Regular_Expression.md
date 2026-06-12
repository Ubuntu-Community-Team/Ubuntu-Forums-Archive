---
title: "Url Regular Expression"
date: 2009-07-06
forum: Programming Talk
---

### Post by Pyro.699 on 2009-07-06
Hello all,

I'm trying to get a well written, flawless regular expression to extract a url from a paragraph.

The url could be jumbled in the middle of other text, such as:
**<a href="http://www.someurl.com">**

but could also be quite complicated:
[B][http://pre.someurl.suf/hash/hash2/randomfile.ext?then?some=GET&variables=parsed](http://pre.someurl.suf/hash/hash2/randomfile.ext?then?some=GET&variables=parsed)

[/B]since this is going to be implemented in a "spider" program, it will have to deal with things like:
&#91;[B]code]http://again.some.url[/code]

[/B]Ive been able to come up with the start of the expression, but im having problems ending it.

```
((ht|f)tp(s?))
```

Thanks in advance
~Cody Woolaver

---

### Post by fr4nko on 2009-07-06
[quote=Pyro.699;7569094
I'm trying to get a well written, flawless regular expression to extract a url from a paragraph.
[/quote]
Writing a regular expression for the more generic url is almost impossible. May be you can get a better help if you clarify what you want to do.

Anyway a simplistic regexp could be:

r'(http|ftp)://((?:\w+\.)+\w+)(?:/(.*))?'

In this case: group(1) is the protocol, group(2) is the domain en group(3) is the rest, if present.

Francesco

---

### Post by Pyro.699 on 2009-07-06
A few problems with that code..

This url would not work:
**[http://ecx.images-amazon.com/images/A/Imagename.jpg](http://ecx.images-amazon.com/images/A/Imagename.jpg)**

I still need the https and ftps, so ill continue using the starting one that i have

That also wouldn't work with something like:
**&#91;code][http://someurl.com/something.php]("http://someurl.com%5B/code%5D")[/code]**

Check out this site, its awesome for making regular expressions, and testing them :)
[http://www.gskinner.com/RegExr/](http://www.gskinner.com/RegExr/)

---

### Post by fr4nko on 2009-07-06
With the following one you can take into account also https and ftps. I've used [\w\-] to allow a dash '-' into the url.

r'(https?|ftps?)://((?:[\w\-]+\.)+\w+)(?:/(.*))?'

Otherwise, if you want to take into account the '[code]' tags you can add them in the regular expression but be aware that such tags are not part of the URL.

---

### Post by myrtle1908 on 2009-07-06
You should probably use a library of some sort.  There are plenty for Perl (no idea re. Python or whatever language you are using).

Anyhoo, for the snippet below, add any other "end of URL characters/sets" that you desire to the third group and you should be fine.

```

use strict;
use warnings;

while (<DATA>) {
	while (/(https?|ftp):\/\/(.*?)(\[|"|'|\s+|$)/gi) {
		print $1.'://'.$2."\n" if ($1 && $2);
	}
}

__DATA__
Put your paragraphs here to test.

```

---

### Post by Reiger on 2009-07-06
Simply put: there is not One Regular Expression pattern that can match *any* URL flawless and all. For starters consider the mailto: URL scheme. And the ED2K ones, and ... 

On a more real-world-application-note: how about implicit protocols? For instance [www.googl.com](www.googl.com) probably should be recognised as (and patched to) a valid URL ... ?

I've tried of course. Anyone doing anything like plain text to HTML conversion will probably have attempted it at some point or another. I've also Google it and apparently the best solution still covers a few code screen full of `Regular Expression Pattern'; though how much `regular', `expression' and `pattern' there is ?

---

