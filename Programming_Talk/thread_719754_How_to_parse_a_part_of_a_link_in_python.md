---
title: "How to parse a part of a link in python?"
date: 2008-03-09
forum: Programming Talk
---

### Post by atomkarinca on 2008-03-09
Hi everyone. How can I crop a part of a link in python? For example, let's say the link is [http://www.youtube.com/watch?v=FRnrKzOrp7M](http://www.youtube.com/watch?v=FRnrKzOrp7M) and I want to get FRnrKzOrp7M from that link. How do I go about doing that? Thanks.

---

### Post by Acglaphotis on 2008-03-09
[php]
string = "http://www.youtube.com/watch?v=FRnrKzOrp7M"
newString = string.replace("http://www.youtube.com/watch?v=", "")
[/php]

newString only has FRnrKzOrp7M.

---

### Post by atomkarinca on 2008-03-09
Thanks for the quick reply :)

---

### Post by Can+~ on 2008-03-09
I would've suggested using regular expressions for that. Like looking for the "?v=_______" with it, since youtube can have different flags like "?locale=" for another language, etc.

---

### Post by atomkarinca on 2008-03-09
How can I do that? What if -like you said- there was another flag?

---

### Post by a9bejo on 2008-03-09
[http://www.amk.ca/python/howto/regex/](http://www.amk.ca/python/howto/regex/)

---

### Post by Acglaphotis on 2008-03-09
Heres a link on how to use regulars expression on python (kinda hard though):

[http://www.amk.ca/python/howto/regex/]("http://www.amk.ca/python/howto/regex/")

Or you could replace the "http://www.youtube.com/watch?v=" with "http://www.youtube.com/watch?*="

---

### Post by atomkarinca on 2008-03-09
> **Can+~ said:**
> I would've suggested using regular expressions for that. Like looking for the "?v=_______" with it, since youtube can have different flags like "?locale=" for another language, etc.

How can I use this with replace() ? Can you give a simple example?

---

### Post by Can+~ on 2008-03-09
More about Regular expressions:
[http://docs.python.org/dev/howto/regex.html](http://docs.python.org/dev/howto/regex.html)

*edited*
[PHP]
import re
ytburl = "http://www.youtube.com/watch?v=FRnrKzOrp7M"
regexp = "v=\\w*" 

#It's a good idea to compile it if you're gonna use it more than once.
regexp = re.compile(regexp, re.IGNORECASE)
result = regexp.search(ytburl)

if (result):
	print "String: %s" % result.group()
else:
	print "Not found."
[/PHP]

Result:
> String: v=FRnrKzOrp7M


------------------
(program exited with code: 0)
Press return to continue


I'm sure there's a lot of improvement you could do to the regular expression like using {7,} to specify a minimum of repetitions instead of using the *.

---

### Post by mssever on 2008-03-09
In Ruby, you would do something like
```
/v=([^&])/.match url
video_id = $1
```
The regular expression (between, but not including, the slashes) should be the same in Python. $1 is the contents of the first perenthesized part of the regex. I don't know how to access that data in Python, but you should be able to find it easily enough. The regex is the hardest part of this.

---

### Post by atomkarinca on 2008-03-09
> **Can+~ said:**
> More about Regular expressions:
[http://docs.python.org/dev/howto/regex.html](http://docs.python.org/dev/howto/regex.html)

*edited*
[php]
import re
ytburl = "http://www.youtube.com/watch?v=FRnrKzOrp7M"
regexp = "v=\\w*" 

#It's a good idea to compile it if you're gonna use it more than once.
regexp = re.compile(regexp, re.IGNORECASE)
result = regexp.search(ytburl)

if (result):
    print "String: %s" % result.group()
else:
    print "Not found."
[/php]Result:


I'm sure there's a lot of improvement you could do to the regular expression like using {7,} to specify a minimum of repetitions instead of using the *.


Thanks a million times. It worked like a charm :)

---

### Post by Can+~ on 2008-03-09
> **atomkarinca said:**
> Thanks a million times. It worked like a charm :)

You should optimize it more though, I've noticed that youtube has other characters rather than the usual alphanumeric, so I give that task to you, so you can learn regexp too. Here are other example url's I've collected so you can try them out:

```
samplelist = [ \
"http://www.youtube.com/watch?v=FRnrKzOrp7M", \
"http://www.youtube.com/watch?v=ngjr6IkDLxg&feature=related", \
"http://de.youtube.com/watch?v=et2Y-_n8_W0&feature=bz303" ]
```

---

### Post by pmasiar on 2008-03-09
I like to keep things simple, and can do without regex in 80%. This one looks simple enough: 

[PHP]url = "http://www.youtube.com/watch?v=FRnrKzOrp7M"
result = url.split('v=')[1][/PHP]

---

### Post by mssever on 2008-03-09
> **pmasiar said:**
> I like to keep things simple, and can do without regex in 80%. This one looks simple enough: 

[php]url = "http://www.youtube.com/watch?v=FRnrKzOrp7M"
result = url.split('v=')[1][/php]

Does that work if the query string has more parameters? 

I think that this is a good candidate for a regex. The regex given above might not work in all cases, though it'll probably work in most. Use something like this to catch all possibilities: ```
regex = '\\?.*v=([^&]+)'
```This grabs all characters after v= until it reaches the end of the string or the & character which separates values.

---

### Post by pmasiar on 2008-03-09
> **mssever said:**
> Does that work if the query string has more parameters? 

[PHP]url = "http://www.youtube.com/watch?v=FRnrKzOrp7M"
result = url.split('v=')[1] 
if '&' in result:
    result = result.split('&')[0]
[/PHP]

[quote]This grabs all characters after v= until it reaches 
the end of the string or the & character which separates values.

this too, and without the regex magic. :-)

I don't hate regex, I even have Perl/regex book signed **personally** by Abigail from Perl conference, but for 80% of tasks, regex is not necessary.

---

### Post by LaRoza on 2008-03-09
> **pmasiar said:**
> 
this too, and without the regex magic. :-)

I don't hate regex, I even have Perl/regex book signed **personally** by Abigail from Perl conference, but for 80% of tasks, regex is not necessary.

Good, I thought I was the odd one for not using re and preferring to use other methods.

---

### Post by ghostdog74 on 2008-03-09
please make use of the library module urlparse
```

>>> import urlparse
>>> url = "http://www.youtube.com/watch?v=FRnrKzOrp7M"
>>> o = urlparse.urlparse(url)
>>> o[4]
'v=FRnrKzOrp7M'

```
look up the document for urlparse to know[ what the attributes mean]("http://docs.python.org/lib/module-urlparse.html")

---

### Post by slavik on 2008-03-09
> **pmasiar said:**
> [QUOTE=mssever;4484635]Does that work if the query string has more parameters? 

[PHP]url = "http://www.youtube.com/watch?v=FRnrKzOrp7M"
result = url.split('v=')[1] 
if '&' in result:
    result = result.split('&')[0]
[/PHP]



this too, and without the regex magic. :-)

I don't hate regex, I even have Perl/regex book signed **personally** by Abigail from Perl conference, but for 80% of tasks, regex is not necessary.
this is one of those that is in the 20% of tasks ;)

EDIT: if you split it on the 'v', then how do you know where the v is?

```

$url = "ur_with_get.php?key1=value1&key2=value2";
$get_string = $1 if ($url =~ /\?(.*)/);
%_GET = map { split /=/, $_ } split /&/, $get_string;

```

what php does (for GET) behind the scenes in 3 Perl statements. :)

---

### Post by mssever on 2008-03-09
> **ghostdog74 said:**
> ```

>>> import urlparse
>>> url = "http://www.youtube.com/watch?v=FRnrKzOrp7M"
>>> o = urlparse.urlparse(url)
>>> o[4]
'v=FRnrKzOrp7M'

```

As in pmasiar's initial example, this one also requires additional code to work properly, since YouTube URLs frequently contain additional parameters in the query string. You can solve this by splitting the string multiple times, or with urlparse plus a split; or, you can write a single simple regex that handles all variations well. While some regexes add complexity to a program, in this case, I think that a regex is the simplest solution by far. (Of course, regexes are a bit awkward in Python. That's one reason I like Ruby :) )

EDIT:
[quote=slavik]this is one of those that is in the 20% of tasks :wink:[/quote]
Agreed. Though Perl code tends to make a simple problem look complex... Compare this Ruby code:
```
/[?&]v=([^&]+)/.match url
the_result = $1
```

---

### Post by ghostdog74 on 2008-03-09
> **mssever said:**
> you can write a single simple regex that handles all variations well.

if a simple regex handles all variations well, it most probably would not be simple anymore, don't you agree? :-)

> . (Of course, regexes are a bit awkward in Python. That's one reason I like Ruby :) )
that's why Python have strong string manipulation capabilities, so say the Python advocate.

---

### Post by pmasiar on 2008-03-09
Compare: regex solution:
[PHP]/[?&]v=([^&]+)/.match url
result = $1[/PHP]

vs plain string parsing:

[PHP]result = url.split('v=')[1] 
if '&' in result:
    result = result.split('&')[0][/PHP]

It takes one more line, but is easier to read, unless you are regex expert.

Of course regex solution scales for more complex cases. But in 80% cases, like this one, regex is overkill, IMHO. YMMV, eat your regex if you want, I don't care anymore. :-)

---

### Post by slavik on 2008-03-10
> **pmasiar said:**
> Of course regex solution scales for more complex cases. But in 80% cases, like this one, regex is overkill, IMHO. YMMV, eat your regex if you want, I don't care anymore. :-)

Once I get a regex to match correctly, I don't have to care about it anymore.

---

### Post by ghostdog74 on 2008-03-10
> **slavik said:**
> Once I get a regex to match correctly, I don't have to care about it anymore.
that's quite untrue isn't it? how do you know your program specs won't change in future?

---

### Post by WW on 2008-03-10
The structure is simple enough; regex does seem like overkill.  This python function gets all the assigned values into a dict.  Python gurus could probably simplify it even more:

```

# parse_url_opts.py

def parse_url_opts(str):
    (url,opts_str) = str.split("?")
    opts_list = opts_str.split("&")
    opts_pairs = [s.split("=") for s in opts_list]
    return dict(opts_pairs)

```
Example:
> 
>>> from parse_url_opts import *
>>> z = parse_url_opts("http://www.youtube.com/watch?v=ngjr6IkDLxg&feature=related")
>>> z.keys()
['feature', 'v']
>>> z['feature']
'related'
>>> z['v']
'ngjr6IkDLxg'
>>> 


(Something like this might already exist in the **cgi** module.)

---

### Post by mssever on 2008-03-10
> **ghostdog74 said:**
> if a simple regex handles all variations well, it most probably would not be simple anymore, don't you agree? 
Not necessarily. The regex I wrote above is quite simple.

---

### Post by ghostdog74 on 2008-03-10
> **mssever said:**
> Not necessarily. The regex I wrote above is quite simple.
yes for this simple case. like you mentioned, if the url contains different kinds of query strings and not just standard "v=xxxxxx", then a simple regex can become quite complex if all variations are to be handled.

---

### Post by slavik on 2008-03-10
> **WW said:**
> 
```

# parse_url_opts.py

def parse_url_opts(str):
    (url,opts_str) = str.split("?")
    opts_list = opts_str.split("&")
    opts_pairs = [s.split("=") for s in opts_list]
    return dict(opts_pairs)

```

the Perl version:
```

sub parse_url_opts {
  my $url = shift;
  (my $base, my $opts) = split /\?/, $url;
  my @opt_list = split /&/, $opts;
  my %opt_pairs = map { split /=/, $_ } @opt_list;
  return %opt_pairs;
}
```

the only real difference is how the subroutines get their arguments and in Perl, the map is explicit. :)

---

### Post by LaRoza on 2008-03-10
> **slavik said:**
> the Perl version:
```

sub parse_url_opts {
  my $url = shift;
  (my $base, my $opts) = split /\?/, $url;
  my @opt_list = split /&/, $opts;
  my %opt_pairs = map { split /=/, $_ } @opt_list;
  return %opt_pairs;
}
```

the only real difference is how the subroutines get their arguments and in Perl, the map is explicit. :)

There is also a "map" function in Python. Although I don't normally use it, it may be used in a way like yours (I just got up and didn't really read the code, except to say the Perl example is very different visually from the Python)

---

### Post by pmasiar on 2008-03-10
map will be dropped in Py3K IIRC. List comprehension does the same in a more obvious and readable way.

---

### Post by LaRoza on 2008-03-10
> **pmasiar said:**
> map will be dropped in Py3K IIRC. List comprehension does the same in a more obvious and readable way.

[http://www.artima.com/weblogs/viewpost.jsp?thread=98196](http://www.artima.com/weblogs/viewpost.jsp?thread=98196)

[quote="GvR"]
Update: lambda, filter and map will stay (the latter two with small changes, returning iterators instead of lists). Only reduce will be removed from the 3.0 standard library. You can import it from functools.
[/quote]

---

